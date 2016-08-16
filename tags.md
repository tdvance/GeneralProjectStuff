#Tags

Tags are used in a lot of situations to categorize things or make it easier to search for things.  One could think of a dictionary (map) type as giving each value a tag called its key, but with the restriction that the key retrieves just that value (though you can get around that by storing a set of values in a tag).  What I'm thinking of is a tag lookup system (multi-key dict? but more than that) closer to how we tend to think of tags.

In addition to having multiple tags per value and multiple values per tag, one should be able to specify a list a tags and retrieve everything that has all those tags, or maybe everything having most of those tags (fuzzy searching).  After that is achieved, do so efficiently as well.

In addition, people are careless in typing tags.  Should A_Tag and atag be the same tag? probably.  So, we need a normalization of some kind for the tag, yet still if we ask for the tags of a value, retrieve the tags as they were originally typed in.

Thus, what we have here is something like this.  A tag is essentially a string.  tag.norm() is the normalization of the tag so that tag1.norm() == tag2.norm() means they are essentially the same tag, even if they are different strings.  We also have values, which can be arbitrary objects.  A value is associated with a collection of tags.  Thus, given the value, we can list all the tags that have been given to it.  In addition, given a list of tags, find all values such that x% (for some x) of the given tags equal (in normalized sense) tags of the value.  And once this is solved, do it efficiently.

So, the stupid (inefficient) solution is to store a set of tuples, (value, tag1, tag2, ...) and do an exhaustive compare for every query.

The problem is to do this better.  Note the "given a value, list its tags" is not entirely trivial to do efficiently.  If the value is an immutable type, it could be looked up by hash to find its tags.  If not, it would be convenient to have the tags stored IN the value itself, which is not always feasible for arbitrary values.  One solution is to store the "address" or other unique ID of the object, if possible in the given language.  Of course, one cannot (efficiently) find the tags for a copy of the object anymore.

If these issues are solved, we can then extend the tagging system, to allow tags to be key-value pairs, not just simple values.  Then we could query for values that have tags having a given key, regardless of value of the key, in addition to values having tags that are a specific key-value.





