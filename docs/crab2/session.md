
# Session

---------
## Calls

---------
### purge_keys
See [`Pallet::purge_keys`].
#### Attributes
No attributes

#### Python
```python
call = substrate.compose_call(
    'Session', 'purge_keys', {}
)
```

---------
### set_keys
See [`Pallet::set_keys`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| keys | `T::Keys` | 
| proof | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'Session', 'set_keys', {'keys': {'aura': '[u8; 32]'}, 'proof': 'Bytes'}
)
```

---------
## Events

---------
### NewSession
New session has happened. Note that the argument is the session index, not the
block number as the type might suggest.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| session_index | `SessionIndex` | ```u32```

---------
## Storage functions

---------
### CurrentIndex
 Current index of the session.

#### Python
```python
result = substrate.query(
    'Session', 'CurrentIndex', []
)
```

#### Return value
```python
'u32'
```
---------
### DisabledValidators
 Indices of disabled validators.

 The vec is always kept sorted so that we can find whether a given validator is
 disabled using binary search. It gets cleared when `on_session_ending` returns
 a new set of identities.

#### Python
```python
result = substrate.query(
    'Session', 'DisabledValidators', []
)
```

#### Return value
```python
['u32']
```
---------
### KeyOwner
 The owner of a key. The key is the `KeyTypeId` + the encoded key.

#### Python
```python
result = substrate.query(
    'Session', 'KeyOwner', [('[u8; 4]', 'Bytes')]
)
```

#### Return value
```python
'[u8; 20]'
```
---------
### NextKeys
 The next session keys for a validator.

#### Python
```python
result = substrate.query(
    'Session', 'NextKeys', ['[u8; 20]']
)
```

#### Return value
```python
{'aura': '[u8; 32]'}
```
---------
### QueuedChanged
 True if the underlying economic identities or weighting behind the validators
 has changed in the queued validator set.

#### Python
```python
result = substrate.query(
    'Session', 'QueuedChanged', []
)
```

#### Return value
```python
'bool'
```
---------
### QueuedKeys
 The queued keys for the next session. When the next session begins, these keys
 will be used to determine the validator&#x27;s session keys.

#### Python
```python
result = substrate.query(
    'Session', 'QueuedKeys', []
)
```

#### Return value
```python
[('[u8; 20]', {'aura': '[u8; 32]'})]
```
---------
### Validators
 The current set of validators.

#### Python
```python
result = substrate.query(
    'Session', 'Validators', []
)
```

#### Return value
```python
['[u8; 20]']
```
---------
## Errors

---------
### DuplicatedKey
Registered duplicate key.

---------
### InvalidProof
Invalid ownership proof.

---------
### NoAccount
Key setting account is not live, so it&\#x27;s impossible to associate keys.

---------
### NoAssociatedValidatorId
No associated validator ID for account.

---------
### NoKeys
No keys are associated with this account.

---------