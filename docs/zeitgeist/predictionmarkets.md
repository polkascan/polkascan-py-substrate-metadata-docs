
# PredictionMarkets

---------
## Calls

---------
### admin_move_market_to_closed
Allows the `CloseOrigin` to immediately move an open market to closed.

\# Weight

Complexity: `O(n + m)`, where `n` is the number of market ids,
which open at the same time as the specified market,
and `m` is the number of market ids,
which close at the same time as the specified market.
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'admin_move_market_to_closed', {'market_id': 'u128'}
)
```

---------
### admin_move_market_to_resolved
Allows the `ResolveOrigin` to immediately move a reported or disputed
market to resolved.

\# Weight

Complexity: `O(n + m)`, where `n` is the number of market ids
per dispute / report block, m is the number of disputes.
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'admin_move_market_to_resolved', {'market_id': 'u128'}
)
```

---------
### approve_market
Approves a market that is waiting for approval from the
advisory committee.

NOTE: Returns the proposer&\#x27;s bond since the market has been
deemed valid by an advisory committee.

NOTE: Can only be called by the `ApproveOrigin`.

\# Weight

Complexity: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'approve_market', {'market_id': 'u128'}
)
```

---------
### buy_complete_set
Buy a complete set of outcome shares of a market.

The cost of a full set is exactly one unit of the market&\#x27;s base asset. For example,
when calling `buy_complete_set(origin, 1, 2)` on a categorical market with five
different outcomes, the caller pays `2` of the base asset and receives `2` of each of
the five outcome tokens.

NOTE: This is the only way to create new shares of outcome tokens.

\# Weight

Complexity: `O(n)`, where `n` is the number of outcome assets in the market.
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 
| amount | `BalanceOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'buy_complete_set', {
    'amount': 'u128',
    'market_id': 'u128',
}
)
```

---------
### close_trusted_market
Allows the market creator of a trusted market
to immediately move an open market to closed.

\# Weight

Complexity: `O(n + m)`, where `n` is the number of market ids,
which open at the same time as the specified market,
and `m` is the number of market ids,
which close at the same time as the specified market.
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'close_trusted_market', {'market_id': 'u128'}
)
```

---------
### create_market
Creates a market.

\# Weight

Complexity: `O(n)`, where `n` is the number of market ids,
which close at the same time as the specified market.
#### Attributes
| Name | Type |
| -------- | -------- | 
| base_asset | `Asset<MarketIdOf<T>>` | 
| creator_fee | `Perbill` | 
| oracle | `T::AccountId` | 
| period | `MarketPeriod<T::BlockNumber, MomentOf<T>>` | 
| deadlines | `Deadlines<T::BlockNumber>` | 
| metadata | `MultiHash` | 
| creation | `MarketCreation` | 
| market_type | `MarketType` | 
| dispute_mechanism | `Option<MarketDisputeMechanism>` | 
| scoring_rule | `ScoringRule` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'create_market', {
    'base_asset': {
        'CategoricalOutcome': (
            'u128',
            'u16',
        ),
        'CombinatorialOutcome': None,
        'ForeignAsset': 'u32',
        'ParimutuelShare': (
            'u128',
            'u16',
        ),
        'PoolShare': 'u128',
        'ScalarOutcome': (
            'u128',
            ('Long', 'Short'),
        ),
        'Ztg': None,
    },
    'creation': (
        'Permissionless',
        'Advised',
    ),
    'creator_fee': 'u32',
    'deadlines': {
        'dispute_duration': 'u64',
        'grace_period': 'u64',
        'oracle_duration': 'u64',
    },
    'dispute_mechanism': (
        None,
        (
            'Authorized',
            'Court',
            'SimpleDisputes',
        ),
    ),
    'market_type': {
        'Categorical': 'u16',
        'Scalar': {
            'end': 'u128',
            'start': 'u128',
        },
    },
    'metadata': {
        'Sha3_384': '[u8; 50]',
    },
    'oracle': 'AccountId',
    'period': {
        'Block': {
            'end': 'u64',
            'start': 'u64',
        },
        'Timestamp': {
            'end': 'u64',
            'start': 'u64',
        },
    },
    'scoring_rule': (
        'Lmsr',
        'Orderbook',
        'Parimutuel',
    ),
}
)
```

---------
### create_market_and_deploy_pool
Create a market, deploy a LMSR pool, and buy outcome tokens and provide liquidity to the
market.

\# Weight

`O(n)` where `n` is the number of markets which close on the same block, plus the
resources consumed by `DeployPool::create_pool`. In the standard implementation using
neo-swaps, this is `O(m)` where `m` is the number of assets in the market.
#### Attributes
| Name | Type |
| -------- | -------- | 
| base_asset | `Asset<MarketIdOf<T>>` | 
| creator_fee | `Perbill` | 
| oracle | `T::AccountId` | 
| period | `MarketPeriod<T::BlockNumber, MomentOf<T>>` | 
| deadlines | `Deadlines<T::BlockNumber>` | 
| metadata | `MultiHash` | 
| market_type | `MarketType` | 
| dispute_mechanism | `Option<MarketDisputeMechanism>` | 
| amount | `BalanceOf<T>` | 
| spot_prices | `Vec<BalanceOf<T>>` | 
| swap_fee | `BalanceOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'create_market_and_deploy_pool', {
    'amount': 'u128',
    'base_asset': {
        'CategoricalOutcome': (
            'u128',
            'u16',
        ),
        'CombinatorialOutcome': None,
        'ForeignAsset': 'u32',
        'ParimutuelShare': (
            'u128',
            'u16',
        ),
        'PoolShare': 'u128',
        'ScalarOutcome': (
            'u128',
            ('Long', 'Short'),
        ),
        'Ztg': None,
    },
    'creator_fee': 'u32',
    'deadlines': {
        'dispute_duration': 'u64',
        'grace_period': 'u64',
        'oracle_duration': 'u64',
    },
    'dispute_mechanism': (
        None,
        (
            'Authorized',
            'Court',
            'SimpleDisputes',
        ),
    ),
    'market_type': {
        'Categorical': 'u16',
        'Scalar': {
            'end': 'u128',
            'start': 'u128',
        },
    },
    'metadata': {
        'Sha3_384': '[u8; 50]',
    },
    'oracle': 'AccountId',
    'period': {
        'Block': {
            'end': 'u64',
            'start': 'u64',
        },
        'Timestamp': {
            'end': 'u64',
            'start': 'u64',
        },
    },
    'spot_prices': ['u128'],
    'swap_fee': 'u128',
}
)
```

---------
### dispute
Dispute on a market that has been reported or already disputed.

\# Weight

Complexity: `O(n)`, where `n` is the number of outstanding disputes.
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'dispute', {'market_id': 'u128'}
)
```

