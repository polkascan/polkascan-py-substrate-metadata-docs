
# Preimage

---------
## Calls

---------
### ensure_updated
#### Attributes
| Name | Type |
| -------- | -------- | 
| hashes | `Vec<T::Hash>` | 

#### Python
```python
call = substrate.compose_call(
    'Preimage', 'ensure_updated', {'hashes': ['scale_info::12']}
)
```

---------
### note_preimage
#### Attributes
| Name | Type |
| -------- | -------- | 
| bytes | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'Preimage', 'note_preimage', {'bytes': 'Bytes'}
)
```

---------
### request_preimage
#### Attributes
| Name | Type |
| -------- | -------- | 
| hash | `T::Hash` | 

#### Python
```python
call = substrate.compose_call(
    'Preimage', 'request_preimage', {'hash': 'scale_info::12'}
)
```

---------
### unnote_preimage
#### Attributes
| Name | Type |
| -------- | -------- | 
| hash | `T::Hash` | 

#### Python
```python
call = substrate.compose_call(
    'Preimage', 'unnote_preimage', {'hash': 'scale_info::12'}
)
```

---------
### unrequest_preimage
#### Attributes
| Name | Type |
| -------- | -------- | 
| hash | `T::Hash` | 

#### Python
```python
call = substrate.compose_call(
    'Preimage', 'unrequest_preimage', {'hash': 'scale_info::12'}
)
```

---------
## Events

---------
### Cleared
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| hash | `T::Hash` | ```scale_info::12```

---------
### Noted
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| hash | `T::Hash` | ```scale_info::12```

---------
### Requested
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| hash | `T::Hash` | ```scale_info::12```

---------
## Storage functions

---------
### PreimageFor

#### Python
```python
result = substrate.query(
    'Preimage', 'PreimageFor', [('scale_info::12', 'u32')]
)
```

#### Return value
```python
'Bytes'
```
---------
### RequestStatusFor

#### Python
```python
result = substrate.query(
    'Preimage', 'RequestStatusFor', ['scale_info::12']
)
```

#### Return value
```python
{
    'Requested': {
        'count': 'u32',
        'maybe_len': (None, 'u32'),
        'maybe_ticket': (None, ('AccountId', 'u128')),
    },
    'Unrequested': {'len': 'u32', 'ticket': ('AccountId', 'u128')},
}
```
---------
### StatusFor

#### Python
```python
result = substrate.query(
    'Preimage', 'StatusFor', ['scale_info::12']
)
```

#### Return value
```python
{
    'Requested': {
        'count': 'u32',
        'deposit': (None, ('AccountId', 'u128')),
        'len': (None, 'u32'),
    },
    'Unrequested': {'deposit': ('AccountId', 'u128'), 'len': 'u32'},
}
```
---------
## Errors

---------
### AlreadyNoted

---------
### NotAuthorized

---------
### NotNoted

---------
### NotRequested

---------
### Requested

---------
### TooBig

---------
### TooFew

---------
### TooMany

---------