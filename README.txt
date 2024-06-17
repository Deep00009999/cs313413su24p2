// In class TestIterator:
//TODO what happens if you use list.remove(Integer.valueOf(77))?
Answer: If the list.remove(Integer.valueOf(77)) is used to remove the element from the list, while an iterator is already
declared and is in execution process, it will cause a ConcurrentModificationException. This is because, an iterator
is meant to be operated in singly threaded instances only. As collections.remove / list.remove() is being
invoked after the iterator is initialized, it is considered multithreaded, hence the exception. If we want to
make use of the iterator.remove() in combination with a list.remove(), the list.remove() needs to be outside the
scope of iterator.remove().

//TODO also try with a LinkedList - does it make any difference?
No difference in behavior

//In class TestList
//list.remove(5); // what does this method do?
this method removes the element at index 5, which is 77.
//TODO also try with a LinkedList - does it make any difference?
No difference in behavior

//In class TestPerformance
As the size of the data set increases, following are the summary of observations :

-> ArrayLists are performing better for (random) access
-> LinkedLists are performing better for add/remove operations

-> LinkedLists are yielding the worst performance for (random) access
-> ArrayLists are yielding the worst performance for add/remove operations

In conclusion, the insert, add, remove operations are faster in LinkedList as no resizing of an array
is performed under the hood. Only the references(addresses) of the neighboring elements needs an update.
While the ArrayLists provide the best performance for random access and not best for adding/removing elements from the
list as resizing of an array or the copying all the elements into a new one is performed in the background.


=========================================================
For Size = 10, REPS = 1000000, Overall runtime = ~285ms
=========================================================
8ms testArrayListAccess
18ms testLinkedListAddRemove
10ms testLinkedListAccess
253ms testArrayListAddRemove
==========================================================
For Size = 100, REPS = 1000000, Overall runtime = ~361ms
==========================================================
9ms testArrayListAccess
17ms testLinkedListAddRemove
17ms testLinkedListAccess
318ms testArrayListAddRemove
==========================================================
For Size = 1000, REPS = 1000000, Overall runtime = ~643ms
==========================================================
8ms testArrayListAccess
14ms testLinkedListAddRemove
234ms testLinkedListAccess
387ms testArrayListAddRemove
============================================================================
For Size = 100000, REPS = 1000000, Overall runtime = ~3sec,965ms or 3,965ms
============================================================================
11ms testArrayListAccess
17ms testLinkedListAddRemove
2.90s (2,900ms) testLinkedListAccess
1.04s (1,040ms) testArrayListAddRemove
============================================================================
For Size = 100000, REPS = 1000000, Overall runtime = ~41sec,02ms or 41,002ms
============================================================================
23ms testArrayListAccess
26ms testLinkedListAddRemove
29.01s (29,001ms) testLinkedListAccess
11.96s (11,096ms) testArrayListAddRemove
============================================================================
For Size = 1000000, REPS = 1000000, Overall runtime = 33 min 5 sec
============================================================================
144ms testArrayListAccess
254ms testLinkedListAddRemove
29 min 52 sec testLinkedListAccess
3 min 13 sec testArrayListAddRemove