---------
### dispute_early_close
Allows anyone to dispute a scheduled early close.

The market period is reset to the original (old) period.
A `CloseEarlyDisputeBond` is reserved, which is returned,
if the `CloseMarketsEarlyOrigin` decides to reject
the early close request of the market creator or
if the `CloseMarketsEarlyOrigin` is inactive.
It is slashed, if the `CloseMarketsEarlyOrigin` decides to schedule the early close.

\# Weight

Complexity: `O(n)`, where `n` is the maximum number of market ids
in `MarketIdsPerClose...` either at the old period end or new period end.
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'dispute_early_close', {'market_id': 'u128'}
)
```

---------
### edit_market
Edit a proposed market for which request is made.

Edit can only be made by the creator of the market.

\# Arguments

* `market_id`: The id of the market to edit.
* `oracle`: Oracle to edit market.
* `period`: MarketPeriod to edit market.
* `deadlines`: Deadlines to edit market.
* `metadata`: MultiHash metadata to edit market.
* `market_type`: MarketType to edit market.
* `dispute_mechanism`: MarketDisputeMechanism to edit market.
* `scoring_rule`: ScoringRule to edit market.

\# Weight

Complexity: `O(n)`, where `n` is the number of markets
which end at the same time as the market before the edit.
#### Attributes
| Name | Type |
| -------- | -------- | 
| base_asset | `Asset<MarketIdOf<T>>` | 
| market_id | `MarketIdOf<T>` | 
| oracle | `T::AccountId` | 
| period | `MarketPeriod<T::BlockNumber, MomentOf<T>>` | 
| deadlines | `Deadlines<T::BlockNumber>` | 
| metadata | `MultiHash` | 
| market_type | `MarketType` | 
| dispute_mechanism | `Option<MarketDisputeMechanism>` | 
| scoring_rule | `ScoringRule` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'edit_market', {
    'base_asset': {
        'CategoricalOutcome': (
            'u128',
            'u16',
        ),
        'CombinatorialOutcome': None,
        'ForeignAsset': 'u32',
        'ParimutuelShare': (
            'u128',
            'u16',
        ),
        'PoolShare': 'u128',
        'ScalarOutcome': (
            'u128',
            ('Long', 'Short'),
        ),
        'Ztg': None,
    },
    'deadlines': {
        'dispute_duration': 'u64',
        'grace_period': 'u64',
        'oracle_duration': 'u64',
    },
    'dispute_mechanism': (
        None,
        (
            'Authorized',
            'Court',
            'SimpleDisputes',
        ),
    ),
    'market_id': 'u128',
    'market_type': {
        'Categorical': 'u16',
        'Scalar': {
            'end': 'u128',
            'start': 'u128',
        },
    },
    'metadata': {
        'Sha3_384': '[u8; 50]',
    },
    'oracle': 'AccountId',
    'period': {
        'Block': {
            'end': 'u64',
            'start': 'u64',
        },
        'Timestamp': {
            'end': 'u64',
            'start': 'u64',
        },
    },
    'scoring_rule': (
        'Lmsr',
        'Orderbook',
        'Parimutuel',
    ),
}
)
```

