
# System

---------
## Calls

---------
### kill_prefix
See [`Pallet::kill_prefix`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| prefix | `Key` | 
| subkeys | `u32` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'kill_prefix', {'prefix': 'Bytes', 'subkeys': 'u32'}
)
```

---------
### kill_storage
See [`Pallet::kill_storage`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| keys | `Vec<Key>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'kill_storage', {'keys': ['Bytes']}
)
```

---------
### remark
See [`Pallet::remark`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| remark | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'remark', {'remark': 'Bytes'}
)
```

---------
### remark_with_event
See [`Pallet::remark_with_event`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| remark | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'remark_with_event', {'remark': 'Bytes'}
)
```

---------
### set_code
See [`Pallet::set_code`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| code | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'set_code', {'code': 'Bytes'}
)
```

---------
### set_code_without_checks
See [`Pallet::set_code_without_checks`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| code | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'set_code_without_checks', {'code': 'Bytes'}
)
```

---------
### set_heap_pages
See [`Pallet::set_heap_pages`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| pages | `u64` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'set_heap_pages', {'pages': 'u64'}
)
```

---------
### set_storage
See [`Pallet::set_storage`].
#### Attributes
| Name | Type |
| -------- | -------- | 
| items | `Vec<KeyValue>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'set_storage', {'items': [('Bytes', 'Bytes')]}
)
```

---------
## Events

---------
### CodeUpdated
`:code` was updated.
#### Attributes
No attributes

---------
### ExtrinsicFailed
An extrinsic failed.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| dispatch_error | `DispatchError` | ```{'Other': None, 'CannotLookup': None, 'BadOrigin': None, 'Module': {'index': 'u8', 'error': '[u8; 4]'}, 'ConsumerRemaining': None, 'NoProviders': None, 'TooManyConsumers': None, 'Token': ('FundsUnavailable', 'OnlyProvider', 'BelowMinimum', 'CannotCreate', 'UnknownAsset', 'Frozen', 'Unsupported', 'CannotCreateHold', 'NotExpendable', 'Blocked'), 'Arithmetic': ('Underflow', 'Overflow', 'DivisionByZero'), 'Transactional': ('LimitReached', 'NoLayer'), 'Exhausted': None, 'Corruption': None, 'Unavailable': None, 'RootNotAllowed': None}```
| dispatch_info | `DispatchInfo` | ```{'weight': {'ref_time': 'u64', 'proof_size': 'u64'}, 'class': ('Normal', 'Operational', 'Mandatory'), 'pays_fee': ('Yes', 'No')}```

---------
### ExtrinsicSuccess
An extrinsic completed successfully.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| dispatch_info | `DispatchInfo` | ```{'weight': {'ref_time': 'u64', 'proof_size': 'u64'}, 'class': ('Normal', 'Operational', 'Mandatory'), 'pays_fee': ('Yes', 'No')}```

---------
### KilledAccount
An account was reaped.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| account | `T::AccountId` | ```AccountId```

---------
### NewAccount
A new account was created.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| account | `T::AccountId` | ```AccountId```

---------
### Remarked
On on-chain remark happened.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| sender | `T::AccountId` | ```AccountId```
| hash | `T::Hash` | ```scale_info::12```

---------
## Storage functions

---------
### Account
 The full account information for a particular account ID.

#### Python
```python
result = substrate.query(
    'System', 'Account', ['AccountId']
)
```

#### Return value
```python
{
    'consumers': 'u32',
    'data': {
        'flags': 'u128',
        'free': 'u128',
        'frozen': 'u128',
        'reserved': 'u128',
    },
    'nonce': 'u32',
    'providers': 'u32',
    'sufficients': 'u32',
}
```
---------
### AllExtrinsicsLen
 Total length (in bytes) for all extrinsics put together, for the current block.

#### Python
```python
result = substrate.query(
    'System', 'AllExtrinsicsLen', []
)
```

#### Return value
```python
'u32'
```
---------
### BlockHash
 Map of block numbers to block hashes.

#### Python
```python
result = substrate.query(
    'System', 'BlockHash', ['u32']
)
```

#### Return value
```python
'scale_info::12'
```
---------
### BlockWeight
 The current weight for the block.

#### Python
```python
result = substrate.query(
    'System', 'BlockWeight', []
)
```

#### Return value
```python
{
    'mandatory': {'proof_size': 'u64', 'ref_time': 'u64'},
    'normal': {'proof_size': 'u64', 'ref_time': 'u64'},
    'operational': {'proof_size': 'u64', 'ref_time': 'u64'},
}
```
---------
### Digest
 Digest of the current block, also part of the block header.

#### Python
```python
result = substrate.query(
    'System', 'Digest', []
)
```

