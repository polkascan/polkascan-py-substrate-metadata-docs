
# System

---------
## Calls

---------
### kill_prefix
Kill all storage items with a key that starts with the given prefix.

**NOTE:** We rely on the Root origin to provide us the number of subkeys under
the prefix we are removing to accurately calculate the weight of this function.
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
Kill some items from storage.
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
Make some on-chain remark.

- `O(1)`
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
Make some on-chain remark and emit event.
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
Set the new runtime code.
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
Set the new runtime code without doing any checks of the given `code`.
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
Set the number of pages in the WebAssembly environment&\#x27;s heap.
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
Set some items of storage.
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

 The value has the type `(T::BlockNumber, EventIndex)` because if we used only just
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
            'AssetManager': {
                'AssetLocationFilteredForOutgoingTransfers': {
                    'filtered_location': 'scale_info::118',
                },
                'AssetLocationUnfilteredForOutgoingTransfers': {
                    'filtered_location': 'scale_info::118',
                },
                'AssetLocationUpdated': {
                    'asset_id': 'u128',
                    'location': 'scale_info::118',
                },
                'AssetMetadataUpdated': {
                    'asset_id': 'u128',
                    'metadata': 'scale_info::128',
                },
                'AssetMinted': {
                    'amount': 'u128',
                    'asset_id': 'u128',
                    'beneficiary': 'AccountId',
                },
                'AssetRegistered': {
                    'asset_id': 'u128',
                    'location': 'scale_info::118',
                    'metadata': 'scale_info::128',
                },
                'LPAssetRegistered': {
                    'asset_id': 'u128',
                    'asset_id0': 'u128',
                    'asset_id1': 'u128',
                    'metadata': 'scale_info::128',
                },
                'MinXcmFeeUpdated': {
                    'min_xcm_fee': 'u128',
                    'reserve_chain': 'scale_info::118',
                },
                'PermissionlessAssetRegistered': {
                    'asset_id': 'u128',
                    'metadata': 'scale_info::128',
                },
                'UnitsPerSecondUpdated': {
                    'asset_id': 'u128',
                    'units_per_second': 'u128',
                },
            },
            'Assets': {
                'AccountsDestroyed': {
                    'accounts_destroyed': 'u32',
                    'accounts_remaining': 'u32',
                    'asset_id': 'u128',
                },
                'ApprovalCancelled': {
                    'asset_id': 'u128',
                    'delegate': 'AccountId',
                    'owner': 'AccountId',
                },
                'ApprovalsDestroyed': {
                    'approvals_destroyed': 'u32',
                    'approvals_remaining': 'u32',
                    'asset_id': 'u128',
                },
                'ApprovedTransfer': {
                    'amount': 'u128',
                    'asset_id': 'u128',
                    'delegate': 'AccountId',
                    'source': 'AccountId',
                },
                'AssetFrozen': {'asset_id': 'u128'},
                'AssetMinBalanceChanged': {
                    'asset_id': 'u128',
                    'new_min_balance': 'u128',
                },
                'AssetStatusChanged': {'asset_id': 'u128'},
                'AssetThawed': {'asset_id': 'u128'},
                'Blocked': {'asset_id': 'u128', 'who': 'AccountId'},
                'Burned': {
                    'asset_id': 'u128',
                    'balance': 'u128',
                    'owner': 'AccountId',
                },
                'Created': {
                    'asset_id': 'u128',
                    'creator': 'AccountId',
                    'owner': 'AccountId',
                },
                'Destroyed': {'asset_id': 'u128'},
                'DestructionStarted': {'asset_id': 'u128'},
                'ForceCreated': {'asset_id': 'u128', 'owner': 'AccountId'},
                'Frozen': {'asset_id': 'u128', 'who': 'AccountId'},
                'Issued': {
                    'amount': 'u128',
                    'asset_id': 'u128',
                    'owner': 'AccountId',
                },
                'MetadataCleared': {'asset_id': 'u128'},
                'MetadataSet': {
                    'asset_id': 'u128',
                    'decimals': 'u8',
                    'is_frozen': 'bool',
                    'name': 'Bytes',
                    'symbol': 'Bytes',
                },
                'OwnerChanged': {'asset_id': 'u128', 'owner': 'AccountId'},
                'TeamChanged': {
                    'admin': 'AccountId',
                    'asset_id': 'u128',
                    'freezer': 'AccountId',
                    'issuer': 'AccountId',
                },
                'Thawed': {'asset_id': 'u128', 'who': 'AccountId'},
                'Touched': {
                    'asset_id': 'u128',
                    'depositor': 'AccountId',
                    'who': 'AccountId',
                },
                'Transferred': {
                    'amount': 'u128',
                    'asset_id': 'u128',
                    'from': 'AccountId',
                    'to': 'AccountId',
                },
                'TransferredApproved': {
                    'amount': 'u128',
                    'asset_id': 'u128',
                    'delegate': 'AccountId',
                    'destination': 'AccountId',
                    'owner': 'AccountId',
                },
            },
            'CalamariVesting': {
                'VestingCompleted': 'AccountId',
                'VestingScheduleUpdated': ['u64'],
                'VestingUpdated': ('AccountId', 'u128'),
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
            None: None,
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
                    'destination_status': 'scale_info::34',
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
                'CandidateAdded': ('AccountId', 'u128'),
                'CandidateRemoved': 'AccountId',
                'NewCandidacyBond': 'u128',
                'NewDesiredCandidates': 'u32',
                'NewEvictionBaseline': 'u8',
                'NewEvictionTolerance': 'u8',
                'NewInvulnerables': ['AccountId'],
            },
            'Council': {
                'Approved': {'proposal_hash': 'scale_info::12'},
                'Closed': {
                    'no': 'u32',
                    'proposal_hash': 'scale_info::12',
                    'yes': 'u32',
                },
                'Disapproved': {'proposal_hash': 'scale_info::12'},
                'Executed': {
                    'proposal_hash': 'scale_info::12',
                    'result': 'scale_info::43',
                },
                'MemberExecuted': {
                    'proposal_hash': 'scale_info::12',
                    'result': 'scale_info::43',
                },
                'Proposed': {
                    'account': 'AccountId',
                    'proposal_hash': 'scale_info::12',
                    'proposal_index': 'u32',
                    'threshold': 'u32',
                },
                'Voted': {
                    'account': 'AccountId',
                    'no': 'u32',
                    'proposal_hash': 'scale_info::12',
                    'voted': 'bool',
                    'yes': 'u32',
                },
            },
            'CouncilMembership': (
                'MemberAdded',
                'MemberRemoved',
                'MembersSwapped',
                'MembersReset',
                'KeyChanged',
                'Dummy',
            ),
            'CumulusXcm': {
                'ExecutedDownward': ('[u8; 32]', 'scale_info::65'),
                'InvalidFormat': '[u8; 32]',
                'UnsupportedVersion': '[u8; 32]',
            },
            'Democracy': {
                'Blacklisted': {'proposal_hash': 'scale_info::12'},
                'Cancelled': {'ref_index': 'u32'},
                'Delegated': {'target': 'AccountId', 'who': 'AccountId'},
                'ExternalTabled': None,
                'MetadataCleared': {
                    'hash': 'scale_info::12',
                    'owner': 'scale_info::40',
                },
                'MetadataSet': {
                    'hash': 'scale_info::12',
                    'owner': 'scale_info::40',
                },
                'MetadataTransferred': {
                    'hash': 'scale_info::12',
                    'owner': 'scale_info::40',
                    'prev_owner': 'scale_info::40',
                },
                'NotPassed': {'ref_index': 'u32'},
                'Passed': {'ref_index': 'u32'},
                'ProposalCanceled': {'prop_index': 'u32'},
                'Proposed': {'deposit': 'u128', 'proposal_index': 'u32'},
                'Seconded': {'prop_index': 'u32', 'seconder': 'AccountId'},
                'Started': {'ref_index': 'u32', 'threshold': 'scale_info::37'},
                'Tabled': {'deposit': 'u128', 'proposal_index': 'u32'},
                'Undelegated': {'account': 'AccountId'},
                'Vetoed': {
                    'proposal_hash': 'scale_info::12',
                    'until': 'u32',
                    'who': 'AccountId',
                },
                'Voted': {
                    'ref_index': 'u32',
                    'vote': 'scale_info::38',
                    'voter': 'AccountId',
                },
            },
            'DmpQueue': {
                'ExecutedDownward': {
                    'message_id': '[u8; 32]',
                    'outcome': 'scale_info::65',
                },
                'InvalidFormat': {'message_id': '[u8; 32]'},
                'MaxMessagesExhausted': {'message_id': '[u8; 32]'},
                'OverweightEnqueued': {
                    'message_id': '[u8; 32]',
                    'overweight_index': 'u64',
                    'required_weight': 'scale_info::9',
                },
                'OverweightServiced': {
                    'overweight_index': 'u64',
                    'weight_used': 'scale_info::9',
                },
                'UnsupportedVersion': {'message_id': '[u8; 32]'},
                'WeightExhausted': {
                    'message_id': '[u8; 32]',
                    'remaining_weight': 'scale_info::9',
                    'required_weight': 'scale_info::9',
                },
            },
            'Farming': {
                'AllForceGaugeClaimed': {'gid': 'u128'},
                'AllRetired': {'pid': 'u128'},
                'Charged': {'pid': 'u128', 'rewards': [('u128', 'u128')], 'who': 'AccountId'},
                'Claimed': {'pid': 'u128', 'who': 'AccountId'},
                'Deposited': {
                    'add_value': 'u128',
                    'gauge_info': (None, ('u128', 'u32')),
                    'pid': 'u128',
                    'who': 'AccountId',
                },
                'FarmingPoolClosed': {'pid': 'u128'},
                'FarmingPoolCreated': {'pid': 'u128'},
                'FarmingPoolEdited': {'pid': 'u128'},
                'FarmingPoolKilled': {'pid': 'u128'},
                'FarmingPoolReset': {'pid': 'u128'},
                'GaugeWithdrawn': {'gid': 'u128', 'who': 'AccountId'},
                'PartiallyForceGaugeClaimed': {'gid': 'u128'},
                'PartiallyRetired': {'pid': 'u128'},
                'RetireLimitSet': {'limit': 'u32'},
                'WithdrawClaimed': {'pid': 'u128', 'who': 'AccountId'},
                'Withdrawn': {
                    'pid': 'u128',
                    'remove_value': (None, 'u128'),
                    'who': 'AccountId',
                },
            },
            'Lottery': {
                'Claimed': {'account': 'AccountId', 'amount': 'u128'},
                'Deposited': {'account': 'AccountId', 'amount': 'u128'},
                'LotteryStarted': None,
                'LotteryStopped': None,
                'LotteryWinner': {'account': 'AccountId', 'amount': 'u128'},
                'ScheduledWithdraw': {
                    'account': 'AccountId',
                    'amount': 'u128',
                },
                'Withdrawn': {'account': 'AccountId', 'amount': 'u128'},
            },
            'MantaPay': {
                'PrivateTransfer': {'origin': (None, 'AccountId')},
                'ToPrivate': {
                    'asset': 'scale_info::131',
                    'source': 'AccountId',
                },
                'ToPublic': {'asset': 'scale_info::131', 'sink': 'AccountId'},
                'Transfer': {
                    'asset': 'scale_info::131',
                    'sink': 'AccountId',
                    'source': 'AccountId',
                },
            },
            'MantaSbt': {
                'AllowlistEvmAddress': {
                    'address': '[u8; 20]',
                    'asset_id': 'u128',
                    'mint_id': 'u32',
                },
                'ChangeAllowlistAccount': {'account': (None, 'AccountId')},
                'ChangeForceAccount': {'account': (None, 'AccountId')},
                'ChangeFreeReserveAccount': {'account': (None, 'AccountId')},
                'ForceMintSbtEvm': {
                    'address': '[u8; 20]',
                    'asset_id': 'u128',
                    'mint_id': 'u32',
                },
                'ForceToPrivate': {'asset': 'u128', 'source': 'AccountId'},
                'MintSbt': {'asset': 'u128', 'source': 'AccountId'},
                'MintSbtEvm': {
                    'address': '[u8; 20]',
                    'asset_id': 'u128',
                    'mint_id': 'u32',
                },
                'NewMintInfo': {
                    'end_time': (None, 'u64'),
                    'mint_id': 'u32',
                    'mint_name': 'Bytes',
                    'start_time': 'u64',
                },
                'RemoveAllowlistEvmAddress': {
                    'address': '[u8; 20]',
                    'mint_id': 'u32',
                },
                'SBTReserved': {
                    'reserve_account': 'AccountId',
                    'start_id': 'u128',
                    'stop_id': 'u128',
                    'who': 'AccountId',
                },
                'SetNextSbtId': {'asset_id': (None, 'u128')},
                'UpdateMintInfo': {
                    'end_time': (None, 'u64'),
                    'mint_id': 'u32',
                    'mint_name': 'Bytes',
                    'start_time': 'u64',
                },
            },
            'Multisig': {
                'MultisigApproval': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                    'timepoint': 'scale_info::124',
                },
                'MultisigCancelled': {
                    'call_hash': '[u8; 32]',
                    'cancelling': 'AccountId',
                    'multisig': 'AccountId',
                    'timepoint': 'scale_info::124',
                },
                'MultisigExecuted': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                    'result': 'scale_info::43',
                    'timepoint': 'scale_info::124',
                },
                'NewMultisig': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                },
            },
            'NameService': {
                'NameQueuedForRegister': {
                    'hash_owner': 'scale_info::12',
                    'hash_username': 'scale_info::12',
                },
                'NameRegistered': {'owner': '[u8; 32]', 'username': 'Bytes'},
                'NameSetAsPrimary': {'owner': '[u8; 32]', 'username': 'Bytes'},
                'RegisterCanceled': {
                    'hash_owner': 'scale_info::12',
                    'hash_username': 'scale_info::12',
                },
                'RegisterRemoved': {'owner': '[u8; 32]', 'username': 'Bytes'},
            },
            'ParachainStaking': {
                'BlocksPerRoundSet': {
                    'current_round': 'u32',
                    'first_block': 'u32',
                    'new': 'u32',
                    'new_per_round_inflation_ideal': 'u32',
                    'new_per_round_inflation_max': 'u32',
                    'new_per_round_inflation_min': 'u32',
                    'old': 'u32',
                },
                'CancelledCandidateBondLess': {
                    'amount': 'u128',
                    'candidate': 'AccountId',
                    'execute_round': 'u32',
                },
                'CancelledCandidateExit': {'candidate': 'AccountId'},
                'CancelledDelegationRequest': {
                    'cancelled_request': 'scale_info::49',
                    'collator': 'AccountId',
                    'delegator': 'AccountId',
                },
                'CandidateBackOnline': {'candidate': 'AccountId'},
                'CandidateBondLessRequested': {
                    'amount_to_decrease': 'u128',
                    'candidate': 'AccountId',
                    'execute_round': 'u32',
                },
                'CandidateBondedLess': {
                    'amount': 'u128',
                    'candidate': 'AccountId',
                    'new_bond': 'u128',
                },
                'CandidateBondedMore': {
                    'amount': 'u128',
                    'candidate': 'AccountId',
                    'new_total_bond': 'u128',
                },
                'CandidateLeft': {
                    'ex_candidate': 'AccountId',
                    'new_total_amt_locked': 'u128',
                    'unlocked_amount': 'u128',
                },
                'CandidateScheduledExit': {
                    'candidate': 'AccountId',
                    'exit_allowed_round': 'u32',
                    'scheduled_exit': 'u32',
                },
                'CandidateWentOffline': {'candidate': 'AccountId'},
                'CollatorChosen': {
                    'collator_account': 'AccountId',
                    'round': 'u32',
                    'total_exposed_amount': 'u128',
                },
                'CollatorCommissionSet': {'new': 'u32', 'old': 'u32'},
                'Delegation': {
                    'candidate': 'AccountId',
                    'delegator': 'AccountId',
                    'delegator_position': 'scale_info::51',
                    'locked_amount': 'u128',
                },
                'DelegationDecreaseScheduled': {
                    'amount_to_decrease': 'u128',
                    'candidate': 'AccountId',
                    'delegator': 'AccountId',
                    'execute_round': 'u32',
                },
                'DelegationDecreased': {
                    'amount': 'u128',
                    'candidate': 'AccountId',
                    'delegator': 'AccountId',
                    'in_top': 'bool',
                },
                'DelegationIncreased': {
                    'amount': 'u128',
                    'candidate': 'AccountId',
                    'delegator': 'AccountId',
                    'in_top': 'bool',
                },
                'DelegationKicked': {
                    'candidate': 'AccountId',
                    'delegator': 'AccountId',
                    'unstaked_amount': 'u128',
                },
                'DelegationRevocationScheduled': {
                    'candidate': 'AccountId',
                    'delegator': 'AccountId',
                    'round': 'u32',
                    'scheduled_exit': 'u32',
                },
                'DelegationRevoked': {
                    'candidate': 'AccountId',
                    'delegator': 'AccountId',
                    'unstaked_amount': 'u128',
                },
                'DelegatorExitCancelled': {'delegator': 'AccountId'},
                'DelegatorExitScheduled': {
                    'delegator': 'AccountId',
                    'round': 'u32',
                    'scheduled_exit': 'u32',
                },
                'DelegatorLeft': {
                    'delegator': 'AccountId',
                    'unstaked_amount': 'u128',
                },
                'DelegatorLeftCandidate': {
                    'candidate': 'AccountId',
                    'delegator': 'AccountId',
                    'total_candidate_staked': 'u128',
                    'unstaked_amount': 'u128',
                },
                'InflationSet': {
                    'annual_ideal': 'u32',
                    'annual_max': 'u32',
                    'annual_min': 'u32',
                    'round_ideal': 'u32',
                    'round_max': 'u32',
                    'round_min': 'u32',
                },
                'JoinedCollatorCandidates': {
                    'account': 'AccountId',
                    'amount_locked': 'u128',
                    'new_total_amt_locked': 'u128',
                },
                'NewRound': {
                    'round': 'u32',
                    'selected_collators_number': 'u32',
                    'starting_block': 'u32',
                    'total_balance': 'u128',
                },
                'ParachainBondAccountSet': {
                    'new': 'AccountId',
                    'old': 'AccountId',
                },
                'ParachainBondReservePercentSet': {'new': 'u8', 'old': 'u8'},
                'ReservedForParachainBond': {
                    'account': 'AccountId',
                    'value': 'u128',
                },
                'Rewarded': {'account': 'AccountId', 'rewards': 'u128'},
                'StakeExpectationsSet': {
                    'expect_ideal': 'u128',
                    'expect_max': 'u128',
                    'expect_min': 'u128',
                },
                'TotalSelectedSet': {'new': 'u32', 'old': 'u32'},
            },
            'PolkadotXcm': {
                'AssetsClaimed': (
                    'scale_info::12',
                    'scale_info::66',
                    'scale_info::104',
                ),
                'AssetsTrapped': (
                    'scale_info::12',
                    'scale_info::66',
                    'scale_info::104',
                ),
                'Attempted': {
                    'Complete': 'scale_info::9',
                    'Error': 'scale_info::62',
                    'Incomplete': ('scale_info::9', 'scale_info::62'),
                },
                'FeesPaid': ('scale_info::66', ['scale_info::81']),
                'InvalidQuerier': (
                    'scale_info::66',
                    'u64',
                    'scale_info::66',
                    (None, 'scale_info::66'),
                ),
                'InvalidQuerierVersion': ('scale_info::66', 'u64'),
                'InvalidResponder': (
                    'scale_info::66',
                    'u64',
                    (None, 'scale_info::66'),
                ),
                'InvalidResponderVersion': ('scale_info::66', 'u64'),
                'Notified': ('u64', 'u8', 'u8'),
                'NotifyDecodeFailed': ('u64', 'u8', 'u8'),
                'NotifyDispatchError': ('u64', 'u8', 'u8'),
                'NotifyOverweight': (
                    'u64',
                    'u8',
                    'u8',
                    'scale_info::9',
                    'scale_info::9',
                ),
                'NotifyTargetMigrationFail': ('scale_info::118', 'u64'),
                'NotifyTargetSendFail': (
                    'scale_info::66',
                    'u64',
                    'scale_info::62',
                ),
                'ResponseReady': ('u64', 'scale_info::87'),
                'ResponseTaken': 'u64',
                'Sent': (
                    'scale_info::66',
                    'scale_info::66',
                    ['scale_info::78'],
                ),
                'SupportedVersionChanged': ('scale_info::66', 'u32'),
                'UnexpectedResponse': ('scale_info::66', 'u64'),
                'VersionChangeNotified': (
                    'scale_info::66',
                    'u32',
                    ['scale_info::81'],
                ),
                'VersionNotifyRequested': (
                    'scale_info::66',
                    ['scale_info::81'],
                ),
                'VersionNotifyStarted': ('scale_info::66', ['scale_info::81']),
                'VersionNotifyUnrequested': (
                    'scale_info::66',
                    ['scale_info::81'],
                ),
            },
            'Preimage': {
                'Cleared': {'hash': 'scale_info::12'},
                'Noted': {'hash': 'scale_info::12'},
                'Requested': {'hash': 'scale_info::12'},
            },
            'Scheduler': {
                'CallUnavailable': {
                    'id': (None, '[u8; 32]'),
                    'task': ('u32', 'u32'),
                },
                'Canceled': {'index': 'u32', 'when': 'u32'},
                'Dispatched': {
                    'id': (None, '[u8; 32]'),
                    'result': 'scale_info::43',
                    'task': ('u32', 'u32'),
                },
                'PeriodicFailed': {
                    'id': (None, '[u8; 32]'),
                    'task': ('u32', 'u32'),
                },
                'PermanentlyOverweight': {
                    'id': (None, '[u8; 32]'),
                    'task': ('u32', 'u32'),
                },
                'Scheduled': {'index': 'u32', 'when': 'u32'},
            },
            'Session': {'NewSession': {'session_index': 'u32'}},
            'TechnicalCommittee': {
                'Approved': {'proposal_hash': 'scale_info::12'},
                'Closed': {
                    'no': 'u32',
                    'proposal_hash': 'scale_info::12',
                    'yes': 'u32',
                },
                'Disapproved': {'proposal_hash': 'scale_info::12'},
                'Executed': {
                    'proposal_hash': 'scale_info::12',
                    'result': 'scale_info::43',
                },
                'MemberExecuted': {
                    'proposal_hash': 'scale_info::12',
                    'result': 'scale_info::43',
                },
                'Proposed': {
                    'account': 'AccountId',
                    'proposal_hash': 'scale_info::12',
                    'proposal_index': 'u32',
                    'threshold': 'u32',
                },
                'Voted': {
                    'account': 'AccountId',
                    'no': 'u32',
                    'proposal_hash': 'scale_info::12',
                    'voted': 'bool',
                    'yes': 'u32',
                },
            },
            'TechnicalMembership': (
                'MemberAdded',
                'MemberRemoved',
                'MembersSwapped',
                'MembersReset',
                'KeyChanged',
                'Dummy',
            ),
            'TransactionPause': {
                'PalletPaused': 'Bytes',
                'PalletUnpaused': 'Bytes',
                'TransactionPaused': ('Bytes', 'Bytes'),
                'TransactionUnpaused': ('Bytes', 'Bytes'),
            },
            'TransactionPayment': {
                'TransactionFeePaid': {
                    'actual_fee': 'u128',
                    'tip': 'u128',
                    'who': 'AccountId',
                },
            },
            'Treasury': {
                'Awarded': {
                    'account': 'AccountId',
                    'award': 'u128',
                    'proposal_index': 'u32',
                },
                'Burnt': {'burnt_funds': 'u128'},
                'Deposit': {'value': 'u128'},
                'Proposed': {'proposal_index': 'u32'},
                'Rejected': {'proposal_index': 'u32', 'slashed': 'u128'},
                'Rollover': {'rollover_balance': 'u128'},
                'SpendApproved': {
                    'amount': 'u128',
                    'beneficiary': 'AccountId',
                    'proposal_index': 'u32',
                },
                'Spending': {'budget_remaining': 'u128'},
                'UpdatedInactive': {
                    'deactivated': 'u128',
                    'reactivated': 'u128',
                },
            },
            'Utility': {
                'BatchCompleted': None,
                'BatchCompletedWithErrors': None,
                'BatchInterrupted': {
                    'error': 'scale_info::25',
                    'index': 'u32',
                },
                'DispatchedAs': {'result': 'scale_info::43'},
                'ItemCompleted': None,
                'ItemFailed': {'error': 'scale_info::25'},
            },
            'XTokens': {
                'TransferredMultiAssets': {
                    'assets': ['scale_info::81'],
                    'dest': 'scale_info::66',
                    'fee': 'scale_info::81',
                    'sender': 'AccountId',
                },
            },
            'XcmpQueue': {
                'BadFormat': {'message_hash': (None, '[u8; 32]')},
                'BadVersion': {'message_hash': (None, '[u8; 32]')},
                'Fail': {
                    'error': 'scale_info::62',
                    'message_hash': (None, '[u8; 32]'),
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
                'Success': {'message_hash': (None, '[u8; 32]'), 'weight': 'scale_info::9'},
                'XcmpMessageSent': {'message_hash': (None, '[u8; 32]')},
            },
            'ZenlinkProtocol': {
                'AssetSwap': (
                    'AccountId',
                    'AccountId',
                    ['scale_info::142'],
                    ['u128'],
                ),
                'BootstrapClaim': (
                    'AccountId',
                    'AccountId',
                    'AccountId',
                    'scale_info::142',
                    'scale_info::142',
                    'u128',
                    'u128',
                    'u128',
                ),
                'BootstrapContribute': (
                    'AccountId',
                    'scale_info::142',
                    'u128',
                    'scale_info::142',
                    'u128',
                ),
                'BootstrapCreated': (
                    'AccountId',
                    'scale_info::142',
                    'scale_info::142',
                    'u128',
                    'u128',
                    'u128',
                    'u128',
                    'u32',
                ),
                'BootstrapEnd': (
                    'scale_info::142',
                    'scale_info::142',
                    'u128',
                    'u128',
                    'u128',
                ),
                'BootstrapRefund': (
                    'AccountId',
                    'AccountId',
                    'scale_info::142',
                    'scale_info::142',
                    'u128',
                    'u128',
                ),
                'BootstrapUpdate': (
                    'AccountId',
                    'scale_info::142',
                    'scale_info::142',
                    'u128',
                    'u128',
                    'u128',
                    'u128',
                    'u32',
                ),
                'Burned': ('scale_info::142', 'AccountId', 'u128'),
                'ChargeReward': (
                    'scale_info::142',
                    'scale_info::142',
                    'AccountId',
                    [('scale_info::142', 'u128')],
                ),
                'DistributeReward': (
                    'scale_info::142',
                    'scale_info::142',
                    'AccountId',
                    [('scale_info::142', 'u128')],
                ),
                'LiquidityAdded': (
                    'AccountId',
                    'scale_info::142',
                    'scale_info::142',
                    'u128',
                    'u128',
                    'u128',
                ),
                'LiquidityRemoved': (
                    'AccountId',
                    'AccountId',
                    'scale_info::142',
                    'scale_info::142',
                    'u128',
                    'u128',
                    'u128',
                ),
                'Minted': ('scale_info::142', 'AccountId', 'u128'),
                'PairCreated': ('scale_info::142', 'scale_info::142'),
                'Transferred': (
                    'scale_info::142',
                    'AccountId',
                    'AccountId',
                    'u128',
                ),
                'TransferredToParachain': (
                    'scale_info::142',
                    'AccountId',
                    'u32',
                    'AccountId',
                    'u128',
                    'u64',
                ),
                'WithdrawReward': (
                    'scale_info::142',
                    'scale_info::142',
                    'AccountId',
                ),
            },
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
2400
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
{'max': {'mandatory': 5242880, 'normal': 3670016, 'operational': 5242880}}
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
    'base_block': {'proof_size': 0, 'ref_time': 5346284000},
    'max_block': {'proof_size': 5242880, 'ref_time': 500000000000},
    'per_class': {
        'mandatory': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 98974000},
            'max_extrinsic': None,
            'max_total': None,
            'reserved': None,
        },
        'normal': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 98974000},
            'max_extrinsic': {'proof_size': 3145728, 'ref_time': 299901026000},
            'max_total': {'proof_size': 3670016, 'ref_time': 350000000000},
            'reserved': {'proof_size': 0, 'ref_time': 0},
        },
        'operational': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 98974000},
            'max_extrinsic': {'proof_size': 4718592, 'ref_time': 449901026000},
            'max_total': {'proof_size': 5242880, 'ref_time': 500000000000},
            'reserved': {'proof_size': 1572864, 'ref_time': 150000000000},
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
78
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
        ('0x43285cafec063af9', 1),
        ('0xea93e3f16f3d6962', 2),
        ('0x853dcae7bb59d2e2', 1),
        ('0xddcc9d428f980d4f', 1),
        ('0x2aa62120049dd2d2', 1),
        ('0x60aed43cb52456f1', 1),
        ('0x0d94b80c178630f0', 1),
    ],
    'authoring_version': 2,
    'impl_name': 'calamari',
    'impl_version': 1,
    'spec_name': 'calamari',
    'spec_version': 4610,
    'state_version': 0,
    'transaction_version': 18,
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