---------
### manually_close_market
Allows the manual closing for &quot;broken&quot; markets.
A market is &quot;broken&quot;, if an unexpected chain stall happened
and the auto close was scheduled during this time.

\# Weight

Complexity: `O(n)`,
and `n` is the number of market ids,
which close at the same time as the specified market.
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'manually_close_market', {'market_id': 'u128'}
)
```

---------
### redeem_shares
Redeems the winning shares of a prediction market.

\# Weight

Complexity: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'redeem_shares', {'market_id': 'u128'}
)
```

---------
### reject_early_close
Allows the `CloseMarketsEarlyOrigin` to reject a scheduled early close.

The market period is reset to the original (old) period
in case it was scheduled before (fat-finger protection).

The disputant gets back the `CloseEarlyDisputeBond`
and receives the market creators `CloseEarlyRequestBond`.

\# Weight

Complexity: `O(n)`, where `n` is the maximum number of market ids
in `MarketIdsPerClose...` either at the old period end or new period end.
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'reject_early_close', {'market_id': 'u128'}
)
```

---------
### reject_market
Rejects a market that is waiting for approval from the advisory committee.

\# Weight

Complexity: `O(n + m)`,
where `n` is the number of market ids,
which open at the same time as the specified market,
and `m` is the number of market ids,
which close at the same time as the specified market.
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 
| reject_reason | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'reject_market', {
    'market_id': 'u128',
    'reject_reason': 'Bytes',
}
)
```

---------
### report
Reports the outcome of a market.

\# Weight

Complexity: `O(n)`, where `n` is the number of market ids,
which reported at the same time as the specified market.
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 
| outcome | `OutcomeReport` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'report', {
    'market_id': 'u128',
    'outcome': {
        'Categorical': 'u16',
        'Scalar': 'u128',
    },
}
)
```

---------
### request_edit
Request an edit to a proposed market.

Can only be called by the `RequestEditOrigin`.

\# Arguments

* `market_id`: The id of the market to edit.
* `edit_reason`: An short record of what needs to be changed.

\# Weight

Complexity: `O(edit_reason.len())`
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 
| edit_reason | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'request_edit', {
    'edit_reason': 'Bytes',
    'market_id': 'u128',
}
)
```

---------
### schedule_early_close
Allows the `CloseMarketsEarlyOrigin` or the market creator to schedule an early close.

The market creator schedules it `now + EarlyClose...Period` in the future.
This is to allow enough time for a potential dispute.
The market creator reserves a `CloseEarlyDisputeBond`, which is returned,
if the `CloseMarketsEarlyOrigin` decides to accept the early close request
or if it is not disputed.
It is slashed, if the early close request is disputed
and the `CloseMarketsEarlyOrigin` decides to reject the early close.
The `CloseMarketsEarlyOrigin` (or root) can schedule it `now + CloseProtection...Period`
in the future. This is to prevent fat finger mistakes.

\# Weight

