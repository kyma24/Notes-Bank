Python supports the following data structures: lists, dictionaries, tuples, and sets.

**when to use a dictionary**:

-   when you need a logical association between a **key:value** pair.
-   when you need fast lookup for your data, based on a custom key
-   when your data is being constantly modified; remember, dictionaries are mutable.

**when to use other types**:

-   use **lists** if you have a collection of data that doesn't need random access. Try to choose lists when you need a simple, iterable collection that is modified frequently
-   use a **set** if you need uniqueness for the elements
-   use **tuples** when your data is final/can't change

note: many times, a tuple is used in combination with a dictionary. i.e. a tuple might represent a key, because it's immutable.