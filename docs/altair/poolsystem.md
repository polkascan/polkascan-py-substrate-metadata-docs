
# PoolSystem

---------
## Calls

---------
### close_epoch
Close the current epoch

Closing an epoch locks in all invest and redeem
orders placed during the epoch, and causes all
further invest and redeem orders to be set for the
next epoch.

If all orders can be executed without violating any
pool constraints - which include maximum reserve and
the tranche risk buffers - the execution will also be
done. See `execute_epoch` for details on epoch
execution.

If pool constraints would be violated by executing all
orders, the pool enters a submission period. During a
submission period, partial executions can be submitted
to be scored, and the best-scoring solution will
eventually be executed. See `submit_solution`.
#### Attributes
| Name | Type |
| -------- | -------- | 
| pool_id | `T::PoolId` | 

#### Python
```python
call = substrate.compose_call(
    'PoolSystem', 'close_epoch', {'pool_id': 'u64'}
)
```

---------
### execute_epoch
Execute an epoch for which a valid solution has been
submitted.

* Mints or burns tranche tokens based on investments and redemptions
* Updates the portion of the reserve and loan balance assigned to
  each tranche, based on the investments and redemptions to those
  tranches.
#### Attributes
| Name | Type |
| -------- | -------- | 
| pool_id | `T::PoolId` | 

#### Python
```python
call = substrate.compose_call(
    'PoolSystem', 'execute_epoch', {'pool_id': 'u64'}
)
```

---------
### set_max_reserve
Sets the maximum reserve for a pool

The caller must have the `LiquidityAdmin` role in
order to invoke this extrinsic. This role is not
given to the pool creator by default, and must be
added with the Permissions pallet before this
extrinsic can be called.
#### Attributes
| Name | Type |
| -------- | -------- | 
| pool_id | `T::PoolId` | 
| max_reserve | `T::Balance` | 

#### Python
```python
call = substrate.compose_call(
    'PoolSystem', 'set_max_reserve', {
    'max_reserve': 'u128',
    'pool_id': 'u64',
}
)
```

---------
### submit_solution
Submit a partial execution solution for a closed epoch

If the submitted solution is &quot;better&quot; than the
previous best solution, it will replace it. Solutions
are ordered such that solutions which do not violate
constraints are better than those that do.

Once a valid solution has been submitted, the
challenge time begins. The pool can be executed once
the challenge time has expired.
#### Attributes
| Name | Type |
| -------- | -------- | 
| pool_id | `T::PoolId` | 
| solution | `Vec<TrancheSolution>` | 

#### Python
```python
call = substrate.compose_call(
    'PoolSystem', 'submit_solution', {
    'pool_id': 'u64',
    'solution': [
        {
            'invest_fulfillment': 'u64',
            'redeem_fulfillment': 'u64',
        },
    ],
}
)
```

---------
## Events

---------
### Created
A pool was created.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| admin | `T::AccountId` | ```AccountId```
| depositor | `T::AccountId` | ```AccountId```
| pool_id | `T::PoolId` | ```u64```
| essence | `PoolEssenceOf<T>` | ```{'currency': {'Native': None, 'Tranche': ('u64', '[u8; 16]'), None: None, 'AUSD': None, 'ForeignAsset': 'u32', 'Staking': ('BlockRewards',), 'LocalAsset': 'u32'}, 'max_reserve': 'u128', 'max_nav_age': 'u64', 'min_epoch_time': 'u64', 'tranches': [{'currency': {'pool_id': 'u64', 'tranche_id': '[u8; 16]'}, 'ty': {'Residual': None, 'NonResidual': {'interest_rate_per_sec': 'u128', 'min_risk_buffer': 'u64'}}, 'metadata': {'token_name': 'Bytes', 'token_symbol': 'Bytes'}}]}```

---------
### EpochClosed
An epoch was closed.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| pool_id | `T::PoolId` | ```u64```
| epoch_id | `T::EpochId` | ```u32```

---------
### EpochExecuted
An epoch was executed.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| pool_id | `T::PoolId` | ```u64```
| epoch_id | `T::EpochId` | ```u32```

---------
### MaxReserveSet
The max reserve was updated.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| pool_id | `T::PoolId` | ```u64```

---------
### NegativeBalanceSheet
The PoolFeesNAV exceeds the sum of the AUM and the total reserve of
the pool
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| pool_id | `T::PoolId` | ```u64```
| nav_aum | `T::Balance` | ```u128```
| nav_fees | `T::Balance` | ```u128```
| reserve | `T::Balance` | ```u128```

