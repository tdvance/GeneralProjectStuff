#Abstract Data Type MKDict

A Multi-Key Dictionary (MKDict) is a dictionary ADT with some
modifictions.  Prerequisite ADTs include the immutable set(ISet),
dictionary (Dict), and immutable dictionary(IDict).



## Immutable Set (ISet)

### Type variable K where K is an immutable type.

###operations and informal notes

* A set is a finite collection of elements, where a given element is
  either in or not in the set (no multiplicity).

* s = new ISet() maps () to ISet s where s is a new, empty set

* s.add(K k) maps (ISet d, K k) to ISet s' where s' contains
  the elements in s, as well as the element k.

* s.has(K k) is a map from (ISet s, K k) to {true, false} where the
 value is true if k is an element of s, and false if not.

* s.remove(K k) maps (ISet s, K k) to ISet s' where s' contains the
  elements of s except for k (if k was an element of s)

* s.count() maps (ISet s) to Integers where the value is the number of
  distinct elements k such that k is an element of s.

### axioms

* (new Iset()).count() == 0 

* s.add(k).has(k) == True

* s.add(j).has(k) = s.has(k) if k != j

* if s.has(k) is true, then s.add(k) == s

* if s.has(k) is false, then s.add(k).count() == s.count() + 1

* (new ISet()).remove(k) = (new ISet())

* s.add(k).remove(k) = s

* s.add(j).remove(k) = s.remove(k).add(j) if k != j

* if s.has(k) is false, then s.remove(k) == s

* if s.has(k) is true, then s.remove(k).count() == s.count() - 1


## Immutable Dictionary (IDict)

### Type variables K, V, where K is an immutable type.

###operations and informal notes

* A dictionary is essentially a set of associations k|->v for k of type
  K and v of type V.  For any given k, there is at most one v such
  that k->v in the dictionary.

* d = new IDict() maps () to IDict s where s is a new, empty
  dictionary

* d.put(K k, V v) maps (IDict d, K k, V v) to IDict d' where d' contains
  the associations in d, as well as the association k|->v.

* d.get(K k) is a partial map from (IDict d, K k) to the unique V v
  such that d contains the association k|->v.  If d contains no such
  association, then the operation fails.

* d.remove(K k) maps (IDict d, K k) to IDict d' where d' contains the
  associations of d except for any association k|->v if one exists.

* d.keys() maps (IDict d) to ISet s such that k is an element of s if and
  only if for some v, there is an association k|->v in d.

### axioms

* (new IDict()).set() == new ISet()

* d.put(k,v).get(k) = v

* d.put(j, v).get(k) = d.get(k) if k != j

* d.keys().has(k) is false if and only if d.get(k) fails

* if d.keys().has(k) is true, then d.put(k,v).keys() == d.keys()

* if d.keys().has(k) is false, then d.put(k,v).keys() == d.keys().add(k)

* (new IDict()).remove(k) = (new IDict())

* d.put(k, v).remove(k) = d.remove(k)

* d.put(j, v).remove(k) = d.remove(k).put(j, v) if k != j

* if d.keys().has(k) is false, then d.remove(k).keys() == d.keys()

* if d.keys().has(k) is true, then d.remove(k).keys() == d.keys().remove(k)

## Dictionary

A (mutable) dictionary Dict is similar to an IDict.  Functionally, it
behaves as folows:

* Setting d <- new Dict() means d behaves as if it is a structure with
  a single modifiable field d.idict == new IDict()

* d.put(k,v) returns nothing but changes d so that d.idict  <-  (d.idict).put(k,v)

* d.remove(k) returns nothing but changes d so that d.idict  <-  (d.idict).remove(k)

* All other IDict operations are supported by d, but are delegated to d.idict.

## KeyTag

A KeyTag object is an extension of an IDict object.  It has the same
behavior as an IDict object, but supports some additional methods:

* If t and t' are KeyTag objects, then t.subsetOf(t') is true or
  false.  It is true if and only if for every k of type K, t.has(k)
  implies t'.has(k).

* If t and t' are KeyTag objects, then t.update(t') is the unique
  KeyTag object such that:

+ t.update(t').has(k) if and only if either  t.has(k) or t'.has(k)

+ If t'.has(k) is false, then t.update(t').get(k) == t.get(k)

+ If t'.has(k) is true, then t.update(t').get(k) == t'.get(k)
 

## MKDict

An MKDict (Multi Key Dictionary) object is an extension of a Dict
object.  It has the same behavior as a Dict object, but has one
restriction and supports some additional methods.

* An MKDict object supports key type only of a KeyTag value.
  Henceforth, we refer to the key type of MKDict not as K, but as
  KeyTag<K, T> where K is the key type for the KeyTag and T is the
  value type (values are called Tags) for the KeyTag.  The value type
  for the MKDict is still denotead by V.

* If m is an MKDict object, m.find(KeyTag t): returns a new MKDict
  object consisting of those associations in m KeyTag t' |-> Value v
  such that t.subsetOf(t') is true.

* If m is an MKDict object, m.remove_all(KeyTag t) behaves as if
  m.remove(KeyTag t') is called on every KeyTag t' such that m.has(t')
  is true and t.subsetOf(t') is true.
