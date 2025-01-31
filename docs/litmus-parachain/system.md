
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

\# &lt;weight&gt;
- `O(1)`
\# &lt;/weight&gt;
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

\# &lt;weight&gt;
- `O(C + S)` where `C` length of `code` and `S` complexity of `can_set_code`
- 1 call to `can_set_code`: `O(S)` (calls `sp_io::misc::runtime_version` which is
  expensive).
- 1 storage write (codec `O(C)`).
- 1 digest item.
- 1 event.
The weight of this function is dependent on the runtime, but generally this is very
expensive. We will treat this as a full block.
\# &lt;/weight&gt;
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

\# &lt;weight&gt;
- `O(C)` where `C` length of `code`
- 1 storage write (codec `O(C)`).
- 1 digest item.
- 1 event.
The weight of this function is dependent on the runtime. We will treat this as a full
block. \# &lt;/weight&gt;
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
| dispatch_error | `DispatchError` | ```{'Other': None, 'CannotLookup': None, 'BadOrigin': None, 'Module': {'index': 'u8', 'error': '[u8; 4]'}, 'ConsumerRemaining': None, 'NoProviders': None, 'TooManyConsumers': None, 'Token': ('NoFunds', 'WouldDie', 'BelowMinimum', 'CannotCreate', 'UnknownAsset', 'Frozen', 'Unsupported'), 'Arithmetic': ('Underflow', 'Overflow', 'DivisionByZero'), 'Transactional': ('LimitReached', 'NoLayer'), 'Exhausted': None, 'Corruption': None, 'Unavailable': None}```
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
| hash | `T::Hash` | ```scale_info::11```

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
        'fee_frozen': 'u128',
        'free': 'u128',
        'misc_frozen': 'u128',
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
'scale_info::11'
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
            'Other': 'Bytes',
            None: None,
            'Consensus': ('[u8; 4]', 'Bytes'),
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
    'System', 'EventTopics', ['scale_info::11']
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
                'ForeignAssetMetadataUpdated': {
                    'asset_id': 'u128',
                    'metadata': 'scale_info::119',
                },
                'ForeignAssetTrackerUpdated': {
                    'new_asset_tracker': 'u128',
                    'old_asset_tracker': 'u128',
                },
                'ForeignAssetTypeRegistered': {
                    'asset_id': 'u128',
                    'asset_type': 'scale_info::120',
                },
                'ForeignAssetTypeRemoved': {
                    'asset_id': 'u128',
                    'default_asset_type': 'scale_info::120',
                    'removed_asset_type': 'scale_info::120',
                },
                'UnitsPerSecondChanged': {
                    'asset_id': 'u128',
                    'units_per_second': 'u128',
                },
            },
            'Balances': {
                'BalanceSet': {
                    'free': 'u128',
                    'reserved': 'u128',
                    'who': 'AccountId',
                },
                'Deposit': {'amount': 'u128', 'who': 'AccountId'},
                'DustLost': {'account': 'AccountId', 'amount': 'u128'},
                'Endowed': {'account': 'AccountId', 'free_balance': 'u128'},
                'ReserveRepatriated': {
                    'amount': 'u128',
                    'destination_status': 'scale_info::42',
                    'from': 'AccountId',
                    'to': 'AccountId',
                },
                'Reserved': {'amount': 'u128', 'who': 'AccountId'},
                'Slashed': {'amount': 'u128', 'who': 'AccountId'},
                'Transfer': {
                    'amount': 'u128',
                    'from': 'AccountId',
                    'to': 'AccountId',
                },
                'Unreserved': {'amount': 'u128', 'who': 'AccountId'},
                'Withdraw': {'amount': 'u128', 'who': 'AccountId'},
            },
            'ChainBridge': {
                'ChainWhitelisted': 'u8',
                'FeeUpdated': {'dest_id': 'u8', 'fee': 'u128'},
                'FungibleTransfer': ('u8', 'u64', '[u8; 32]', 'u128', 'Bytes'),
                'GenericTransfer': ('u8', 'u64', '[u8; 32]', 'Bytes'),
                'NonFungibleTransfer': (
                    'u8',
                    'u64',
                    '[u8; 32]',
                    'Bytes',
                    'Bytes',
                    'Bytes',
                ),
                'ProposalApproved': ('u8', 'u64'),
                'ProposalFailed': ('u8', 'u64'),
                'ProposalRejected': ('u8', 'u64'),
                'ProposalSucceeded': ('u8', 'u64'),
                'RelayerAdded': 'AccountId',
                'RelayerRemoved': 'AccountId',
                'RelayerThresholdChanged': 'u32',
                'VoteAgainst': ('u8', 'u64', 'AccountId'),
                'VoteFor': ('u8', 'u64', 'AccountId'),
            },
            'Council': {
                'Approved': {'proposal_hash': 'scale_info::11'},
                'Closed': {
                    'no': 'u32',
                    'proposal_hash': 'scale_info::11',
                    'yes': 'u32',
                },
                'Disapproved': {'proposal_hash': 'scale_info::11'},
                'Executed': {
                    'proposal_hash': 'scale_info::11',
                    'result': 'scale_info::32',
                },
                'MemberExecuted': {
                    'proposal_hash': 'scale_info::11',
                    'result': 'scale_info::32',
                },
                'Proposed': {
                    'account': 'AccountId',
                    'proposal_hash': 'scale_info::11',
                    'proposal_index': 'u32',
                    'threshold': 'u32',
                },
                'Voted': {
                    'account': 'AccountId',
                    'no': 'u32',
                    'proposal_hash': 'scale_info::11',
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
            'Multisig': {
                'MultisigApproval': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                    'timepoint': 'scale_info::36',
                },
                'MultisigCancelled': {
                    'call_hash': '[u8; 32]',
                    'cancelling': 'AccountId',
                    'multisig': 'AccountId',
                    'timepoint': 'scale_info::36',
                },
                'MultisigExecuted': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                    'result': 'scale_info::32',
                    'timepoint': 'scale_info::36',
                },
                'NewMultisig': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                },
            },
            None: None,
            'Bounties': {
                'BountyAwarded': {'beneficiary': 'AccountId', 'index': 'u32'},
                'BountyBecameActive': {'index': 'u32'},
                'BountyCanceled': {'index': 'u32'},
                'BountyClaimed': {
                    'beneficiary': 'AccountId',
                    'index': 'u32',
                    'payout': 'u128',
                },
                'BountyExtended': {'index': 'u32'},
                'BountyProposed': {'index': 'u32'},
                'BountyRejected': {'bond': 'u128', 'index': 'u32'},
            },
            'BridgeTransfer': {'MaximumIssuanceChanged': {'old_value': 'u128'}},
            'CollatorSelection': {
                'CandidateAdded': {
                    'account_id': 'AccountId',
                    'deposit': 'u128',
                },
                'CandidateRemoved': {'account_id': 'AccountId'},
                'NewCandidacyBond': {'bond_amount': 'u128'},
                'NewDesiredCandidates': {'desired_candidates': 'u32'},
                'NewInvulnerables': {'invulnerables': ['AccountId']},
            },
            'CumulusXcm': {
                'ExecutedDownward': ('[u8; 8]', 'scale_info::65'),
                'InvalidFormat': '[u8; 8]',
                'UnsupportedVersion': '[u8; 8]',
            },
            'Democracy': {
                'Blacklisted': {'proposal_hash': 'scale_info::11'},
                'Cancelled': {'ref_index': 'u32'},
                'Delegated': {'target': 'AccountId', 'who': 'AccountId'},
                'ExternalTabled': None,
                'NotPassed': {'ref_index': 'u32'},
                'Passed': {'ref_index': 'u32'},
                'ProposalCanceled': {'prop_index': 'u32'},
                'Proposed': {'deposit': 'u128', 'proposal_index': 'u32'},
                'Seconded': {'prop_index': 'u32', 'seconder': 'AccountId'},
                'Started': {'ref_index': 'u32', 'threshold': 'scale_info::47'},
                'Tabled': {'deposit': 'u128', 'proposal_index': 'u32'},
                'Undelegated': {'account': 'AccountId'},
                'Vetoed': {
                    'proposal_hash': 'scale_info::11',
                    'until': 'u32',
                    'who': 'AccountId',
                },
                'Voted': {
                    'ref_index': 'u32',
                    'vote': 'scale_info::48',
                    'voter': 'AccountId',
                },
            },
            'DmpQueue': {
                'ExecutedDownward': {
                    'message_id': '[u8; 32]',
                    'outcome': 'scale_info::65',
                },
                'InvalidFormat': {'message_id': '[u8; 32]'},
                'OverweightEnqueued': {
                    'message_id': '[u8; 32]',
                    'overweight_index': 'u64',
                    'required_weight': 'scale_info::8',
                },
                'OverweightServiced': {
                    'overweight_index': 'u64',
                    'weight_used': 'scale_info::8',
                },
                'UnsupportedVersion': {'message_id': '[u8; 32]'},
                'WeightExhausted': {
                    'message_id': '[u8; 32]',
                    'remaining_weight': 'scale_info::8',
                    'required_weight': 'scale_info::8',
                },
            },
            'Drop3': {
                'AdminChanged': {'old_admin': (None, 'AccountId')},
                'BalanceSlashed': {'amount': 'u128', 'who': 'AccountId'},
                'RewardPoolApproved': {'id': 'u64'},
                'RewardPoolProposed': {
                    'id': 'u64',
                    'name': 'Bytes',
                    'owner': 'AccountId',
                },
                'RewardPoolRejected': {'id': 'u64'},
                'RewardPoolRemoved': {
                    'id': 'u64',
                    'name': 'Bytes',
                    'owner': 'AccountId',
                },
                'RewardPoolStarted': {'id': 'u64'},
                'RewardPoolStopped': {'id': 'u64'},
                'RewardSent': {'amount': 'u128', 'to': 'AccountId'},
            },
            'ExtrinsicFilter': {
                'ExtrinsicsBlocked': {
                    'function_name_bytes': (None, 'Bytes'),
                    'pallet_name_bytes': 'Bytes',
                },
                'ExtrinsicsUnblocked': {
                    'function_name_bytes': (None, 'Bytes'),
                    'pallet_name_bytes': 'Bytes',
                },
                'ModeSet': {'new_mode': 'scale_info::112'},
            },
            'IdentityManagement': {
                'CreateIdentityHandlingFailed': None,
                'CreateIdentityRequested': {'shard': 'scale_info::11'},
                'DecodeHexFailed': {'reason': 'Bytes'},
                'DelegateeAdded': {'account': 'AccountId'},
                'DelegateeRemoved': {'account': 'AccountId'},
                'HttpRequestFailed': {'reason': 'Bytes'},
                'IdentityCreated': {
                    'account': 'AccountId',
                    'code': 'scale_info::115',
                    'id_graph': 'scale_info::115',
                    'identity': 'scale_info::115',
                },
                'IdentityRemoved': {
                    'account': 'AccountId',
                    'id_graph': 'scale_info::115',
                    'identity': 'scale_info::115',
                },
                'IdentityVerified': {
                    'account': 'AccountId',
                    'id_graph': 'scale_info::115',
                    'identity': 'scale_info::115',
                },
                'InvalidIdentity': None,
                'RecoverEvmAddressFailed': None,
                'RecoverSubstratePubkeyFailed': None,
                'RemoveIdentityHandlingFailed': None,
                'RemoveIdentityRequested': {'shard': 'scale_info::11'},
                'SetUserShieldingKeyHandlingFailed': None,
                'SetUserShieldingKeyRequested': {'shard': 'scale_info::11'},
                'UnexpectedMessage': None,
                'UserShieldingKeySet': {'account': 'AccountId'},
                'VerifyEvmSignatureFailed': None,
                'VerifyIdentityHandlingFailed': None,
                'VerifyIdentityRequested': {'shard': 'scale_info::11'},
                'VerifySubstrateSignatureFailed': None,
                'WrongIdentityHandleType': None,
                'WrongSignatureType': None,
                'WrongWeb2Handle': None,
            },
            'IdentityManagementMock': {
                'CreateIdentityRequested': {'shard': 'scale_info::11'},
                'DelegateeAdded': {'account': 'AccountId'},
                'DelegateeRemoved': {'account': 'AccountId'},
                'IdentityCreated': {
                    'account': 'AccountId',
                    'code': 'scale_info::115',
                    'id_graph': 'scale_info::115',
                    'identity': 'scale_info::115',
                },
                'IdentityCreatedPlain': {
                    'account': 'AccountId',
                    'code': '[u8; 16]',
                    'id_graph': [('scale_info::140', 'scale_info::148')],
                    'identity': 'scale_info::140',
                },
                'IdentityRemoved': {
                    'account': 'AccountId',
                    'id_graph': 'scale_info::115',
                    'identity': 'scale_info::115',
                },
                'IdentityRemovedPlain': {
                    'account': 'AccountId',
                    'id_graph': [('scale_info::140', 'scale_info::148')],
                    'identity': 'scale_info::140',
                },
                'IdentityVerified': {
                    'account': 'AccountId',
                    'id_graph': 'scale_info::115',
                    'identity': 'scale_info::115',
                },
                'IdentityVerifiedPlain': {
                    'account': 'AccountId',
                    'id_graph': [('scale_info::140', 'scale_info::148')],
                    'identity': 'scale_info::140',
                },
                'RemoveIdentityRequested': {'shard': 'scale_info::11'},
                'SetUserShieldingKeyRequested': {'shard': 'scale_info::11'},
                'SomeError': {'error': 'Bytes', 'func': 'Bytes'},
                'UserShieldingKeySet': {'account': 'AccountId'},
                'UserShieldingKeySetPlain': {'account': 'AccountId'},
                'VerifyIdentityRequested': {'shard': 'scale_info::11'},
            },
            'ParachainSystem': {
                'DownwardMessagesProcessed': {
                    'dmq_head': 'scale_info::11',
                    'weight_used': 'scale_info::8',
                },
                'DownwardMessagesReceived': {'count': 'u32'},
                'UpgradeAuthorized': {'code_hash': 'scale_info::11'},
                'ValidationFunctionApplied': {'relay_chain_block_num': 'u32'},
                'ValidationFunctionDiscarded': None,
                'ValidationFunctionStored': None,
            },
            'PolkadotXcm': {
                'AssetsClaimed': (
                    'scale_info::11',
                    'scale_info::66',
                    'scale_info::97',
                ),
                'AssetsTrapped': (
                    'scale_info::11',
                    'scale_info::66',
                    'scale_info::97',
                ),
                'Attempted': {
                    'Complete': 'u64',
                    'Error': 'scale_info::62',
                    'Incomplete': ('u64', 'scale_info::62'),
                },
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
                    'scale_info::8',
                    'scale_info::8',
                ),
                'NotifyTargetMigrationFail': ('scale_info::102', 'u64'),
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
                'VersionChangeNotified': ('scale_info::66', 'u32'),
            },
            'Preimage': {
                'Cleared': {'hash': 'scale_info::11'},
                'Noted': {'hash': 'scale_info::11'},
                'Requested': {'hash': 'scale_info::11'},
            },
            'Proxy': {
                'Announced': {
                    'call_hash': 'scale_info::11',
                    'proxy': 'AccountId',
                    'real': 'AccountId',
                },
                'ProxyAdded': {
                    'delay': 'u32',
                    'delegatee': 'AccountId',
                    'delegator': 'AccountId',
                    'proxy_type': 'scale_info::38',
                },
                'ProxyExecuted': {'result': 'scale_info::32'},
                'ProxyRemoved': {
                    'delay': 'u32',
                    'delegatee': 'AccountId',
                    'delegator': 'AccountId',
                    'proxy_type': 'scale_info::38',
                },
                'PureCreated': {
                    'disambiguation_index': 'u16',
                    'proxy_type': 'scale_info::38',
                    'pure': 'AccountId',
                    'who': 'AccountId',
                },
            },
            'Scheduler': {
                'CallUnavailable': {
                    'id': (None, '[u8; 32]'),
                    'task': ('u32', 'u32'),
                },
                'Canceled': {'index': 'u32', 'when': 'u32'},
                'Dispatched': {
                    'id': (None, '[u8; 32]'),
                    'result': 'scale_info::32',
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
            'Sidechain': {
                'FinalizedSidechainBlock': ('AccountId', 'scale_info::11'),
                'ProposedSidechainBlock': ('AccountId', 'scale_info::11'),
            },
            'System': {
                'CodeUpdated': None,
                'ExtrinsicFailed': {
                    'dispatch_error': 'scale_info::24',
                    'dispatch_info': 'scale_info::21',
                },
                'ExtrinsicSuccess': {'dispatch_info': 'scale_info::21'},
                'KilledAccount': {'account': 'AccountId'},
                'NewAccount': {'account': 'AccountId'},
                'Remarked': {'hash': 'scale_info::11', 'sender': 'AccountId'},
            },
            'TechnicalCommittee': {
                'Approved': {'proposal_hash': 'scale_info::11'},
                'Closed': {
                    'no': 'u32',
                    'proposal_hash': 'scale_info::11',
                    'yes': 'u32',
                },
                'Disapproved': {'proposal_hash': 'scale_info::11'},
                'Executed': {
                    'proposal_hash': 'scale_info::11',
                    'result': 'scale_info::32',
                },
                'MemberExecuted': {
                    'proposal_hash': 'scale_info::11',
                    'result': 'scale_info::32',
                },
                'Proposed': {
                    'account': 'AccountId',
                    'proposal_hash': 'scale_info::11',
                    'proposal_index': 'u32',
                    'threshold': 'u32',
                },
                'Voted': {
                    'account': 'AccountId',
                    'no': 'u32',
                    'proposal_hash': 'scale_info::11',
                    'voted': 'bool',
                    'yes': 'u32',
                },
            },
            'TechnicalCommitteeMembership': (
                'MemberAdded',
                'MemberRemoved',
                'MembersSwapped',
                'MembersReset',
                'KeyChanged',
                'Dummy',
            ),
            'Teeracle': {
                'AddedToWhitelist': ('Bytes', '[u8; 32]'),
                'ExchangeRateDeleted': ('Bytes', 'Bytes'),
                'ExchangeRateUpdated': (
                    'Bytes',
                    'Bytes',
                    (None, 'scale_info::129'),
                ),
                'OracleUpdated': ('Bytes', 'Bytes'),
                'RemovedFromWhitelist': ('Bytes', '[u8; 32]'),
            },
            'Teerex': {
                'AddedEnclave': ('AccountId', 'Bytes'),
                'Forwarded': 'scale_info::11',
                'ProcessedParentchainBlock': (
                    'AccountId',
                    'scale_info::11',
                    'scale_info::11',
                    'u32',
                ),
                'PublishedHash': {
                    'data': 'Bytes',
                    'hash': 'scale_info::11',
                    'mr_enclave': '[u8; 32]',
                },
                'RemovedEnclave': 'AccountId',
                'RemovedScheduledEnclave': 'u32',
                'SetHeartbeatTimeout': 'u64',
                'ShieldFunds': 'Bytes',
                'UnshieldedFunds': 'AccountId',
                'UpdatedScheduledEnclave': ('u32', '[u8; 32]'),
            },
            'Tokens': {
                'BalanceSet': {
                    'currency_id': 'u128',
                    'free': 'u128',
                    'reserved': 'u128',
                    'who': 'AccountId',
                },
                'Deposited': {
                    'amount': 'u128',
                    'currency_id': 'u128',
                    'who': 'AccountId',
                },
                'DustLost': {
                    'amount': 'u128',
                    'currency_id': 'u128',
                    'who': 'AccountId',
                },
                'Endowed': {
                    'amount': 'u128',
                    'currency_id': 'u128',
                    'who': 'AccountId',
                },
                'LockRemoved': {
                    'currency_id': 'u128',
                    'lock_id': '[u8; 8]',
                    'who': 'AccountId',
                },
                'LockSet': {
                    'amount': 'u128',
                    'currency_id': 'u128',
                    'lock_id': '[u8; 8]',
                    'who': 'AccountId',
                },
                'ReserveRepatriated': {
                    'amount': 'u128',
                    'currency_id': 'u128',
                    'from': 'AccountId',
                    'status': 'scale_info::42',
                    'to': 'AccountId',
                },
                'Reserved': {
                    'amount': 'u128',
                    'currency_id': 'u128',
                    'who': 'AccountId',
                },
                'Slashed': {
                    'currency_id': 'u128',
                    'free_amount': 'u128',
                    'reserved_amount': 'u128',
                    'who': 'AccountId',
                },
                'TotalIssuanceSet': {'amount': 'u128', 'currency_id': 'u128'},
                'Transfer': {
                    'amount': 'u128',
                    'currency_id': 'u128',
                    'from': 'AccountId',
                    'to': 'AccountId',
                },
                'Unreserved': {
                    'amount': 'u128',
                    'currency_id': 'u128',
                    'who': 'AccountId',
                },
                'Withdrawn': {
                    'amount': 'u128',
                    'currency_id': 'u128',
                    'who': 'AccountId',
                },
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
                    'error': 'scale_info::24',
                    'index': 'u32',
                },
                'DispatchedAs': {'result': 'scale_info::32'},
                'ItemCompleted': None,
                'ItemFailed': {'error': 'scale_info::24'},
            },
            'VCManagement': {
                'Assertion10Failed': None,
                'Assertion11Failed': None,
                'Assertion1Failed': None,
                'Assertion2Failed': None,
                'Assertion3Failed': None,
                'Assertion4Failed': None,
                'Assertion5Failed': None,
                'Assertion6Failed': None,
                'Assertion7Failed': None,
                'Assertion8Failed': None,
                'HttpRequestFailed': {'reason': 'Bytes'},
                'ParseError': None,
                'RequestVCHandlingFailed': None,
                'SchemaActivated': {
                    'account': 'AccountId',
                    'index': 'u64',
                    'shard': 'scale_info::11',
                },
                'SchemaAdminChanged': {
                    'new_admin': (None, 'AccountId'),
                    'old_admin': (None, 'AccountId'),
                },
                'SchemaDisabled': {
                    'account': 'AccountId',
                    'index': 'u64',
                    'shard': 'scale_info::11',
                },
                'SchemaIssued': {
                    'account': 'AccountId',
                    'index': 'u64',
                    'shard': 'scale_info::11',
                },
                'SchemaRevoked': {
                    'account': 'AccountId',
                    'index': 'u64',
                    'shard': 'scale_info::11',
                },
                'VCDisabled': {'index': 'scale_info::11'},
                'VCIssued': {
                    'account': 'AccountId',
                    'index': 'scale_info::11',
                    'vc': 'scale_info::115',
                },
                'VCNotExist': {'index': 'scale_info::11'},
                'VCRequested': {
                    'assertion': 'scale_info::123',
                    'shard': 'scale_info::11',
                },
                'VCRevoked': {'index': 'scale_info::11'},
            },
            'Vesting': {
                'VestingCompleted': {'account': 'AccountId'},
                'VestingUpdated': {'account': 'AccountId', 'unvested': 'u128'},
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
                'BadFormat': {'message_hash': (None, 'scale_info::11')},
                'BadVersion': {'message_hash': (None, 'scale_info::11')},
                'Fail': {
                    'error': 'scale_info::62',
                    'message_hash': (None, 'scale_info::11'),
                    'weight': 'scale_info::8',
                },
                'OverweightEnqueued': {
                    'index': 'u64',
                    'required': 'scale_info::8',
                    'sender': 'u32',
                    'sent_at': 'u32',
                },
                'OverweightServiced': {
                    'index': 'u64',
                    'used': 'scale_info::8',
                },
                'Success': {'message_hash': (None, 'scale_info::11'), 'weight': 'scale_info::8'},
                'UpwardMessageSent': {'message_hash': (None, 'scale_info::11')},
                'XcmpMessageSent': {'message_hash': (None, 'scale_info::11')},
            },
        },
        'phase': {
            'ApplyExtrinsic': 'u32',
            'Finalization': None,
            'Initialization': None,
        },
        'topics': ['scale_info::11'],
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
'scale_info::11'
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
250
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
    'base_block': {'proof_size': 0, 'ref_time': 358523000},
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
            'max_extrinsic': {'proof_size': 3407872, 'ref_time': 324901026000},
            'max_total': {'proof_size': 3932160, 'ref_time': 375000000000},
            'reserved': {'proof_size': 0, 'ref_time': 0},
        },
        'operational': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 98974000},
            'max_extrinsic': {'proof_size': 4718592, 'ref_time': 449901026000},
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
131
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
        ('0xdf6acb689907609b', 4),
        ('0x37e397fc7c91f5e4', 1),
        ('0x40fe3ad401f8959a', 6),
        ('0xd2bc9897eed08f15', 3),
        ('0xf78b278be53f454c', 2),
        ('0xab3c0572291feb8b', 1),
        ('0xdd718d5cc53262d4', 1),
        ('0xbc9d89904f5b923f', 1),
        ('0x37c8bb1350a9a2a8', 2),
        ('0xea93e3f16f3d6962', 2),
    ],
    'authoring_version': 1,
    'impl_name': 'litmus-parachain',
    'impl_version': 0,
    'spec_name': 'litmus-parachain',
    'spec_version': 9151,
    'state_version': 0,
    'transaction_version': 1,
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