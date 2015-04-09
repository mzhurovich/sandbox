# KVStorage Deisgn Doc
**KVStorage** is a layer of abstraction above **Sherlock** stream, which implements a key-value storage functionality. It is responsible for keeping in-memory state and data consistency. KVStorage provides API to add, modify and delete data, accesing records by key.

## Data Structure
Each data structure which is supposed to be used in KVStorage should have **Key** and **Value** members.

### Key
Key should implement: 
* `HashFunction` to provide single unique identifier for complex keys
* Comparison operator `==`

## API Structure
There are three groups of access methods:
* Get
* Set
* Delete

For each method there are three types of implementation:
* Synchronous
* Asynchronous via `std::future`
* Asynchronous with callbacks

## Get
### Synchronous version
`ValueType Get[Typename](const KeyType& key);`
If key does not exist, throws an exception.

### Asynchronous version
`std::future<ValueType> AsyncGet[Typename](const KeyType& key);`
If key does not exist, throws an exception.

### Callback version
```
void CallbackGet[Typename](const KeyType& key, std::function<void(ValueType& value)> on_found,
                                               std::function<void(KeyType& key)> on_not_found);
```

## Set

## Delete

## Multiple types support

## Data consistency
