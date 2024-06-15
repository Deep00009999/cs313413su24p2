//TODO what happens if you use list.remove(Integer.valueOf(77))?
Answer: If the list.remove(Integer.valueOf(77)) is used to remove the element from the list, while an iterator is already
declared and is in execution process, it will cause a ConcurrentModificationException. This is because, an iterator
is meant to be operated in singly threaded instances only. As collections.remove / list.remove() is being
invoked after the iterator is initialized, it is considered multithreaded, hence the exception. If we want to
make use of the iterator.remove() in combination with a list.remove(), the list.remove() needs to be outside the
scope of iterator.remove().

//TODO also try with a LinkedList - does it make any difference?
When using a LinkedList instead of an ArrayList there is a chance of slight increase in performance. This is because
LinkedList doesn't do any array resizing under the hood while arrayList does an array resizing. As a (doubly)LinkedList operates
based on the nodes of the next element it consumes the memory required to store that address. On the other side the Lists
doesn't need to store the address so it saves some memory. Overall functionality wise there will be no difference.