#### Return value
```python
{
    'logs': [
        {
            None: None,
            'Consensus': ('[u8; 4]', 'Bytes'),
            'Other': 'Bytes',
            'PreRuntime': ('[u8; 4]', 'Bytes'),
            'RuntimeEnvironmentUpdated': None,
            'Seal': ('[u8; 4]', 'Bytes'),
        },
    ],
}
```
---------
### EventCount
 The number of events in the `Events&lt;T&gt;` list.

#### Python
```python
result = substrate.query(
    'System', 'EventCount', []
)
```

#### Return value
```python
'u32'
```
---------
### EventTopics
 Mapping between a topic (represented by T::Hash) and a vector of indexes
 of events in the `&lt;Events&lt;T&gt;&gt;` list.

 All topic vectors have deterministic storage locations depending on the topic. This
 allows light-clients to leverage the changes trie storage tracking mechanism and
 in case of changes fetch the list of events of interest.

 The value has the type `(BlockNumberFor&lt;T&gt;, EventIndex)` because if we used only just
 the `EventIndex` then in case if the topic has the same contents on the next block
 no notification will be triggered thus the event might be lost.

#### Python
```python
result = substrate.query(
    'System', 'EventTopics', ['scale_info::12']
)
```

#### Return value
```python
[('u32', 'u32')]
```
---------
### Events
 Events deposited for the current block.

 NOTE: The item is unbound and should therefore never be read on chain.
 It could otherwise inflate the PoV size of a block.

 Events have a large in-memory size. Box the events to not go out-of-memory
 just in case someone still reads them from within the runtime.

#### Python
```python
result = substrate.query(
    'System', 'Events', []
)
```