---------
### ProposedChange
A change was proposed.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| pool_id | `T::PoolId` | ```u64```
| change_id | `T::Hash` | ```scale_info::12```
| change | `T::RuntimeChange` | ```{'Loans': {'Loan': ('u64', {'Maturity': {'Fixed': 'InnerStruct'}, 'MaturityExtension': 'u64', 'InterestRate': {'Fixed': 'InnerStruct'}, 'InterestPayments': ('None',), 'PayDownSchedule': ('None',), 'Internal': {'ValuationMethod': 'scale_info::122', 'ProbabilityOfDefault': 'u128', 'LossGivenDefault': 'u128', 'DiscountRate': 'scale_info::117'}}), 'Policy': [{'triggers': 'scale_info::129', 'status': 'scale_info::131'}], 'TransferDebt': ('u64', 'u64', {'principal': {'Internal': 'u128', 'External': 'scale_info::135'}, 'interest': 'u128', 'unscheduled': 'u128'}, {'Internal': 'u128', 'External': {'quantity': 'u128', 'settlement_price': 'u128'}})}, 'OracleCollection': {'CollectionInfo': {'value_lifetime': (None, 'u64'), 'min_feeders': 'u32', 'feeders': 'scale_info::162'}}, 'PoolFee': {'AppendFee': ('u64', ('Top',), {'destination': 'AccountId', 'editor': {'Root': None, 'Account': 'AccountId'}, 'fee_type': {'Fixed': 'InnerStruct', 'ChargedUpTo': 'InnerStruct'}})}, '_Unreachable': None}```

---------
### Rebalanced
The tranches were rebalanced.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| pool_id | `T::PoolId` | ```u64```

---------
### SolutionSubmitted
An epoch was executed.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| pool_id | `T::PoolId` | ```u64```
| epoch_id | `T::EpochId` | ```u32```
| solution | `EpochSolution<T::Balance, T::MaxTranches>` | ```{'Healthy': {'solution': [{'invest_fulfillment': 'u64', 'redeem_fulfillment': 'u64'}], 'score': 'u128'}, 'Unhealthy': {'state': [('MaxReserveViolated', 'MinRiskBufferViolated')], 'solution': [{'invest_fulfillment': 'u64', 'redeem_fulfillment': 'u64'}], 'risk_buffer_improvement_scores': (None, ['u128']), 'reserve_improvement_score': (None, 'u128')}}```

---------
### Updated
A pool was updated.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| id | `T::PoolId` | ```u64```
| old | `PoolEssenceOf<T>` | ```{'currency': {'Native': None, 'Tranche': ('u64', '[u8; 16]'), None: None, 'AUSD': None, 'ForeignAsset': 'u32', 'Staking': ('BlockRewards',), 'LocalAsset': 'u32'}, 'max_reserve': 'u128', 'max_nav_age': 'u64', 'min_epoch_time': 'u64', 'tranches': [{'currency': {'pool_id': 'u64', 'tranche_id': '[u8; 16]'}, 'ty': {'Residual': None, 'NonResidual': {'interest_rate_per_sec': 'u128', 'min_risk_buffer': 'u64'}}, 'metadata': {'token_name': 'Bytes', 'token_symbol': 'Bytes'}}]}```
| new | `PoolEssenceOf<T>` | ```{'currency': {'Native': None, 'Tranche': ('u64', '[u8; 16]'), None: None, 'AUSD': None, 'ForeignAsset': 'u32', 'Staking': ('BlockRewards',), 'LocalAsset': 'u32'}, 'max_reserve': 'u128', 'max_nav_age': 'u64', 'min_epoch_time': 'u64', 'tranches': [{'currency': {'pool_id': 'u64', 'tranche_id': '[u8; 16]'}, 'ty': {'Residual': None, 'NonResidual': {'interest_rate_per_sec': 'u128', 'min_risk_buffer': 'u64'}}, 'metadata': {'token_name': 'Bytes', 'token_symbol': 'Bytes'}}]}```

---------
## Storage functions

---------
### AccountDeposit

#### Python
```python
result = substrate.query(
    'PoolSystem', 'AccountDeposit', ['AccountId']
)
```

#### Return value
```python
'u128'
```
---------
### EpochExecution

#### Python
```python
result = substrate.query(
    'PoolSystem', 'EpochExecution', ['u64']
)
```

#### Return value
```python
{
    'best_submission': (
        None,
        {
            'Healthy': {'score': 'u128', 'solution': ['scale_info::90']},
            'Unhealthy': {
                'reserve_improvement_score': (None, 'u128'),
                'risk_buffer_improvement_scores': (None, ['u128']),
                'solution': ['scale_info::90'],
                'state': ['scale_info::95'],
            },
        },
    ),
    'challenge_period_end': (None, 'u32'),
    'epoch': 'u32',
    'nav': {'nav_aum': 'u128', 'nav_fees': 'u128'},
    'tranches': {
        'tranches': [
            {
                'currency': 'scale_info::102',
                'invest': 'u128',
                'min_risk_buffer': 'u64',
                'price': 'u128',
                'redeem': 'u128',
                'seniority': 'u32',
                'supply': 'u128',
            },
        ],
    },
}
```
---------
### NotedChange

