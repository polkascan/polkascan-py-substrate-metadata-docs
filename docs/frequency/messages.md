
# Messages

---------
## Calls

---------
### add_ipfs_message
#### Attributes
| Name | Type |
| -------- | -------- | 
| schema_id | `SchemaId` | 
| cid | `Vec<u8>` | 
| payload_length | `u32` | 

#### Python
```python
call = substrate.compose_call(
    'Messages', 'add_ipfs_message', {
    'cid': 'Bytes',
    'payload_length': 'u32',
    'schema_id': 'u16',
}
)
```

---------
### add_onchain_message
#### Attributes
| Name | Type |
| -------- | -------- | 
| on_behalf_of | `Option<MessageSourceId>` | 
| schema_id | `SchemaId` | 
| payload | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'Messages', 'add_onchain_message', {
    'on_behalf_of': (None, 'u64'),
    'payload': 'Bytes',
    'schema_id': 'u16',
}
)
```

---------
## Events

---------
### MessagesInBlock
#### Attributes
No attributes

---------
### MessagesStored
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| schema_id | `SchemaId` | ```u16```
| block_number | `BlockNumberFor<T>` | ```u32```

---------
## Storage functions

---------
### BlockMessageIndex

#### Python
```python
result = substrate.query(
    'Messages', 'BlockMessageIndex', []
)
```

#### Return value
```python
'u16'
```
---------
### MessagesV2

#### Python
```python
result = substrate.query(
    'Messages', 'MessagesV2', ['u32', 'u16', 'u16']
)
```

#### Return value
```python
{'msa_id': (None, 'u64'), 'payload': 'Bytes', 'provider_msa_id': 'u64'}
```
---------
## Constants

---------
### MessagesMaxPayloadSizeBytes
#### Value
```python
3072
```
#### Python
```python
constant = substrate.get_constant('Messages', 'MessagesMaxPayloadSizeBytes')
```
---------
## Errors

---------
### ExceedsMaxMessagePayloadSizeBytes

---------
### InvalidCid

---------
### InvalidMessageSourceAccount

---------
### InvalidPayloadLocation

---------
### InvalidSchemaId

---------
### TooManyMessagesInBlock

---------
### TypeConversionOverflow

---------
### UnAuthorizedDelegate

---------
### UnsupportedCidVersion

---------