#### Return value
```python
[
    {
        'event': {
            'AssetTxPayment': {
                'AssetTxFeePaid': {
                    'actual_fee': 'u128',
                    'asset_id': (None, 'u32'),
                    'tip': 'u128',
                    'who': 'AccountId',
                },
            },
            'Assets': {
                'AccountsDestroyed': {
                    'accounts_destroyed': 'u32',
                    'accounts_remaining': 'u32',
                    'asset_id': 'u32',
                },
                'ApprovalCancelled': {
                    'asset_id': 'u32',
                    'delegate': 'AccountId',
                    'owner': 'AccountId',
                },
                'ApprovalsDestroyed': {
                    'approvals_destroyed': 'u32',
                    'approvals_remaining': 'u32',
                    'asset_id': 'u32',
                },
                'ApprovedTransfer': {
                    'amount': 'u128',
                    'asset_id': 'u32',
                    'delegate': 'AccountId',
                    'source': 'AccountId',
                },
                'AssetFrozen': {'asset_id': 'u32'},
                'AssetMinBalanceChanged': {
                    'asset_id': 'u32',
                    'new_min_balance': 'u128',
                },
                'AssetStatusChanged': {'asset_id': 'u32'},
                'AssetThawed': {'asset_id': 'u32'},
                'Blocked': {'asset_id': 'u32', 'who': 'AccountId'},
                'Burned': {
                    'asset_id': 'u32',
                    'balance': 'u128',
                    'owner': 'AccountId',
                },
                'Created': {
                    'asset_id': 'u32',
                    'creator': 'AccountId',
                    'owner': 'AccountId',
                },
                'Destroyed': {'asset_id': 'u32'},
                'DestructionStarted': {'asset_id': 'u32'},
                'ForceCreated': {'asset_id': 'u32', 'owner': 'AccountId'},
                'Frozen': {'asset_id': 'u32', 'who': 'AccountId'},
                'Issued': {
                    'amount': 'u128',
                    'asset_id': 'u32',
                    'owner': 'AccountId',
                },
                'MetadataCleared': {'asset_id': 'u32'},
                'MetadataSet': {
                    'asset_id': 'u32',
                    'decimals': 'u8',
                    'is_frozen': 'bool',
                    'name': 'Bytes',
                    'symbol': 'Bytes',
                },
                'OwnerChanged': {'asset_id': 'u32', 'owner': 'AccountId'},
                'TeamChanged': {
                    'admin': 'AccountId',
                    'asset_id': 'u32',
                    'freezer': 'AccountId',
                    'issuer': 'AccountId',
                },
                'Thawed': {'asset_id': 'u32', 'who': 'AccountId'},
                'Touched': {
                    'asset_id': 'u32',
                    'depositor': 'AccountId',
                    'who': 'AccountId',
                },
                'Transferred': {
                    'amount': 'u128',
                    'asset_id': 'u32',
                    'from': 'AccountId',
                    'to': 'AccountId',
                },
                'TransferredApproved': {
                    'amount': 'u128',
                    'asset_id': 'u32',
                    'delegate': 'AccountId',
                    'destination': 'AccountId',
                    'owner': 'AccountId',
                },
            },
            'Balances': {
                'BalanceSet': {'free': 'u128', 'who': 'AccountId'},
                'Burned': {'amount': 'u128', 'who': 'AccountId'},
                'Deposit': {'amount': 'u128', 'who': 'AccountId'},
                'DustLost': {'account': 'AccountId', 'amount': 'u128'},
                'Endowed': {'account': 'AccountId', 'free_balance': 'u128'},
                'Frozen': {'amount': 'u128', 'who': 'AccountId'},
                'Issued': {'amount': 'u128'},
                'Locked': {'amount': 'u128', 'who': 'AccountId'},
                'Minted': {'amount': 'u128', 'who': 'AccountId'},
                'Rescinded': {'amount': 'u128'},
                'ReserveRepatriated': {
                    'amount': 'u128',
                    'destination_status': 'scale_info::33',
                    'from': 'AccountId',
                    'to': 'AccountId',
                },
                'Reserved': {'amount': 'u128', 'who': 'AccountId'},
                'Restored': {'amount': 'u128', 'who': 'AccountId'},
                'Slashed': {'amount': 'u128', 'who': 'AccountId'},
                'Suspended': {'amount': 'u128', 'who': 'AccountId'},
                'Thawed': {'amount': 'u128', 'who': 'AccountId'},
                'Transfer': {
                    'amount': 'u128',
                    'from': 'AccountId',
                    'to': 'AccountId',
                },
                'Unlocked': {'amount': 'u128', 'who': 'AccountId'},
                'Unreserved': {'amount': 'u128', 'who': 'AccountId'},
                'Upgraded': {'who': 'AccountId'},
                'Withdraw': {'amount': 'u128', 'who': 'AccountId'},
            },
            'CollatorSelection': {
                'CandidateAdded': {
                    'account_id': 'AccountId',
                    'deposit': 'u128',
                },
                'CandidateRemoved': {'account_id': 'AccountId'},
                'InvalidInvulnerableSkipped': {'account_id': 'AccountId'},
                'InvulnerableAdded': {'account_id': 'AccountId'},
                'InvulnerableRemoved': {'account_id': 'AccountId'},
                'NewCandidacyBond': {'bond_amount': 'u128'},
                'NewDesiredCandidates': {'desired_candidates': 'u32'},
                'NewInvulnerables': {'invulnerables': ['AccountId']},
            },
            'CumulusXcm': {
                'ExecutedDownward': ('[u8; 32]', 'scale_info::44'),
                'InvalidFormat': '[u8; 32]',
                'UnsupportedVersion': '[u8; 32]',
            },
            'DmpQueue': {
                'ExecutedDownward': {
                    'message_hash': '[u8; 32]',
                    'message_id': '[u8; 32]',
                    'outcome': 'scale_info::44',
                },
                'InvalidFormat': {'message_hash': '[u8; 32]'},
                'MaxMessagesExhausted': {'message_hash': '[u8; 32]'},
                'OverweightEnqueued': {
                    'message_hash': '[u8; 32]',
                    'message_id': '[u8; 32]',
                    'overweight_index': 'u64',
                    'required_weight': 'scale_info::9',
                },
                'OverweightServiced': {
                    'overweight_index': 'u64',
                    'weight_used': 'scale_info::9',
                },
                'UnsupportedVersion': {'message_hash': '[u8; 32]'},
                'WeightExhausted': {
                    'message_hash': '[u8; 32]',
                    'message_id': '[u8; 32]',
                    'remaining_weight': 'scale_info::9',
                    'required_weight': 'scale_info::9',
                },
            },
            'ForeignAssets': {
                'AccountsDestroyed': {
                    'accounts_destroyed': 'u32',
                    'accounts_remaining': 'u32',
                    'asset_id': 'scale_info::45',
                },
                'ApprovalCancelled': {
                    'asset_id': 'scale_info::45',
                    'delegate': 'AccountId',
                    'owner': 'AccountId',
                },
                'ApprovalsDestroyed': {
                    'approvals_destroyed': 'u32',
                    'approvals_remaining': 'u32',
                    'asset_id': 'scale_info::45',
                },
                'ApprovedTransfer': {
                    'amount': 'u128',
                    'asset_id': 'scale_info::45',
                    'delegate': 'AccountId',
                    'source': 'AccountId',
                },
                'AssetFrozen': {'asset_id': 'scale_info::45'},
                'AssetMinBalanceChanged': {
                    'asset_id': 'scale_info::45',
                    'new_min_balance': 'u128',
                },
                'AssetStatusChanged': {'asset_id': 'scale_info::45'},
                'AssetThawed': {'asset_id': 'scale_info::45'},
                'Blocked': {'asset_id': 'scale_info::45', 'who': 'AccountId'},
                'Burned': {
                    'asset_id': 'scale_info::45',
                    'balance': 'u128',
                    'owner': 'AccountId',
                },
                'Created': {
                    'asset_id': 'scale_info::45',
                    'creator': 'AccountId',
                    'owner': 'AccountId',
                },
                'Destroyed': {'asset_id': 'scale_info::45'},
                'DestructionStarted': {'asset_id': 'scale_info::45'},
                'ForceCreated': {
                    'asset_id': 'scale_info::45',
                    'owner': 'AccountId',
                },
                'Frozen': {'asset_id': 'scale_info::45', 'who': 'AccountId'},
                'Issued': {
                    'amount': 'u128',
                    'asset_id': 'scale_info::45',
                    'owner': 'AccountId',
                },
                'MetadataCleared': {'asset_id': 'scale_info::45'},
                'MetadataSet': {
                    'asset_id': 'scale_info::45',
                    'decimals': 'u8',
                    'is_frozen': 'bool',
                    'name': 'Bytes',
                    'symbol': 'Bytes',
                },
                'OwnerChanged': {
                    'asset_id': 'scale_info::45',
                    'owner': 'AccountId',
                },
                'TeamChanged': {
                    'admin': 'AccountId',
                    'asset_id': 'scale_info::45',
                    'freezer': 'AccountId',
                    'issuer': 'AccountId',
                },
                'Thawed': {'asset_id': 'scale_info::45', 'who': 'AccountId'},
                'Touched': {
                    'asset_id': 'scale_info::45',
                    'depositor': 'AccountId',
                    'who': 'AccountId',
                },
                'Transferred': {
                    'amount': 'u128',
                    'asset_id': 'scale_info::45',
                    'from': 'AccountId',
                    'to': 'AccountId',
                },
                'TransferredApproved': {
                    'amount': 'u128',
                    'asset_id': 'scale_info::45',
                    'delegate': 'AccountId',
                    'destination': 'AccountId',
                    'owner': 'AccountId',
                },
            },
            'Multisig': {
                'MultisigApproval': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                    'timepoint': 'scale_info::105',
                },
                'MultisigCancelled': {
                    'call_hash': '[u8; 32]',
                    'cancelling': 'AccountId',
                    'multisig': 'AccountId',
                    'timepoint': 'scale_info::105',
                },
                'MultisigExecuted': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                    'result': 'scale_info::102',
                    'timepoint': 'scale_info::105',
                },
                'NewMultisig': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                },
            },
            'Nfts': {
                'AllApprovalsCancelled': {
                    'collection': 'u32',
                    'item': 'u32',
                    'owner': 'AccountId',
                },
                'ApprovalCancelled': {
                    'collection': 'u32',
                    'delegate': 'AccountId',
                    'item': 'u32',
                    'owner': 'AccountId',
                },
                'AttributeCleared': {
                    'collection': 'u32',
                    'key': 'Bytes',
                    'maybe_item': (None, 'u32'),
                    'namespace': 'scale_info::118',
                },
                'AttributeSet': {
                    'collection': 'u32',
                    'key': 'Bytes',
                    'maybe_item': (None, 'u32'),
                    'namespace': 'scale_info::118',
                    'value': 'Bytes',
                },
                'Burned': {
                    'collection': 'u32',
                    'item': 'u32',
                    'owner': 'AccountId',
                },
                'CollectionConfigChanged': {'collection': 'u32'},
                'CollectionLocked': {'collection': 'u32'},
                'CollectionMaxSupplySet': {
                    'collection': 'u32',
                    'max_supply': 'u32',
                },
                'CollectionMetadataCleared': {'collection': 'u32'},
                'CollectionMetadataSet': {
                    'collection': 'u32',
                    'data': 'Bytes',
                },
                'CollectionMintSettingsUpdated': {'collection': 'u32'},
                'Created': {
                    'collection': 'u32',
                    'creator': 'AccountId',
                    'owner': 'AccountId',
                },
                'Destroyed': {'collection': 'u32'},
                'ForceCreated': {'collection': 'u32', 'owner': 'AccountId'},
                'Issued': {
                    'collection': 'u32',
                    'item': 'u32',
                    'owner': 'AccountId',
                },
                'ItemAttributesApprovalAdded': {
                    'collection': 'u32',
                    'delegate': 'AccountId',
                    'item': 'u32',
                },
                'ItemAttributesApprovalRemoved': {
                    'collection': 'u32',
                    'delegate': 'AccountId',
                    'item': 'u32',
                },
                'ItemBought': {
                    'buyer': 'AccountId',
                    'collection': 'u32',
                    'item': 'u32',
                    'price': 'u128',
                    'seller': 'AccountId',
                },
                'ItemMetadataCleared': {'collection': 'u32', 'item': 'u32'},
                'ItemMetadataSet': {
                    'collection': 'u32',
                    'data': 'Bytes',
                    'item': 'u32',
                },
                'ItemPriceRemoved': {'collection': 'u32', 'item': 'u32'},
                'ItemPriceSet': {
                    'collection': 'u32',
                    'item': 'u32',
                    'price': 'u128',
                    'whitelisted_buyer': (None, 'AccountId'),
                },
                'ItemPropertiesLocked': {
                    'collection': 'u32',
                    'item': 'u32',
                    'lock_attributes': 'bool',
                    'lock_metadata': 'bool',
                },
                'ItemTransferLocked': {'collection': 'u32', 'item': 'u32'},
                'ItemTransferUnlocked': {'collection': 'u32', 'item': 'u32'},
                'NextCollectionIdIncremented': {'next_id': (None, 'u32')},
                'OwnerChanged': {
                    'collection': 'u32',
                    'new_owner': 'AccountId',
                },
                'OwnershipAcceptanceChanged': {
                    'maybe_collection': (None, 'u32'),
                    'who': 'AccountId',
                },
                'PalletAttributeSet': {
                    'attribute': 'scale_info::122',
                    'collection': 'u32',
                    'item': (None, 'u32'),
                    'value': 'Bytes',
                },
                'PreSignedAttributesSet': {
                    'collection': 'u32',
                    'item': 'u32',
                    'namespace': 'scale_info::118',
                },
                'Redeposited': {
                    'collection': 'u32',
                    'successful_items': ['u32'],
                },
                'SwapCancelled': {
                    'deadline': 'u32',
                    'desired_collection': 'u32',
                    'desired_item': (None, 'u32'),
                    'offered_collection': 'u32',
                    'offered_item': 'u32',
                    'price': (None, 'scale_info::120'),
                },
                'SwapClaimed': {
                    'deadline': 'u32',
                    'price': (None, 'scale_info::120'),
                    'received_collection': 'u32',
                    'received_item': 'u32',
                    'received_item_owner': 'AccountId',
                    'sent_collection': 'u32',
                    'sent_item': 'u32',
                    'sent_item_owner': 'AccountId',
                },
                'SwapCreated': {
                    'deadline': 'u32',
                    'desired_collection': 'u32',
                    'desired_item': (None, 'u32'),
                    'offered_collection': 'u32',
                    'offered_item': 'u32',
                    'price': (None, 'scale_info::120'),
                },
                'TeamChanged': {
                    'admin': (None, 'AccountId'),
                    'collection': 'u32',
                    'freezer': (None, 'AccountId'),
                    'issuer': (None, 'AccountId'),
                },
                'TipSent': {
                    'amount': 'u128',
                    'collection': 'u32',
                    'item': 'u32',
                    'receiver': 'AccountId',
                    'sender': 'AccountId',
                },
                'TransferApproved': {
                    'collection': 'u32',
                    'deadline': (None, 'u32'),
                    'delegate': 'AccountId',
                    'item': 'u32',
                    'owner': 'AccountId',
                },
                'Transferred': {
                    'collection': 'u32',
                    'from': 'AccountId',
                    'item': 'u32',
                    'to': 'AccountId',
                },
            },
            'ParachainSystem': {
                'DownwardMessagesProcessed': {
                    'dmq_head': 'scale_info::12',
                    'weight_used': 'scale_info::9',
                },
                'DownwardMessagesReceived': {'count': 'u32'},
                'UpgradeAuthorized': {'code_hash': 'scale_info::12'},
                'UpwardMessageSent': {'message_hash': (None, '[u8; 32]')},
                'ValidationFunctionApplied': {'relay_chain_block_num': 'u32'},
                'ValidationFunctionDiscarded': None,
                'ValidationFunctionStored': None,
            },
            'PolkadotXcm': {
                'AssetsClaimed': {
                    'assets': 'scale_info::84',
                    'hash': 'scale_info::12',
                    'origin': 'scale_info::45',
                },
                'AssetsTrapped': {
                    'assets': 'scale_info::84',
                    'hash': 'scale_info::12',
                    'origin': 'scale_info::45',
                },
                'Attempted': {'outcome': 'scale_info::44'},
                'FeesPaid': {'fees': ['scale_info::60'], 'paying': 'scale_info::45'},
                'InvalidQuerier': {
                    'expected_querier': 'scale_info::45',
                    'maybe_actual_querier': (None, 'scale_info::45'),
                    'origin': 'scale_info::45',
                    'query_id': 'u64',
                },
                'InvalidQuerierVersion': {
                    'origin': 'scale_info::45',
                    'query_id': 'u64',
                },
                'InvalidResponder': {
                    'expected_location': (None, 'scale_info::45'),
                    'origin': 'scale_info::45',
                    'query_id': 'u64',
                },
                'InvalidResponderVersion': {
                    'origin': 'scale_info::45',
                    'query_id': 'u64',
                },
                'Notified': {
                    'call_index': 'u8',
                    'pallet_index': 'u8',
                    'query_id': 'u64',
                },
                'NotifyDecodeFailed': {
                    'call_index': 'u8',
                    'pallet_index': 'u8',
                    'query_id': 'u64',
                },
                'NotifyDispatchError': {
                    'call_index': 'u8',
                    'pallet_index': 'u8',
                    'query_id': 'u64',
                },
                'NotifyOverweight': {
                    'actual_weight': 'scale_info::9',
                    'call_index': 'u8',
                    'max_budgeted_weight': 'scale_info::9',
                    'pallet_index': 'u8',
                    'query_id': 'u64',
                },
                'NotifyTargetMigrationFail': {
                    'location': 'scale_info::98',
                    'query_id': 'u64',
                },
                'NotifyTargetSendFail': {
                    'error': 'scale_info::41',
                    'location': 'scale_info::45',
                    'query_id': 'u64',
                },
                'ResponseReady': {
                    'query_id': 'u64',
                    'response': 'scale_info::66',
                },
                'ResponseTaken': {'query_id': 'u64'},
                'Sent': {
                    'destination': 'scale_info::45',
                    'message': ['scale_info::57'],
                    'message_id': '[u8; 32]',
                    'origin': 'scale_info::45',
                },
                'SupportedVersionChanged': {
                    'location': 'scale_info::45',
                    'version': 'u32',
                },
                'UnexpectedResponse': {
                    'origin': 'scale_info::45',
                    'query_id': 'u64',
                },
                'VersionChangeNotified': {
                    'cost': ['scale_info::60'],
                    'destination': 'scale_info::45',
                    'message_id': '[u8; 32]',
                    'result': 'u32',
                },
                'VersionNotifyRequested': {
                    'cost': ['scale_info::60'],
                    'destination': 'scale_info::45',
                    'message_id': '[u8; 32]',
                },
                'VersionNotifyStarted': {
                    'cost': ['scale_info::60'],
                    'destination': 'scale_info::45',
                    'message_id': '[u8; 32]',
                },
                'VersionNotifyUnrequested': {
                    'cost': ['scale_info::60'],
                    'destination': 'scale_info::45',
                    'message_id': '[u8; 32]',
                },
            },
            'Proxy': {
                'Announced': {
                    'call_hash': 'scale_info::12',
                    'proxy': 'AccountId',
                    'real': 'AccountId',
                },
                'ProxyAdded': {
                    'delay': 'u32',
                    'delegatee': 'AccountId',
                    'delegator': 'AccountId',
                    'proxy_type': 'scale_info::107',
                },
                'ProxyExecuted': {'result': 'scale_info::102'},
                'ProxyRemoved': {
                    'delay': 'u32',
                    'delegatee': 'AccountId',
                    'delegator': 'AccountId',
                    'proxy_type': 'scale_info::107',
                },
                'PureCreated': {
                    'disambiguation_index': 'u16',
                    'proxy_type': 'scale_info::107',
                    'pure': 'AccountId',
                    'who': 'AccountId',
                },
            },
            'Session': {'NewSession': {'session_index': 'u32'}},
            'System': {
                'CodeUpdated': None,
                'ExtrinsicFailed': {
                    'dispatch_error': 'scale_info::25',
                    'dispatch_info': 'scale_info::22',
                },
                'ExtrinsicSuccess': {'dispatch_info': 'scale_info::22'},
                'KilledAccount': {'account': 'AccountId'},
                'NewAccount': {'account': 'AccountId'},
                'Remarked': {'hash': 'scale_info::12', 'sender': 'AccountId'},
            },
            'TransactionPayment': {
                'TransactionFeePaid': {
                    'actual_fee': 'u128',
                    'tip': 'u128',
                    'who': 'AccountId',
                },
            },
            'Uniques': {
                'ApprovalCancelled': {
                    'collection': 'u32',
                    'delegate': 'AccountId',
                    'item': 'u32',
                    'owner': 'AccountId',
                },
                'ApprovedTransfer': {
                    'collection': 'u32',
                    'delegate': 'AccountId',
                    'item': 'u32',
                    'owner': 'AccountId',
                },
                'AttributeCleared': {
                    'collection': 'u32',
                    'key': 'Bytes',
                    'maybe_item': (None, 'u32'),
                },
                'AttributeSet': {
                    'collection': 'u32',
                    'key': 'Bytes',
                    'maybe_item': (None, 'u32'),
                    'value': 'Bytes',
                },
                'Burned': {
                    'collection': 'u32',
                    'item': 'u32',
                    'owner': 'AccountId',
                },
                'CollectionFrozen': {'collection': 'u32'},
                'CollectionMaxSupplySet': {
                    'collection': 'u32',
                    'max_supply': 'u32',
                },
                'CollectionMetadataCleared': {'collection': 'u32'},
                'CollectionMetadataSet': {
                    'collection': 'u32',
                    'data': 'Bytes',
                    'is_frozen': 'bool',
                },
                'CollectionThawed': {'collection': 'u32'},
                'Created': {
                    'collection': 'u32',
                    'creator': 'AccountId',
                    'owner': 'AccountId',
                },
                'Destroyed': {'collection': 'u32'},
                'ForceCreated': {'collection': 'u32', 'owner': 'AccountId'},
                'Frozen': {'collection': 'u32', 'item': 'u32'},
                'Issued': {
                    'collection': 'u32',
                    'item': 'u32',
                    'owner': 'AccountId',
                },
                'ItemBought': {
                    'buyer': 'AccountId',
                    'collection': 'u32',
                    'item': 'u32',
                    'price': 'u128',
                    'seller': 'AccountId',
                },
                'ItemPriceRemoved': {'collection': 'u32', 'item': 'u32'},
                'ItemPriceSet': {
                    'collection': 'u32',
                    'item': 'u32',
                    'price': 'u128',
                    'whitelisted_buyer': (None, 'AccountId'),
                },
                'ItemStatusChanged': {'collection': 'u32'},
                'MetadataCleared': {'collection': 'u32', 'item': 'u32'},
                'MetadataSet': {
                    'collection': 'u32',
                    'data': 'Bytes',
                    'is_frozen': 'bool',
                    'item': 'u32',
                },
                'OwnerChanged': {
                    'collection': 'u32',
                    'new_owner': 'AccountId',
                },
                'OwnershipAcceptanceChanged': {
                    'maybe_collection': (None, 'u32'),
                    'who': 'AccountId',
                },
                'Redeposited': {
                    'collection': 'u32',
                    'successful_items': ['u32'],
                },
                'TeamChanged': {
                    'admin': 'AccountId',
                    'collection': 'u32',
                    'freezer': 'AccountId',
                    'issuer': 'AccountId',
                },
                'Thawed': {'collection': 'u32', 'item': 'u32'},
                'Transferred': {
                    'collection': 'u32',
                    'from': 'AccountId',
                    'item': 'u32',
                    'to': 'AccountId',
                },
            },
            'Utility': {
                'BatchCompleted': None,
                'BatchCompletedWithErrors': None,
                'BatchInterrupted': {
                    'error': 'scale_info::25',
                    'index': 'u32',
                },
                'DispatchedAs': {'result': 'scale_info::102'},
                'ItemCompleted': None,
                'ItemFailed': {'error': 'scale_info::25'},
            },
            'XcmpQueue': {
                'BadFormat': {'message_hash': '[u8; 32]'},
                'BadVersion': {'message_hash': '[u8; 32]'},
                'Fail': {
                    'error': 'scale_info::41',
                    'message_hash': '[u8; 32]',
                    'message_id': '[u8; 32]',
                    'weight': 'scale_info::9',
                },
                'OverweightEnqueued': {
                    'index': 'u64',
                    'required': 'scale_info::9',
                    'sender': 'u32',
                    'sent_at': 'u32',
                },
                'OverweightServiced': {
                    'index': 'u64',
                    'used': 'scale_info::9',
                },
                'Success': {
                    'message_hash': '[u8; 32]',
                    'message_id': '[u8; 32]',
                    'weight': 'scale_info::9',
                },
                'XcmpMessageSent': {'message_hash': '[u8; 32]'},
            },
            None: None,
        },
        'phase': {
            'ApplyExtrinsic': 'u32',
            'Finalization': None,
            'Initialization': None,
        },
        'topics': ['scale_info::12'],
    },
]
```
---------
### ExecutionPhase
 The execution phase of the block.

