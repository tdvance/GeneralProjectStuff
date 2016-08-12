#Abstract Data Type MKDict

* Depends on the Dictionary ADT and the Set ADT.

* Let KeyTag be an ADT that is a dictionary, except that it is immutable.  It represents a dictionary mapping keys (strings) to tags (also strings).

* The KeyTag type has a notion of subset: If k and l are KeyTag objects, we say k is a subset of l if for every key-value pair (a,v) association in k, there is a key-value pair (a,v) association in l having the same key and value.  That is, whenever k.get(a)=v, then l.get(a)=v.

* An MKDict (multi-key dictionary) is a mapping from keytags to values.  Assume Value is the value type.

* The following operations are supported:

* m = new MKDict(): m is now an empty MKDict object.

* m.put(KeyTag k, Value v): m is modified so that it now contains the association between k and v.  If k had an association with a different Value v', that association no longer holds and is replaced with the new association between k and v.

* m.find(KeyTag l): returns a new MKDict object consisting of those associations in m from KeyTag K to some Value v such that l is a subset of k.

* m.get(KeyTag k): Returns a Value object.  If k is associated with a Value v in m, then v is returned.  Otherwise, raises an exception.

* m.has(KeyTag k): Returns a boolean.  If there is an association from k to some Value v in m, True is returned.  Otherwise, False is returned.

* m.remove(KeyTag k): m is modified so that it no longer has any value associated with KeyTag k.  If k was not already associated with a value in m, m is unchanged.

* m.keytags(): returns a set ADT object (can be a view) whose elements are all KeyTag objects k such that there is a Value object v such that m.get(k) == v.

* m.count(): returns the number of KeyTag-Value associations in m.

## Axioms

The MKDict ADT satisfies the following axioms:

* Only put and remove change the state of m.  All other operations return something about the state of m.  Thus all other operations return the same value on every call until either put or remove is performed, then some operations may return different values.

* If m = new MKDict() then m.count() == 0

* For all KeyTag objects k, m.has(k) returns False if and only if m.get(k) raises an exception.

* If KeyTag l is a subset of KeyTag k and m.has(k) is True,  m.find(l).get(k) = m.get(k)

* If KeyTag l is not a subset of KeyTag k or m.has(k) is False, m.find(l).has(k) is False.

* After m.put(k,v) is performed, it holds that m.get(k) == v

* If m.has(k) is False and m.count() == n, then after m.put(k, v) is performed, m.count() == n + 1.

* If m.has(k) is True and m.count() == n, then after m.put(k, v) is performed, m.count() == n.

* If m.get(k) == v, then m.put(k) has no effect on the state of m.

* After m.remove(k) is performed, it holds that m.has(k) is False.

* If m.has(k) is False, then m.remove(k) has no effect on the state of m.

* If m.has(k) is True and m.count() == n, then after m.remove(k) is performed, m.count() = n - 1.

* If k' != k and m.get(k') == v' and m.put(k, v) is performed, then m.get(k') == v' still.

* If k' != k and m.has(k') is False and m.put(k, v) is performed, then m.has(k') is False still.

* If k' != k and m.get(k') == v' and m.remove(k) is performed, then m.get(k') == v' still.

* If k' != k and m.has(k') is False and m.remove(k) is performed, then m.has(k') is False still.

* The size of the set m.keytags() is equal to m.count().

* For any KeyTag object k, k is in m.keytags() if and only m.has(k) is True.