#### Python
```python
result = substrate.query(
    'PoolSystem', 'NotedChange', ['u64', 'scale_info::12']
)
```

#### Return value
```python
{
    'change': {
        'Loans': {
            'Loan': (
                'u64',
                {
                    'InterestPayments': 'scale_info::119',
                    'InterestRate': 'scale_info::117',
                    'Internal': 'scale_info::121',
                    'Maturity': 'scale_info::116',
                    'MaturityExtension': 'u64',
                    'PayDownSchedule': 'scale_info::120',
                },
            ),
            'Policy': ['scale_info::125'],
            'TransferDebt': (
                'u64',
                'u64',
                {
                    'interest': 'u128',
                    'principal': 'scale_info::134',
                    'unscheduled': 'u128',
                },
                {'External': 'scale_info::135', 'Internal': 'u128'},
            ),
        },
        'OracleCollection': {
            'CollectionInfo': {
                'feeders': 'scale_info::162',
                'min_feeders': 'u32',
                'value_lifetime': (None, 'u64'),
            },
        },
        'PoolFee': {
            'AppendFee': (
                'u64',
                ('Top', ),
                {
                    'destination': 'AccountId',
                    'editor': 'scale_info::167',
                    'fee_type': 'scale_info::168',
                },
            ),
        },
        '_Unreachable': None,
    },
    'submitted_time': 'u64',
}
```
---------
### Pool

#### Python
```python
result = substrate.query(
    'PoolSystem', 'Pool', ['u64']
)
```

#### Return value
```python
{
    'currency': {
        'Native': None,
        'Tranche': ('u64', '[u8; 16]'),
        None: None,
        'AUSD': None,
        'ForeignAsset': 'u32',
        'LocalAsset': 'u32',
        'Staking': ('BlockRewards', ),
    },
    'epoch': {'current': 'u32', 'last_closed': 'u64', 'last_executed': 'u32'},
    'parameters': {'max_nav_age': 'u64', 'min_epoch_time': 'u64'},
    'reserve': {'available': 'u128', 'max': 'u128', 'total': 'u128'},
    'status': ('Open', ),
    'tranches': {
        'ids': ['[u8; 16]'],
        'salt': ('u64', 'u64'),
        'tranches': [
            {
                'currency': 'scale_info::102',
                'debt': 'u128',
                'last_updated_interest': 'u64',
                'loss': 'u128',
                'ratio': 'u64',
                'reserve': 'u128',
                'seniority': 'u32',
                'tranche_type': 'scale_info::108',
            },
        ],
    },
}
```
---------
### PoolDeposit

#### Python
```python
result = substrate.query(
    'PoolSystem', 'PoolDeposit', ['u64']
)
```

#### Return value
```python
{'deposit': 'u128', 'depositor': 'AccountId'}
```
---------
### ScheduledUpdate

#### Python
```python
result = substrate.query(
    'PoolSystem', 'ScheduledUpdate', ['u64']
)
```

#### Return value
```python
{
    'changes': {
        'max_nav_age': {'NewValue': 'u64', 'NoChange': None},
        'min_epoch_time': {'NewValue': 'u64', 'NoChange': None},
        'tranche_metadata': {'NewValue': ['scale_info::109'], 'NoChange': None},
        'tranches': {'NewValue': ['scale_info::374'], 'NoChange': None},
    },
    'submitted_at': 'u64',
}
```
---------
## Constants

---------
### ChallengeTime
 Challenge time
#### Value
```python
150
```
#### Python
```python
constant = substrate.get_constant('PoolSystem', 'ChallengeTime')
```
---------
### DefaultMaxNAVAge
#### Value
```python
0
```
#### Python
```python
constant = substrate.get_constant('PoolSystem', 'DefaultMaxNAVAge')
```
---------
### DefaultMinEpochTime
 Pool parameter defaults
#### Value
```python
85800
```
#### Python
```python
constant = substrate.get_constant('PoolSystem', 'DefaultMinEpochTime')
```
---------
### MaxNAVAgeUpperBound
#### Value
```python
0
```
#### Python
```python
constant = substrate.get_constant('PoolSystem', 'MaxNAVAgeUpperBound')
```
---------
### MaxTokenNameLength
 Max length for a tranche token name