#### Python
```python
result = substrate.query(
    'System', 'ExecutionPhase', []
)
```

#### Return value
```python
{'ApplyExtrinsic': 'u32', 'Finalization': None, 'Initialization': None}
```
---------
### ExtrinsicCount
 Total extrinsics count for the current block.

#### Python
```python
result = substrate.query(
    'System', 'ExtrinsicCount', []
)
```

#### Return value
```python
'u32'
```
---------
### ExtrinsicData
 Extrinsics data for the current block (maps an extrinsic&#x27;s index to its data).

#### Python
```python
result = substrate.query(
    'System', 'ExtrinsicData', ['u32']
)
```

#### Return value
```python
'Bytes'
```
---------
### LastRuntimeUpgrade
 Stores the `spec_version` and `spec_name` of when the last runtime upgrade happened.

#### Python
```python
result = substrate.query(
    'System', 'LastRuntimeUpgrade', []
)
```

#### Return value
```python
{'spec_name': 'Str', 'spec_version': 'u32'}
```
---------
### Number
 The current block number being processed. Set by `execute_block`.

#### Python
```python
result = substrate.query(
    'System', 'Number', []
)
```

#### Return value
```python
'u32'
```
---------
### ParentHash
 Hash of the previous block.

#### Python
```python
result = substrate.query(
    'System', 'ParentHash', []
)
```

#### Return value
```python
'scale_info::12'
```
---------
### UpgradedToTripleRefCount
 True if we have upgraded so that AccountInfo contains three types of `RefCount`. False
 (default) if not.

#### Python
```python
result = substrate.query(
    'System', 'UpgradedToTripleRefCount', []
)
```

#### Return value
```python
'bool'
```
---------
### UpgradedToU32RefCount
 True if we have upgraded so that `type RefCount` is `u32`. False (default) if not.

#### Python
```python
result = substrate.query(
    'System', 'UpgradedToU32RefCount', []
)
```

#### Return value
```python
'bool'
```
---------
## Constants

---------
### BlockHashCount
 Maximum number of block number to block hash mappings to keep (oldest pruned first).
#### Value
```python
4096
```
#### Python
```python
constant = substrate.get_constant('System', 'BlockHashCount')
```
---------
### BlockLength
 The maximum length of a block (in bytes).
#### Value
```python
{'max': {'mandatory': 5242880, 'normal': 3932160, 'operational': 5242880}}
```
#### Python
```python
constant = substrate.get_constant('System', 'BlockLength')
```
---------
### BlockWeights
 Block &amp; extrinsics weights: base values and limits.
#### Value
```python
{
    'base_block': {'proof_size': 0, 'ref_time': 5000000000},
    'max_block': {'proof_size': 5242880, 'ref_time': 500000000000},
    'per_class': {
        'mandatory': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 125000000},
            'max_extrinsic': None,
            'max_total': None,
            'reserved': None,
        },
        'normal': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 125000000},
            'max_extrinsic': {'proof_size': 3670016, 'ref_time': 349875000000},
            'max_total': {'proof_size': 3932160, 'ref_time': 375000000000},
            'reserved': {'proof_size': 0, 'ref_time': 0},
        },
        'operational': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 125000000},
            'max_extrinsic': {'proof_size': 4980736, 'ref_time': 474875000000},
            'max_total': {'proof_size': 5242880, 'ref_time': 500000000000},
            'reserved': {'proof_size': 1310720, 'ref_time': 125000000000},
        },
    },
}
```
#### Python
```python
constant = substrate.get_constant('System', 'BlockWeights')
```
---------
### DbWeight
 The weight of runtime database operations the runtime can invoke.
#### Value
```python
{'read': 25000000, 'write': 100000000}
```
#### Python
```python
constant = substrate.get_constant('System', 'DbWeight')
```
---------
### SS58Prefix
 The designated SS58 prefix of this chain.

 This replaces the &quot;ss58Format&quot; property declared in the chain spec. Reason is
 that the runtime should know about the prefix in order to make use of it as
 an identifier of the chain.
#### Value
```python
0
```
#### Python
```python
constant = substrate.get_constant('System', 'SS58Prefix')
```
---------
### Version
 Get the chain&#x27;s current version.
#### Value
```python
{
    'apis': [
        ('0xdd718d5cc53262d4', 1),
        ('0xdf6acb689907609b', 4),
        ('0x37e397fc7c91f5e4', 2),
        ('0x40fe3ad401f8959a', 6),
        ('0xd2bc9897eed08f15', 3),
        ('0xf78b278be53f454c', 2),
        ('0xab3c0572291feb8b', 1),
        ('0xbc9d89904f5b923f', 1),
        ('0x37c8bb1350a9a2a8', 4),
        ('0xf3ff14d5ab527059', 3),
        ('0xde92b8a0426b9bf6', 2),
        ('0xea93e3f16f3d6962', 2),
        ('0xfbc577b9d747efd6', 1),
    ],
    'authoring_version': 1,
    'impl_name': 'statemint',
    'impl_version': 0,
    'spec_name': 'statemint',
    'spec_version': 1001002,
    'state_version': 0,
    'transaction_version': 14,
}
```
#### Python
```python
constant = substrate.get_constant('System', 'Version')
```
---------
## Errors

---------
### CallFiltered
The origin filter prevent the call to be dispatched.

---------
### FailedToExtractRuntimeVersion
Failed to extract the runtime version from the new runtime.

Either calling `Core_version` or decoding `RuntimeVersion` failed.

---------
### InvalidSpecName
The name of specification does not match between the current runtime
and the new runtime.

---------
### NonDefaultComposite
Suicide called when the account has non-default composite data.

---------
### NonZeroRefCount
There is a non-zero reference count preventing the account from being purged.

---------
### SpecVersionNeedsToIncrease
The specification version is not allowed to decrease between the current runtime
and the new runtime.

---------