//TODO what happens if you use list.remove(Integer.valueOf(77))?
Answer: If the list.remove(Integer.valueOf(77)) is used to remove the element from the list, while an iterator is already
declared and is in execution process, it will cause a ConcurrentModificationException. This is because, an iterator
is meant to be operated in singly threaded instances only. As collections.remove / list.remove() is being
invoked after the iterator is initialized, it is considered multithreaded, hence the exception. If we want to
make use of the iterator.remove() in combination with a list.remove(), the list.remove() needs to be outside the
scope of iterator.remove().