Complexity: `O(n)`, where `n` is the maximum number of market ids
in `MarketIdsPerClose...` either at the old period end or new period end.
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'schedule_early_close', {'market_id': 'u128'}
)
```

---------
### sell_complete_set
Sells a complete set of outcomes shares for a market.

Each complete set is sold for one unit of the market&\#x27;s base asset.

\# Weight

Complexity: `O(n)`, where `n` is the number of assets for a categorical market.
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 
| amount | `BalanceOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'sell_complete_set', {
    'amount': 'u128',
    'market_id': 'u128',
}
)
```

---------
### start_global_dispute
Start a global dispute, if the market dispute mechanism fails.

\# Arguments

* `market_id`: The identifier of the market.

NOTE:
The returned outcomes of the market dispute mechanism and the report outcome
are added to the global dispute voting outcomes.
The bond of each dispute is the initial vote amount.
#### Attributes
| Name | Type |
| -------- | -------- | 
| market_id | `MarketIdOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PredictionMarkets', 'start_global_dispute', {'market_id': 'u128'}
)
```

---------
## Events

---------
### BadOnInitialize
Custom addition block initialization logic wasn&\#x27;t successful.
#### Attributes
No attributes

---------
### BoughtCompleteSet
A complete set of assets has been bought. \[market_id, amount_per_asset, buyer\]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `MarketIdOf<T>` | ```u128```
| None | `BalanceOf<T>` | ```u128```
| None | `AccountIdOf<T>` | ```AccountId```

---------
### GlobalDisputeStarted
The global dispute was started. \[market_id\]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `MarketIdOf<T>` | ```u128```

---------
### MarketApproved
A market has been approved. \[market_id, new_market_status\]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `MarketIdOf<T>` | ```u128```
| None | `MarketStatus` | ```('Proposed', 'Active', 'Closed', 'Reported', 'Disputed', 'Resolved')```

---------
### MarketClosed
A market has been closed. \[market_id\]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `MarketIdOf<T>` | ```u128```

---------
### MarketCreated
A market has been created. \[market_id, market_account, market\]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `MarketIdOf<T>` | ```u128```
| None | `T::AccountId` | ```AccountId```
| None | `MarketOf<T>` | ```{'base_asset': {'CategoricalOutcome': ('u128', 'u16'), 'ScalarOutcome': ('u128', ('Long', 'Short')), 'CombinatorialOutcome': None, 'PoolShare': 'u128', 'Ztg': None, 'ForeignAsset': 'u32', 'ParimutuelShare': ('u128', 'u16')}, 'creator': 'AccountId', 'creation': ('Permissionless', 'Advised'), 'creator_fee': 'u32', 'oracle': 'AccountId', 'metadata': 'Bytes', 'market_type': {'Categorical': 'u16', 'Scalar': {'start': 'u128', 'end': 'u128'}}, 'period': {'Block': {'start': 'u64', 'end': 'u64'}, 'Timestamp': {'start': 'u64', 'end': 'u64'}}, 'deadlines': {'grace_period': 'u64', 'oracle_duration': 'u64', 'dispute_duration': 'u64'}, 'scoring_rule': ('Lmsr', 'Orderbook', 'Parimutuel'), 'status': ('Proposed', 'Active', 'Closed', 'Reported', 'Disputed', 'Resolved'), 'report': (None, {'at': 'u64', 'by': 'AccountId', 'outcome': {'Categorical': 'u16', 'Scalar': 'u128'}}), 'resolved_outcome': (None, {'Categorical': 'u16', 'Scalar': 'u128'}), 'dispute_mechanism': (None, ('Authorized', 'Court', 'SimpleDisputes')), 'bonds': {'creation': (None, {'who': 'AccountId', 'value': 'u128', 'is_settled': 'bool'}), 'oracle': (None, {'who': 'AccountId', 'value': 'u128', 'is_settled': 'bool'}), 'outsider': (None, {'who': 'AccountId', 'value': 'u128', 'is_settled': 'bool'}), 'dispute': (None, {'who': 'AccountId', 'value': 'u128', 'is_settled': 'bool'}), 'close_request': (None, {'who': 'AccountId', 'value': 'u128', 'is_settled': 'bool'}), 'close_dispute': (None, {'who': 'AccountId', 'value': 'u128', 'is_settled': 'bool'})}, 'early_close': (None, {'old': {'Block': {'start': 'u64', 'end': 'u64'}, 'Timestamp': {'start': 'u64', 'end': 'u64'}}, 'new': {'Block': {'start': 'u64', 'end': 'u64'}, 'Timestamp': {'start': 'u64', 'end': 'u64'}}, 'state': ('ScheduledAsMarketCreator', 'ScheduledAsOther', 'Disputed', 'Rejected')})}```

---------
### MarketDestroyed
A market has been destroyed. \[market_id\]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `MarketIdOf<T>` | ```u128```

---------
### MarketDisputed
A market has been disputed \[market_id, new_market_status, disputant\]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `MarketIdOf<T>` | ```u128```
| None | `MarketStatus` | ```('Proposed', 'Active', 'Closed', 'Reported', 'Disputed', 'Resolved')```
| None | `AccountIdOf<T>` | ```AccountId```

---------
### MarketEarlyCloseDisputed
A market early close request has been disputed.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| market_id | `MarketIdOf<T>` | ```u128```

---------
### MarketEarlyCloseRejected
A market early close request has been rejected.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| market_id | `MarketIdOf<T>` | ```u128```

---------
### MarketEarlyCloseScheduled
A market has been scheduled to close early.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| market_id | `MarketIdOf<T>` | ```u128```
| new_period | `MarketPeriod<T::BlockNumber, MomentOf<T>>` | ```{'Block': {'start': 'u64', 'end': 'u64'}, 'Timestamp': {'start': 'u64', 'end': 'u64'}}```
| state | `EarlyCloseState` | ```('ScheduledAsMarketCreator', 'ScheduledAsOther', 'Disputed', 'Rejected')```

---------
### MarketEdited
A proposed market has been edited by the market creator. \[market_id, new_market\]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `MarketIdOf<T>` | ```u128```
| None | `MarketOf<T>` | ```{'base_asset': {'CategoricalOutcome': ('u128', 'u16'), 'ScalarOutcome': ('u128', ('Long', 'Short')), 'CombinatorialOutcome': None, 'PoolShare': 'u128', 'Ztg': None, 'ForeignAsset': 'u32', 'ParimutuelShare': ('u128', 'u16')}, 'creator': 'AccountId', 'creation': ('Permissionless', 'Advised'), 'creator_fee': 'u32', 'oracle': 'AccountId', 'metadata': 'Bytes', 'market_type': {'Categorical': 'u16', 'Scalar': {'start': 'u128', 'end': 'u128'}}, 'period': {'Block': {'start': 'u64', 'end': 'u64'}, 'Timestamp': {'start': 'u64', 'end': 'u64'}}, 'deadlines': {'grace_period': 'u64', 'oracle_duration': 'u64', 'dispute_duration': 'u64'}, 'scoring_rule': ('Lmsr', 'Orderbook', 'Parimutuel'), 'status': ('Proposed', 'Active', 'Closed', 'Reported', 'Disputed', 'Resolved'), 'report': (None, {'at': 'u64', 'by': 'AccountId', 'outcome': {'Categorical': 'u16', 'Scalar': 'u128'}}), 'resolved_outcome': (None, {'Categorical': 'u16', 'Scalar': 'u128'}), 'dispute_mechanism': (None, ('Authorized', 'Court', 'SimpleDisputes')), 'bonds': {'creation': (None, {'who': 'AccountId', 'value': 'u128', 'is_settled': 'bool'}), 'oracle': (None, {'who': 'AccountId', 'value': 'u128', 'is_settled': 'bool'}), 'outsider': (None, {'who': 'AccountId', 'value': 'u128', 'is_settled': 'bool'}), 'dispute': (None, {'who': 'AccountId', 'value': 'u128', 'is_settled': 'bool'}), 'close_request': (None, {'who': 'AccountId', 'value': 'u128', 'is_settled': 'bool'}), 'close_dispute': (None, {'who': 'AccountId', 'value': 'u128', 'is_settled': 'bool'})}, 'early_close': (None, {'old': {'Block': {'start': 'u64', 'end': 'u64'}, 'Timestamp': {'start': 'u64', 'end': 'u64'}}, 'new': {'Block': {'start': 'u64', 'end': 'u64'}, 'Timestamp': {'start': 'u64', 'end': 'u64'}}, 'state': ('ScheduledAsMarketCreator', 'ScheduledAsOther', 'Disputed', 'Rejected')})}```

---------
### MarketExpired
An advised market has ended before it was approved or rejected. \[market_id\]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `MarketIdOf<T>` | ```u128```

---------
### MarketRejected
A pending market has been rejected as invalid with a reason.
\[market_id, reject_reason\]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `MarketIdOf<T>` | ```u128```
| None | `RejectReason<T>` | ```Bytes```

---------
### MarketReported
A market has been reported on. \[market_id, new_market_status, reported_outcome\]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `MarketIdOf<T>` | ```u128```
| None | `MarketStatus` | ```('Proposed', 'Active', 'Closed', 'Reported', 'Disputed', 'Resolved')```
| None | `ReportOf<T>` | ```{'at': 'u64', 'by': 'AccountId', 'outcome': {'Categorical': 'u16', 'Scalar': 'u128'}}```

---------
### MarketRequestedEdit
A proposed market has been requested edit by advisor. \[market_id, edit_reason\]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `MarketIdOf<T>` | ```u128```
| None | `EditReason<T>` | ```Bytes```

---------
### MarketResolved
A market has been resolved. \[market_id, new_market_status, real_outcome\]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `MarketIdOf<T>` | ```u128```
| None | `MarketStatus` | ```('Proposed', 'Active', 'Closed', 'Reported', 'Disputed', 'Resolved')```
| None | `OutcomeReport` | ```{'Categorical': 'u16', 'Scalar': 'u128'}```

---------
### RecoveryLimitReached
The recovery limit for timestamp based markets was reached due to a prolonged chain stall.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| last_time_frame | `TimeFrame` | ```u64```
| limit_time_frame | `TimeFrame` | ```u64```

---------
### SoldCompleteSet
A complete set of assets has been sold. \[market_id, amount_per_asset, seller\]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `MarketIdOf<T>` | ```u128```
| None | `BalanceOf<T>` | ```u128```
| None | `AccountIdOf<T>` | ```AccountId```

---------
### TokensRedeemed
An amount of winning outcomes have been redeemed.
\[market_id, currency_id, amount_redeemed, payout, who\]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `MarketIdOf<T>` | ```u128```
| None | `Asset<MarketIdOf<T>>` | ```{'CategoricalOutcome': ('u128', 'u16'), 'ScalarOutcome': ('u128', ('Long', 'Short')), 'CombinatorialOutcome': None, 'PoolShare': 'u128', 'Ztg': None, 'ForeignAsset': 'u32', 'ParimutuelShare': ('u128', 'u16')}```
| None | `BalanceOf<T>` | ```u128```
| None | `BalanceOf<T>` | ```u128```
| None | `AccountIdOf<T>` | ```AccountId```

---------
## Storage functions

---------
### LastTimeFrame
 The last time frame that was checked for markets to close.

#### Python
```python
result = substrate.query(
    'PredictionMarkets', 'LastTimeFrame', []
)
```

#### Return value
```python
'u64'
```
---------
### MarketIdsForEdit
 Contains market_ids for which advisor has requested edit.
 Value for given market_id represents the reason for the edit.

#### Python
```python
result = substrate.query(
    'PredictionMarkets', 'MarketIdsForEdit', ['u128']
)
```

#### Return value
```python
'Bytes'
```
---------
### MarketIdsPerCloseBlock
 A mapping of market identifiers to the block their market ends on.

#### Python
```python
result = substrate.query(
    'PredictionMarkets', 'MarketIdsPerCloseBlock', ['u64']
)
```

#### Return value
```python
['u128']
```
---------
### MarketIdsPerCloseTimeFrame
 A mapping of market identifiers to the time frame their market ends in.

#### Python
```python
result = substrate.query(
    'PredictionMarkets', 'MarketIdsPerCloseTimeFrame', ['u64']
)
```

#### Return value
```python
['u128']
```
---------
### MarketIdsPerDisputeBlock
 A mapping of market identifiers to the block they were disputed at.
 A market only ends up here if it was disputed.

#### Python
```python
result = substrate.query(
    'PredictionMarkets', 'MarketIdsPerDisputeBlock', ['u64']
)
```

#### Return value
```python
['u128']
```
---------
### MarketIdsPerOpenBlock

#### Python
```python
result = substrate.query(
    'PredictionMarkets', 'MarketIdsPerOpenBlock', ['u64']
)
```

#### Return value
```python
['u128']
```
---------
### MarketIdsPerOpenTimeFrame

#### Python
```python
result = substrate.query(
    'PredictionMarkets', 'MarketIdsPerOpenTimeFrame', ['u64']
)
```

#### Return value
```python
['u128']
```
---------
### MarketIdsPerReportBlock
 A mapping of market identifiers to the block that they were reported on.

#### Python
```python
result = substrate.query(
    'PredictionMarkets', 'MarketIdsPerReportBlock', ['u64']
)
```

#### Return value
```python
['u128']
```
---------
### MarketsCollectingSubsidy
 Contains a list of all markets that are currently collecting subsidy and the deadline.

#### Python
```python
result = substrate.query(
    'PredictionMarkets', 'MarketsCollectingSubsidy', []
)
```

#### Return value
```python
[
    {
        'market_id': 'u128',
        'period': {
            'Block': {'end': 'u64', 'start': 'u64'},
            'Timestamp': {'end': 'u64', 'start': 'u64'},
        },
    },
]
```
---------
## Constants

---------
### AdvisoryBond
 The base amount of currency that must be bonded for a market approved by the
  advisory committee.
#### Value
```python
2000000000000
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'AdvisoryBond')
```
---------
### AdvisoryBondSlashPercentage
 The percentage of the advisory bond that gets slashed when a market is rejected.
#### Value
```python
0
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'AdvisoryBondSlashPercentage')
```
---------
### CloseEarlyBlockPeriod
 The block time to wait for the market creator
 before the early market close actually happens.
#### Value
```python
36000
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'CloseEarlyBlockPeriod')
```
---------
### CloseEarlyDisputeBond
 The base amount of currency that must be bonded
 by the disputant in order to dispute an early market closure of the market creator.
#### Value
```python
20000000000000
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'CloseEarlyDisputeBond')
```
---------
### CloseEarlyProtectionBlockPeriod
 The block time to wait for the `CloseMarketsEarlyOrigin`
 before the early market close actually happens (fat-finger protection).
#### Value
```python
3600
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'CloseEarlyProtectionBlockPeriod')
```
---------
### CloseEarlyProtectionTimeFramePeriod
 The milliseconds to wait for the `CloseMarketsEarlyOrigin`
 before the early market close actually happens (fat-finger protection).
#### Value
```python
43200000
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'CloseEarlyProtectionTimeFramePeriod')
```
---------
### CloseEarlyRequestBond
 The base amount of currency that must be bonded
 by the market creator in order to schedule an early market closure.
#### Value
```python
20000000000000
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'CloseEarlyRequestBond')
```
---------
### CloseEarlyTimeFramePeriod
 The milliseconds to wait for the market creator
 before the early market close actually happens.
#### Value
```python
432000000
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'CloseEarlyTimeFramePeriod')
```
---------
### DisputeBond
 The base amount of currency that must be bonded in order to create a dispute.
#### Value
```python
20000000000000
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'DisputeBond')
```
---------
### MaxCategories
 The maximum number of categories available for categorical markets.
#### Value
```python
64
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'MaxCategories')
```
---------
### MaxCreatorFee
 A upper bound for the fee that is charged each trade and given to the market creator.
#### Value
```python
10000000
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'MaxCreatorFee')
```
---------
### MaxDisputeDuration
 The maximum number of blocks allowed to be specified as dispute_duration
 in create_market.
#### Value
```python
216000
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'MaxDisputeDuration')
```
---------
### MaxDisputes
 The maximum number of disputes allowed on any single market.
#### Value
```python
1
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'MaxDisputes')
```
---------
### MaxEditReasonLen
 The maximum number of bytes allowed as edit reason.
#### Value
```python
1024
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'MaxEditReasonLen')
```
---------
### MaxGracePeriod
 The maximum number of blocks allowed to be specified as grace_period
 in create_market.
#### Value
```python
2629800
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'MaxGracePeriod')
```
---------
### MaxMarketLifetime
 The maximum allowed duration of a market from creation to market close in blocks.
#### Value
```python
10519200
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'MaxMarketLifetime')
```
---------
### MaxOracleDuration
 The maximum number of blocks allowed to be specified as oracle_duration
 in create_market.
#### Value
```python
100800
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'MaxOracleDuration')
```
---------
### MaxRejectReasonLen
 The maximum length of reject reason string.
#### Value
```python
1024
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'MaxRejectReasonLen')
```
---------
### MinCategories
 The minimum number of categories available for categorical markets.
#### Value
```python
2
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'MinCategories')
```
---------
### MinDisputeDuration
 The minimum number of blocks allowed to be specified as dispute_duration
 in create_market.
#### Value
```python
3600
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'MinDisputeDuration')
```
---------
### MinOracleDuration
 The minimum number of blocks allowed to be specified as oracle_duration
 in create_market.
#### Value
```python
300
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'MinOracleDuration')
```
---------
### OracleBond
 The base amount of currency that must be bonded to ensure the oracle reports
  in a timely manner.
#### Value
```python
2000000000000
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'OracleBond')
```
---------
### OutsiderBond
#### Value
```python
4000000000000
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'OutsiderBond')
```
---------
### PalletId
 The module identifier.
#### Value
```python
'0x7a67652f70726564'
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'PalletId')
```
---------
### ValidityBond
 The base amount of currency that must be bonded for a permissionless market,
 guaranteeing that it will resolve as anything but `Invalid`.
#### Value
```python
10000000000000
```
#### Python
```python
constant = substrate.get_constant('PredictionMarkets', 'ValidityBond')
```
---------
## Errors

---------
### CallerNotMarketCreator
The caller is not the market creator.

---------
### CannotDisputeSameOutcome
Someone is trying to call `dispute` with the same outcome that is currently
registered on-chain.

---------
### DisputeDurationGreaterThanMaxDisputeDuration
Specified dispute_duration is greater than MaxDisputeDuration.

---------
### DisputeDurationSmallerThanMinDisputeDuration
Specified dispute_duration is smaller than MinDisputeDuration.

---------
### EarlyCloseRequestTooLate
The early close would be scheduled after the original market period end.

---------
### EditReasonLengthExceedsMaxEditReasonLen
EditReason&\#x27;s length greater than MaxEditReasonLen.

---------
### EditorNotCreator
Only creator is able to edit the market.

---------
### FeeTooHigh
The fee is too high.

---------
### GlobalDisputeExistsAlready
The start of the global dispute for this market happened already.

---------
### GracePeriodGreaterThanMaxGracePeriod
Specified grace_period is greater than MaxGracePeriod.

---------
### InsufficientFundsInMarketAccount
Market account does not have enough funds to pay out.

---------
### InsufficientShareBalance
Sender does not have enough share balance.

---------
### InvalidBaseAsset
Provided base_asset is not allowed to be used as base_asset.

---------
### InvalidDisputeMechanism
The action requires another market dispute mechanism.

---------
### InvalidEarlyCloseState
This early close state is not valid.

---------
### InvalidMarketPeriod
Market period is faulty (too short, outside of limits)

---------
### InvalidMarketStatus
Catch-all error for invalid market status.

---------
### InvalidMarketType
An invalid market type was found.

---------
### InvalidMultihash
An invalid Hash was included in a multihash parameter.

---------
### InvalidOutcomeRange
The outcome range of the scalar market is invalid.

---------
### InvalidResolutionMechanism
The resolution mechanism resulting from the scoring rule is not supported.

---------
### InvalidScoringRule
An operation is requested that is unsupported for the given scoring rule.

---------
### MarketAlreadyReported
Market is already reported on.

---------
### MarketDisputeMechanismNotFailed
The market dispute mechanism has not failed.

---------
### MarketDurationTooLong
The market duration is longer than allowed.

---------
### MarketEditNotRequested
Market is not requested for edit.

---------
### MarketEditRequestAlreadyInProgress
Market edit request is already in progress.

---------
### MarketIsNotActive
Market was expected to be active.

---------
### MarketIsNotClosed
Market was expected to be closed.

---------
### MarketIsNotCollectingSubsidy
A market in subsidy collection phase was expected.

---------
### MarketIsNotDisputed
A disputed market was expected.

---------
### MarketIsNotProposed
A proposed market was expected.

---------
### MarketIsNotReported
A reported market was expected.

---------
### MarketIsNotResolved
A resolved market was expected.

---------
### MarketIsNotTrusted
The market is not trusted.

---------
### MarketNotInCloseTimeFrameList
The market is not in the close time frame list.

---------
### MarketPeriodEndNotAlreadyReachedYet
The market period end was not already reached yet.

---------
### MarketStartTooLate
The point in time when the market becomes active is too late.

---------
### MarketStartTooSoon
The point in time when the market becomes active is too soon.

---------
### MissingBond
Tried to settle missing bond.

---------
### NoDisputeMechanism
The market has no dispute mechanism.

---------
### NoEarlyCloseScheduled
There is no early close scheduled.

---------
### NoWinningBalance
The user has no winning balance.

---------
### NonZeroDisputePeriodOnTrustedMarket
The dispute duration is positive but the market has dispute period.

---------
### NotAllowedForBlockBasedMarkets
The operation is not allowed for market with a block period.

---------
### NotAllowedToReportYet
Can not report before market.deadlines.grace_period is ended.

---------
### NotEnoughBalance
Sender does not have enough balance to buy shares.

---------
### NotEnoughCategories
The number of categories for a categorical market is too low.

---------
### OnlyAuthorizedCanScheduleEarlyClose
After there was an early close already scheduled,
only the `CloseMarketsEarlyOrigin` can schedule another one.

---------
### OracleDurationGreaterThanMaxOracleDuration
Specified oracle_duration is greater than MaxOracleDuration.

---------
### OracleDurationSmallerThanMinOracleDuration
Specified oracle_duration is smaller than MinOracleDuration.

---------
### OutcomeMismatch
Submitted outcome does not match market type.

---------
### RejectReasonLengthExceedsMaxRejectReasonLen
RejectReason&\#x27;s length greater than MaxRejectReasonLen.

---------
### ReporterNotOracle
The report is not coming from designated oracle.

---------
### RequesterNotCreator
The early market close operation was not requested by the market creator.

---------
### StorageOverflow
It was tried to append an item to storage beyond the boundaries.

---------
### TooManyCategories
Too many categories for a categorical market.

---------
### UnexpectedNoneInPostInfo
The post dispatch should never be None.

---------
### UnregisteredForeignAsset
A foreign asset in not registered in AssetRegistry.

---------
### WeightsLenMustEqualAssetsLen
The weights length has to be equal to the assets length.

---------
### ZeroAmount
An amount was illegally specified as zero.

---------