#### Value
```python
128
```
#### Python
```python
constant = substrate.get_constant('PoolSystem', 'MaxTokenNameLength')
```
---------
### MaxTokenSymbolLength
 Max length for a tranche token symbol
#### Value
```python
32
```
#### Python
```python
constant = substrate.get_constant('PoolSystem', 'MaxTokenSymbolLength')
```
---------
### MaxTranches
 Max number of Tranches
#### Value
```python
5
```
#### Python
```python
constant = substrate.get_constant('PoolSystem', 'MaxTranches')
```
---------
### MinEpochTimeLowerBound
 Pool parameter bounds
#### Value
```python
3600
```
#### Python
```python
constant = substrate.get_constant('PoolSystem', 'MinEpochTimeLowerBound')
```
---------
### MinEpochTimeUpperBound
#### Value
```python
2592000
```
#### Python
```python
constant = substrate.get_constant('PoolSystem', 'MinEpochTimeUpperBound')
```
---------
### MinUpdateDelay
 Pool update settings
#### Value
```python
172800
```
#### Python
```python
constant = substrate.get_constant('PoolSystem', 'MinUpdateDelay')
```
---------
### PalletId
#### Value
```python
'0x726f632f706f6f6c'
```
#### Python
```python
constant = substrate.get_constant('PoolSystem', 'PalletId')
```
---------
### PalletIndex
 The immutable index of this pallet when instantiated within the
 context of a runtime where it is used.
#### Value
```python
99
```
#### Python
```python
constant = substrate.get_constant('PoolSystem', 'PalletIndex')
```
---------
### PoolDeposit
 The amount that must be reserved to create a pool
#### Value
```python
0
```
#### Python
```python
constant = substrate.get_constant('PoolSystem', 'PoolDeposit')
```
---------
## Errors

---------
### CannotAddOrRemoveTranches
Adding &amp; removing tranches is not supported

---------
### ChallengeTimeHasNotPassed
Attempted to execute an epoch too early

---------
### ChangeNotFound
The external change was not found for the specified ChangeId.

---------
### ChangeNotReady
The external change was found for is not ready yet to be released.

---------
### EpochNotExecutedYet
Epoch needs to be executed before you can collect

---------
### FailedToRegisterTrancheMetadata
Registering the metadata for a tranche threw an error

---------
### FailedToUpdateTrancheMetadata
Updating the metadata for a tranche threw an error

---------
### InSubmissionPeriod
Cannot be called while the pool is in a submission period

---------
### InsufficientCurrency
Insufficient currency available for desired operation

---------
### InvalidCurrency
A user has tried to create a pool with an invalid currency

---------
### InvalidJuniorTranche
Attempted to create a pool without a junior tranche

---------
### InvalidSolution
The provided solution is not a valid one

---------
### InvalidTrancheId
Invalid TrancheId passed. In most cases out-of-bound index

---------
### InvalidTrancheSeniority
Invalid tranche seniority value
* seniority MUST be smaller number of tranches
* MUST be increasing per tranche

---------
### InvalidTrancheStructure
Attempted to create a tranche structure where
* non-decreasing interest rate per tranche

---------
### InvalidTrancheUpdate
Pre-requirements for a TrancheUpdate are not met
for example: Tranche changed but not its metadata or vice versa

---------
### MetadataForCurrencyNotFound
No metada for the given currency found

---------
### MinEpochTimeHasNotPassed
Attempted to close an epoch too early

---------
### NAVTooOld
Attempted to close an epoch with an out of date NAV

---------
### NoNAV
The NAV was not available

---------
### NoScheduledUpdate
No update for the pool is scheduled

---------
### NoSolutionAvailable
No solution has yet been provided for the epoch

---------
### NoSuchPool
Attempted an operation on a pool which does not exist

---------
### NotInSubmissionPeriod
Attempted to solve a pool which is not in a submission period

---------
### NotNewBestSubmission
Submitted solution is not an improvement

---------
### PoolInUse
A pool with this ID is already in use

---------
### PoolParameterBoundViolated
One of the runtime-level pool parameter bounds was violated

---------
### RiskBufferViolated
Risk Buffer validation failed

---------
### ScheduledTimeHasNotPassed
Scheduled time for this update is in the future

---------
### TooManyTranches
The requested tranche configuration has too many tranches

---------
### TrancheId
A Tranche ID cannot be converted to an address

---------
### TrancheSymbolNameTooLong
The given tranche symbol name exceeds the length limit

---------
### TrancheTokenNameTooLong
The given tranche token name exceeds the length limit

---------
### UpdatePrerequesitesNotFulfilled
Update cannot be fulfilled yet

---------
### WipedOut
Closing the epoch now would wipe out the junior tranche

---------