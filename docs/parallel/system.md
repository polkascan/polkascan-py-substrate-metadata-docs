
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
| hash | `T::Hash` | ```[u8; 32]```

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
'[u8; 32]'
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
    'System', 'EventTopics', ['[u8; 32]']
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
            'AMM': {
                'LiquidityAdded': (
                    'AccountId',
                    'u32',
                    'u32',
                    'u128',
                    'u128',
                    'u32',
                    'u128',
                    'u128',
                ),
                'LiquidityRemoved': (
                    'AccountId',
                    'u32',
                    'u32',
                    'u128',
                    'u128',
                    'u128',
                    'u32',
                    'u128',
                    'u128',
                ),
                'PoolCreated': ('AccountId', 'u32', 'u32', 'u32'),
                'ProtocolFeeReceiverUpdated': 'AccountId',
                'ProtocolFeeUpdated': 'u32',
                'Traded': (
                    'AccountId',
                    'u32',
                    'u32',
                    'u128',
                    'u128',
                    'u32',
                    'u128',
                    'u128',
                ),
            },
            'AMMRoute': {'Traded': ('AccountId', 'u128', ['u32'], 'u128')},
            'AssetRegistry': {
                'AssetDeregisteredd': {
                    'asset_id': 'u32',
                    'asset_type': 'scale_info::158',
                },
                'AssetRegistered': {
                    'asset_id': 'u32',
                    'asset_type': 'scale_info::158',
                },
                'AssetTypeUpdated': {
                    'asset_id': 'u32',
                    'new_asset_type': 'scale_info::158',
                },
                'FeePaymentAssetRemoved': {'asset_type': 'scale_info::158'},
                'UnitsPerSecondUpdated': {
                    'asset_type': 'scale_info::158',
                    'units_per_second': 'u128',
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
                'AssetStatusChanged': {'asset_id': 'u32'},
                'AssetThawed': {'asset_id': 'u32'},
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
                    'destination_status': 'scale_info::35',
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
            'BaseFee': {
                'BaseFeeOverflow': None,
                'NewBaseFeePerGas': {'fee': '[u64; 4]'},
                'NewElasticity': {'elasticity': 'u32'},
            },
            'Bridge': {
                'BridgeTokenAccumulatedValueCleaned': (
                    'u32',
                    'scale_info::151',
                ),
                'BridgeTokenCapUpdated': ('u32', 'scale_info::151', 'u128'),
                'BridgeTokenFeeUpdated': ('u32', 'u128'),
                'BridgeTokenRegistered': (
                    'u32',
                    'u32',
                    'bool',
                    'u128',
                    'bool',
                    'u128',
                    'u128',
                    'u128',
                    'u128',
                ),
                'BridgeTokenRemoved': ('u32', 'u32'),
                'BridgeTokenStatusUpdated': ('u32', 'bool'),
                'ChainRegistered': 'u32',
                'ChainRemoved': 'u32',
                'MaterializeInitialized': (
                    'AccountId',
                    'u32',
                    'u64',
                    'u32',
                    'AccountId',
                    'u128',
                ),
                'MaterializeMinted': (
                    'u32',
                    'u64',
                    'u32',
                    'AccountId',
                    'u128',
                ),
                'MaterializeVoteAgainst': (
                    'u32',
                    'u64',
                    'AccountId',
                    'u32',
                    'AccountId',
                    'u128',
                ),
                'MaterializeVoteFor': (
                    'u32',
                    'u64',
                    'AccountId',
                    'u32',
                    'AccountId',
                    'u128',
                ),
                'ProposalApproved': ('u32', 'u64'),
                'ProposalRejected': ('u32', 'u64'),
                'TeleportBurned': (
                    'AccountId',
                    'u32',
                    'u64',
                    'u32',
                    'Bytes',
                    'u128',
                    'u128',
                ),
                'VoteThresholdUpdated': 'u32',
            },
            'BridgeMembership': (
                'MemberAdded',
                'MemberRemoved',
                'MembersSwapped',
                'MembersReset',
                'KeyChanged',
                'Dummy',
            ),
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
            'Crowdloans': {
                'AllMigrated': ('u32', ('u32', 'u32')),
                'AllRefunded': ('u32', ('u32', 'u32')),
                'LeasesBonusUpdated': (('u32', 'u32'), 'scale_info::136'),
                'NotificationReceived': (
                    'scale_info::60',
                    'u64',
                    (None, ('u32', 'scale_info::55')),
                ),
                'PartiallyMigrated': ('u32', ('u32', 'u32')),
                'PartiallyRefunded': ('u32', ('u32', 'u32')),
                'ProxyUpdated': 'AccountId',
                'UserRefunded': (
                    'u32',
                    ('u32', 'u32'),
                    'AccountId',
                    'scale_info::135',
                    'u128',
                ),
                'VaultClaimed': (
                    'u32',
                    ('u32', 'u32'),
                    'u32',
                    'AccountId',
                    'u128',
                    'scale_info::133',
                ),
                'VaultContributed': ('u32', ('u32', 'u32'), 'AccountId', 'u128', 'Bytes'),
                'VaultCreated': (
                    'u32',
                    ('u32', 'u32'),
                    'u32',
                    'scale_info::133',
                    'scale_info::134',
                    'u128',
                    'u32',
                    'u32',
                ),
                'VaultDissolved': ('u32', ('u32', 'u32')),
                'VaultDoContributing': (
                    'u32',
                    ('u32', 'u32'),
                    'AccountId',
                    'u128',
                    'Bytes',
                ),
                'VaultDoWithdrawing': ('u32', ('u32', 'u32'), 'u128', 'scale_info::133'),
                'VaultPhaseUpdated': (
                    'u32',
                    ('u32', 'u32'),
                    'scale_info::133',
                    'scale_info::133',
                ),
                'VaultRedeemed': (
                    'u32',
                    ('u32', 'u32'),
                    'u32',
                    'AccountId',
                    'u128',
                    'scale_info::133',
                ),
                'VaultUpdated': ('u32', ('u32', 'u32'), 'scale_info::134', 'u128', 'u32'),
                'VaultWithdrew': (
                    'u32',
                    ('u32', 'u32'),
                    'AccountId',
                    'u128',
                    'scale_info::133',
                ),
                'VrfUpdated': 'bool',
            },
            'CrowdloansAutomatorsMembership': (
                'MemberAdded',
                'MemberRemoved',
                'MembersSwapped',
                'MembersReset',
                'KeyChanged',
                'Dummy',
            ),
            'CumulusXcm': {
                'ExecutedDownward': ('[u8; 32]', 'scale_info::58'),
                'InvalidFormat': '[u8; 32]',
                'UnsupportedVersion': '[u8; 32]',
            },
            'Democracy': {
                'Blacklisted': {'proposal_hash': '[u8; 32]'},
                'Cancelled': {'ref_index': 'u32'},
                'Delegated': {'target': 'AccountId', 'who': 'AccountId'},
                'ExternalTabled': None,
                'NotPassed': {'ref_index': 'u32'},
                'Passed': {'ref_index': 'u32'},
                'ProposalCanceled': {'prop_index': 'u32'},
                'Proposed': {'deposit': 'u128', 'proposal_index': 'u32'},
                'Seconded': {'prop_index': 'u32', 'seconder': 'AccountId'},
                'Started': {'ref_index': 'u32', 'threshold': 'scale_info::44'},
                'Tabled': {'deposit': 'u128', 'proposal_index': 'u32'},
                'Undelegated': {'account': 'AccountId'},
                'Vetoed': {
                    'proposal_hash': '[u8; 32]',
                    'until': 'u32',
                    'who': 'AccountId',
                },
                'Voted': {
                    'ref_index': 'u32',
                    'vote': 'scale_info::45',
                    'voter': 'AccountId',
                },
            },
            'DmpQueue': {
                'ExecutedDownward': {
                    'message_id': '[u8; 32]',
                    'outcome': 'scale_info::58',
                },
                'InvalidFormat': {'message_id': '[u8; 32]'},
                'MaxMessagesExhausted': {'message_id': '[u8; 32]'},
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
            'EVM': {
                'Created': {'address': '[u8; 20]'},
                'CreatedFailed': {'address': '[u8; 20]'},
                'Executed': {'address': '[u8; 20]'},
                'ExecutedFailed': {'address': '[u8; 20]'},
                'Log': {'log': 'scale_info::160'},
            },
            'EVMSignatureCall': {'Executed': ('AccountId', 'scale_info::30')},
            'EmergencyShutdown': {
                'ToggledCall': 'bool',
                'ToggledPallet': 'bool',
            },
            'Ethereum': {
                'Executed': {
                    'exit_reason': 'scale_info::164',
                    'from': '[u8; 20]',
                    'to': '[u8; 20]',
                    'transaction_hash': '[u8; 32]',
                },
            },
            'Farming': {
                'AssetsDeposited': ('AccountId', 'u32', 'u32', 'u32', 'u128'),
                'AssetsRedeem': ('AccountId', 'u32', 'u32', 'u32', 'u128'),
                'AssetsWithdrew': ('AccountId', 'u32', 'u32', 'u32', 'u128'),
                'PoolAdded': ('u32', 'u32', 'u32'),
                'PoolCoolDownDurationChanged': ('u32', 'u32', 'u32', 'u32'),
                'PoolStatusChanged': ('u32', 'u32', 'u32', 'bool'),
                'PoolUnlockHeightReset': ('u32', 'u32', 'u32', 'u32'),
                'RewardAdded': ('u32', 'u32', 'u32', 'u128'),
                'RewardPaid': ('AccountId', 'u32', 'u32', 'u32', 'u128'),
            },
            'GeneralCouncil': {
                'Approved': {'proposal_hash': '[u8; 32]'},
                'Closed': {
                    'no': 'u32',
                    'proposal_hash': '[u8; 32]',
                    'yes': 'u32',
                },
                'Disapproved': {'proposal_hash': '[u8; 32]'},
                'Executed': {
                    'proposal_hash': '[u8; 32]',
                    'result': 'scale_info::30',
                },
                'MemberExecuted': {
                    'proposal_hash': '[u8; 32]',
                    'result': 'scale_info::30',
                },
                'Proposed': {
                    'account': 'AccountId',
                    'proposal_hash': '[u8; 32]',
                    'proposal_index': 'u32',
                    'threshold': 'u32',
                },
                'Voted': {
                    'account': 'AccountId',
                    'no': 'u32',
                    'proposal_hash': '[u8; 32]',
                    'voted': 'bool',
                    'yes': 'u32',
                },
            },
            'GeneralCouncilMembership': (
                'MemberAdded',
                'MemberRemoved',
                'MembersSwapped',
                'MembersReset',
                'KeyChanged',
                'Dummy',
            ),
            'Identity': {
                'IdentityCleared': {'deposit': 'u128', 'who': 'AccountId'},
                'IdentityKilled': {'deposit': 'u128', 'who': 'AccountId'},
                'IdentitySet': {'who': 'AccountId'},
                'JudgementGiven': {
                    'registrar_index': 'u32',
                    'target': 'AccountId',
                },
                'JudgementRequested': {
                    'registrar_index': 'u32',
                    'who': 'AccountId',
                },
                'JudgementUnrequested': {
                    'registrar_index': 'u32',
                    'who': 'AccountId',
                },
                'RegistrarAdded': {'registrar_index': 'u32'},
                'SubIdentityAdded': {
                    'deposit': 'u128',
                    'main': 'AccountId',
                    'sub': 'AccountId',
                },
                'SubIdentityRemoved': {
                    'deposit': 'u128',
                    'main': 'AccountId',
                    'sub': 'AccountId',
                },
                'SubIdentityRevoked': {
                    'deposit': 'u128',
                    'main': 'AccountId',
                    'sub': 'AccountId',
                },
            },
            'LiquidStaking': {
                'Bonding': ('u16', 'AccountId', 'u128', 'scale_info::141'),
                'BondingExtra': ('u16', 'u128'),
                'ClaimedFor': ('AccountId', 'u128'),
                'CommissionRateUpdated': 'u128',
                'ExchangeRateUpdated': 'u128',
                'FastUnstakeMatched': ('AccountId', 'u128', 'u128', 'u128'),
                'IncentiveUpdated': 'u128',
                'Matching': ('u128', 'u128', 'u128'),
                'NewEra': 'u32',
                'Nominating': ('u16', ['AccountId']),
                'NonIdealStakingLedger': 'u16',
                'NotificationReceived': (
                    'scale_info::60',
                    'u64',
                    (None, ('u32', 'scale_info::55')),
                ),
                'Rebonding': ('u16', 'u128'),
                'ReserveFactorUpdated': 'u32',
                'ReservesReduced': ('AccountId', 'u128'),
                'Staked': ('AccountId', 'u128'),
                'StakingLedgerCapUpdated': 'u128',
                'StakingLedgerUpdated': ('u16', 'scale_info::138'),
                'Unbonding': ('u16', 'u128'),
                'UnstakeCancelled': ('AccountId', 'u128', 'u128'),
                'Unstaked': ('AccountId', 'u128', 'u128'),
                'WithdrawingUnbonded': ('u16', 'u32'),
            },
            'LiquidStakingAgentsMembership': (
                'MemberAdded',
                'MemberRemoved',
                'MembersSwapped',
                'MembersReset',
                'KeyChanged',
                'Dummy',
            ),
            'Loans': {
                'ActivatedMarket': 'u32',
                'Borrowed': ('AccountId', 'u32', 'u128'),
                'CollateralAssetAdded': ('AccountId', 'u32'),
                'CollateralAssetRemoved': ('AccountId', 'u32'),
                'Deposited': ('AccountId', 'u32', 'u128'),
                'DistributedBorrowerReward': (
                    'u32',
                    'AccountId',
                    'u128',
                    'u128',
                ),
                'DistributedSupplierReward': (
                    'u32',
                    'AccountId',
                    'u128',
                    'u128',
                ),
                'IncentiveReservesReduced': ('AccountId', 'u32', 'u128'),
                'LiquidatedBorrow': (
                    'AccountId',
                    'AccountId',
                    'u32',
                    'u32',
                    'u128',
                    'u128',
                ),
                'LiquidationFreeCollateralsUpdated': ['u32'],
                'MarketRewardSpeedUpdated': ('u32', 'u128', 'u128'),
                'NewMarket': ('u32', 'scale_info::124'),
                'Redeemed': ('AccountId', 'u32', 'u128'),
                'RepaidBorrow': ('AccountId', 'u32', 'u128'),
                'ReservesAdded': ('AccountId', 'u32', 'u128', 'u128'),
                'ReservesReduced': ('AccountId', 'u32', 'u128', 'u128'),
                'RewardAdded': ('AccountId', 'u128'),
                'RewardPaid': ('AccountId', 'u128'),
                'RewardWithdrawn': ('AccountId', 'u128'),
                'UpdatedMarket': ('u32', 'scale_info::124'),
            },
            'Multisig': {
                'MultisigApproval': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                    'timepoint': 'scale_info::33',
                },
                'MultisigCancelled': {
                    'call_hash': '[u8; 32]',
                    'cancelling': 'AccountId',
                    'multisig': 'AccountId',
                    'timepoint': 'scale_info::33',
                },
                'MultisigExecuted': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                    'result': 'scale_info::30',
                    'timepoint': 'scale_info::33',
                },
                'NewMultisig': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                },
            },
            'Oracle': {
                'NewFeedData': {
                    'sender': 'AccountId',
                    'values': [('u32', 'u128')],
                },
            },
            'OracleMembership': (
                'MemberAdded',
                'MemberRemoved',
                'MembersSwapped',
                'MembersReset',
                'KeyChanged',
                'Dummy',
            ),
            'OrmlXcm': {
                'Sent': {'message': ['scale_info::72'], 'to': 'scale_info::60'},
            },
            'ParachainSystem': {
                'DownwardMessagesProcessed': {
                    'dmq_head': '[u8; 32]',
                    'weight_used': 'scale_info::8',
                },
                'DownwardMessagesReceived': {'count': 'u32'},
                'UpgradeAuthorized': {'code_hash': '[u8; 32]'},
                'UpwardMessageSent': {'message_hash': (None, '[u8; 32]')},
                'ValidationFunctionApplied': {'relay_chain_block_num': 'u32'},
                'ValidationFunctionDiscarded': None,
                'ValidationFunctionStored': None,
            },
            'PolkadotXcm': {
                'AssetsClaimed': (
                    '[u8; 32]',
                    'scale_info::60',
                    'scale_info::96',
                ),
                'AssetsTrapped': (
                    '[u8; 32]',
                    'scale_info::60',
                    'scale_info::96',
                ),
                'Attempted': {
                    'Complete': 'scale_info::8',
                    'Error': 'scale_info::55',
                    'Incomplete': ('scale_info::8', 'scale_info::55'),
                },
                'FeesPaid': ('scale_info::60', ['scale_info::75']),
                'InvalidQuerier': (
                    'scale_info::60',
                    'u64',
                    'scale_info::60',
                    (None, 'scale_info::60'),
                ),
                'InvalidQuerierVersion': ('scale_info::60', 'u64'),
                'InvalidResponder': (
                    'scale_info::60',
                    'u64',
                    (None, 'scale_info::60'),
                ),
                'InvalidResponderVersion': ('scale_info::60', 'u64'),
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
                'NotifyTargetMigrationFail': ('scale_info::110', 'u64'),
                'NotifyTargetSendFail': (
                    'scale_info::60',
                    'u64',
                    'scale_info::55',
                ),
                'ResponseReady': ('u64', 'scale_info::81'),
                'ResponseTaken': 'u64',
                'Sent': (
                    'scale_info::60',
                    'scale_info::60',
                    ['scale_info::72'],
                ),
                'SupportedVersionChanged': ('scale_info::60', 'u32'),
                'UnexpectedResponse': ('scale_info::60', 'u64'),
                'VersionChangeNotified': (
                    'scale_info::60',
                    'u32',
                    ['scale_info::75'],
                ),
                'VersionNotifyRequested': (
                    'scale_info::60',
                    ['scale_info::75'],
                ),
                'VersionNotifyStarted': ('scale_info::60', ['scale_info::75']),
                'VersionNotifyUnrequested': (
                    'scale_info::60',
                    ['scale_info::75'],
                ),
            },
            'Preimage': {
                'Cleared': {'hash': '[u8; 32]'},
                'Noted': {'hash': '[u8; 32]'},
                'Requested': {'hash': '[u8; 32]'},
            },
            'Prices': {'ResetPrice': 'u32', 'SetPrice': ('u32', 'u128')},
            'Proxy': {
                'Announced': {
                    'call_hash': '[u8; 32]',
                    'proxy': 'AccountId',
                    'real': 'AccountId',
                },
                'ProxyAdded': {
                    'delay': 'u32',
                    'delegatee': 'AccountId',
                    'delegator': 'AccountId',
                    'proxy_type': 'scale_info::40',
                },
                'ProxyExecuted': {'result': 'scale_info::30'},
                'ProxyRemoved': {
                    'delay': 'u32',
                    'delegatee': 'AccountId',
                    'delegator': 'AccountId',
                    'proxy_type': 'scale_info::40',
                },
                'PureCreated': {
                    'disambiguation_index': 'u16',
                    'proxy_type': 'scale_info::40',
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
                    'result': 'scale_info::30',
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
            'Streaming': {
                'MinimumDepositSet': ('u32', 'u128'),
                'StreamCancelled': (
                    'u128',
                    'AccountId',
                    'AccountId',
                    'u32',
                    'u128',
                    'u128',
                ),
                'StreamCreated': (
                    'u128',
                    'AccountId',
                    'AccountId',
                    'u128',
                    'u32',
                    'u64',
                    'u64',
                    'bool',
                ),
                'StreamWithdrawn': ('u128', 'AccountId', 'u32', 'u128'),
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
                'Remarked': {'hash': '[u8; 32]', 'sender': 'AccountId'},
            },
            'TechnicalCommittee': {
                'Approved': {'proposal_hash': '[u8; 32]'},
                'Closed': {
                    'no': 'u32',
                    'proposal_hash': '[u8; 32]',
                    'yes': 'u32',
                },
                'Disapproved': {'proposal_hash': '[u8; 32]'},
                'Executed': {
                    'proposal_hash': '[u8; 32]',
                    'result': 'scale_info::30',
                },
                'MemberExecuted': {
                    'proposal_hash': '[u8; 32]',
                    'result': 'scale_info::30',
                },
                'Proposed': {
                    'account': 'AccountId',
                    'proposal_hash': '[u8; 32]',
                    'proposal_index': 'u32',
                    'threshold': 'u32',
                },
                'Voted': {
                    'account': 'AccountId',
                    'no': 'u32',
                    'proposal_hash': '[u8; 32]',
                    'voted': 'bool',
                    'yes': 'u32',
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
            None: None,
            'TechnicalCommitteeMembership': (
                'MemberAdded',
                'MemberRemoved',
                'MembersSwapped',
                'MembersReset',
                'KeyChanged',
                'Dummy',
            ),
            'TransactionPayment': {
                'TransactionFeePaid': {
                    'actual_fee': 'u128',
                    'tip': 'u128',
                    'who': 'AccountId',
                },
            },
            'Utility': {
                'BatchCompleted': None,
                'BatchCompletedWithErrors': None,
                'BatchInterrupted': {
                    'error': 'scale_info::24',
                    'index': 'u32',
                },
                'DispatchedAs': {'result': 'scale_info::30'},
                'ItemCompleted': None,
                'ItemFailed': {'error': 'scale_info::24'},
            },
            'Vesting': {
                'Claimed': {'amount': 'u128', 'who': 'AccountId'},
                'VestingScheduleAdded': {
                    'from': 'AccountId',
                    'to': 'AccountId',
                    'vesting_schedule': 'scale_info::122',
                },
                'VestingSchedulesUpdated': {'who': 'AccountId'},
            },
            'XTokens': {
                'TransferredMultiAssets': {
                    'assets': ['scale_info::75'],
                    'dest': 'scale_info::60',
                    'fee': 'scale_info::75',
                    'sender': 'AccountId',
                },
            },
            'XcmHelper': {
                'XcmWeightFeeUpdated': {
                    'fee': 'u128',
                    'weight': 'scale_info::8',
                },
            },
            'XcmpQueue': {
                'BadFormat': {'message_hash': (None, '[u8; 32]')},
                'BadVersion': {'message_hash': (None, '[u8; 32]')},
                'Fail': {
                    'error': 'scale_info::55',
                    'message_hash': (None, '[u8; 32]'),
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
                'Success': {'message_hash': (None, '[u8; 32]'), 'weight': 'scale_info::8'},
                'XcmpMessageSent': {'message_hash': (None, '[u8; 32]')},
            },
        },
        'phase': {
            'ApplyExtrinsic': 'u32',
            'Finalization': None,
            'Initialization': None,
        },
        'topics': ['[u8; 32]'],
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
'[u8; 32]'
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
    'base_block': {'proof_size': 0, 'ref_time': 381015000},
    'max_block': {'proof_size': 5242880, 'ref_time': 500000000000},
    'per_class': {
        'mandatory': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 99840000},
            'max_extrinsic': None,
            'max_total': None,
            'reserved': None,
        },
        'normal': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 99840000},
            'max_extrinsic': {'proof_size': 3407872, 'ref_time': 324900160000},
            'max_total': {'proof_size': 3932160, 'ref_time': 375000000000},
            'reserved': {'proof_size': 0, 'ref_time': 0},
        },
        'operational': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 99840000},
            'max_extrinsic': {'proof_size': 4718592, 'ref_time': 449900160000},
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
172
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
        ('0xab3c0572291feb8b', 1),
        ('0xdf6acb689907609b', 4),
        ('0x37e397fc7c91f5e4', 1),
        ('0x40fe3ad401f8959a', 6),
        ('0xd2bc9897eed08f15', 3),
        ('0xf78b278be53f454c', 2),
        ('0xbc9d89904f5b923f', 1),
        ('0x37c8bb1350a9a2a8', 3),
        ('0x6ef953004ba30e59', 1),
        ('0xea93e3f16f3d6962', 2),
        ('0x22b97323b9e853da', 1),
        ('0x99bb7f9383f5f9b8', 1),
        ('0x582211f65bb14b89', 4),
        ('0xe65b00e46cedd0aa', 2),
    ],
    'authoring_version': 1,
    'impl_name': 'parallel',
    'impl_version': 33,
    'spec_name': 'parallel',
    'spec_version': 201,
    'state_version': 0,
    'transaction_version': 17,
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