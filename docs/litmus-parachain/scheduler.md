
# Scheduler

---------
## Calls

---------
### cancel
Cancel an anonymously scheduled task.
#### Attributes
| Name | Type |
| -------- | -------- | 
| when | `T::BlockNumber` | 
| index | `u32` | 

#### Python
```python
call = substrate.compose_call(
    'Scheduler', 'cancel', {'index': 'u32', 'when': 'u32'}
)
```

---------
### cancel_named
Cancel a named scheduled task.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `TaskName` | 

#### Python
```python
call = substrate.compose_call(
    'Scheduler', 'cancel_named', {'id': '[u8; 32]'}
)
```

---------
### schedule
Anonymously schedule a task.
#### Attributes
| Name | Type |
| -------- | -------- | 
| when | `T::BlockNumber` | 
| maybe_periodic | `Option<schedule::Period<T::BlockNumber>>` | 
| priority | `schedule::Priority` | 
| call | `Box<<T as Config>::RuntimeCall>` | 

#### Python
```python
call = substrate.compose_call(
    'Scheduler', 'schedule', {
    'call': 'Call',
    'maybe_periodic': (
        None,
        ('u32', 'u32'),
    ),
    'priority': 'u8',
    'when': 'u32',
}
)
```

---------
### schedule_after
Anonymously schedule a task after a delay.

\# &lt;weight&gt;
Same as [`schedule`].
\# &lt;/weight&gt;
#### Attributes
| Name | Type |
| -------- | -------- | 
| after | `T::BlockNumber` | 
| maybe_periodic | `Option<schedule::Period<T::BlockNumber>>` | 
| priority | `schedule::Priority` | 
| call | `Box<<T as Config>::RuntimeCall>` | 

#### Python
```python
call = substrate.compose_call(
    'Scheduler', 'schedule_after', {
    'after': 'u32',
    'call': 'Call',
    'maybe_periodic': (
        None,
        ('u32', 'u32'),
    ),
    'priority': 'u8',
}
)
```

---------
### schedule_named
Schedule a named task.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `TaskName` | 
| when | `T::BlockNumber` | 
| maybe_periodic | `Option<schedule::Period<T::BlockNumber>>` | 
| priority | `schedule::Priority` | 
| call | `Box<<T as Config>::RuntimeCall>` | 

#### Python
```python
call = substrate.compose_call(
    'Scheduler', 'schedule_named', {
    'call': 'Call',
    'id': '[u8; 32]',
    'maybe_periodic': (
        None,
        ('u32', 'u32'),
    ),
    'priority': 'u8',
    'when': 'u32',
}
)
```

---------
### schedule_named_after
Schedule a named task after a delay.

\# &lt;weight&gt;
Same as [`schedule_named`](Self::schedule_named).
\# &lt;/weight&gt;
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `TaskName` | 
| after | `T::BlockNumber` | 
| maybe_periodic | `Option<schedule::Period<T::BlockNumber>>` | 
| priority | `schedule::Priority` | 
| call | `Box<<T as Config>::RuntimeCall>` | 

#### Python
```python
call = substrate.compose_call(
    'Scheduler', 'schedule_named_after', {
    'after': 'u32',
    'call': 'Call',
    'id': '[u8; 32]',
    'maybe_periodic': (
        None,
        ('u32', 'u32'),
    ),
    'priority': 'u8',
}
)
```

---------
## Events

---------
### CallUnavailable
The call for the provided hash was not found so the task has been aborted.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| task | `TaskAddress<T::BlockNumber>` | ```('u32', 'u32')```
| id | `Option<TaskName>` | ```(None, '[u8; 32]')```

---------
### Canceled
Canceled some task.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| when | `T::BlockNumber` | ```u32```
| index | `u32` | ```u32```

---------
### Dispatched
Dispatched some task.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| task | `TaskAddress<T::BlockNumber>` | ```('u32', 'u32')```
| id | `Option<TaskName>` | ```(None, '[u8; 32]')```
| result | `DispatchResult` | ```{'Ok': (), 'Err': {'Other': None, 'CannotLookup': None, 'BadOrigin': None, 'Module': {'index': 'u8', 'error': '[u8; 4]'}, 'ConsumerRemaining': None, 'NoProviders': None, 'TooManyConsumers': None, 'Token': ('NoFunds', 'WouldDie', 'BelowMinimum', 'CannotCreate', 'UnknownAsset', 'Frozen', 'Unsupported'), 'Arithmetic': ('Underflow', 'Overflow', 'DivisionByZero'), 'Transactional': ('LimitReached', 'NoLayer'), 'Exhausted': None, 'Corruption': None, 'Unavailable': None}}```

---------
### PeriodicFailed
The given task was unable to be renewed since the agenda is full at that block.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| task | `TaskAddress<T::BlockNumber>` | ```('u32', 'u32')```
| id | `Option<TaskName>` | ```(None, '[u8; 32]')```

---------
### PermanentlyOverweight
The given task can never be executed since it is overweight.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| task | `TaskAddress<T::BlockNumber>` | ```('u32', 'u32')```
| id | `Option<TaskName>` | ```(None, '[u8; 32]')```

---------
### Scheduled
Scheduled some task.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| when | `T::BlockNumber` | ```u32```
| index | `u32` | ```u32```

---------
## Storage functions

---------
### Agenda
 Items to be executed, indexed by the block number that they should be executed on.

#### Python
```python
result = substrate.query(
    'Scheduler', 'Agenda', ['u32']
)
```

#### Return value
```python
[
    (
        None,
        {
            'call': {
                'Inline': 'Bytes',
                'Legacy': {'hash': 'scale_info::11'},
                'Lookup': {'hash': 'scale_info::11', 'len': 'u32'},
            },
            'maybe_id': (None, '[u8; 32]'),
            'maybe_periodic': (None, ('u32', 'u32')),
            'origin': {
                None: None,
                'Council': {
                    'Member': 'AccountId',
                    'Members': ('u32', 'u32'),
                    '_Phantom': None,
                },
                'CumulusXcm': {'Relay': None, 'SiblingParachain': 'u32'},
                'PolkadotXcm': {
                    'Response': 'scale_info::66',
                    'Xcm': 'scale_info::66',
                },
                'TechnicalCommittee': {
                    'Member': 'AccountId',
                    'Members': ('u32', 'u32'),
                    '_Phantom': None,
                },
                'Void': (),
                'system': {'None': None, 'Root': None, 'Signed': 'AccountId'},
            },
            'priority': 'u8',
        },
    ),
]
```
---------
### IncompleteSince

#### Python
```python
result = substrate.query(
    'Scheduler', 'IncompleteSince', []
)
```

#### Return value
```python
'u32'
```
---------
### Lookup
 Lookup from a name to the block number and index of the task.

 For v3 -&gt; v4 the previously unbounded identities are Blake2-256 hashed to form the v4
 identities.

#### Python
```python
result = substrate.query(
    'Scheduler', 'Lookup', ['[u8; 32]']
)
```

#### Return value
```python
('u32', 'u32')
```
---------
## Constants

---------
### MaxScheduledPerBlock
 The maximum number of scheduled calls in the queue for a single block.
#### Value
```python
50
```
#### Python
```python
constant = substrate.get_constant('Scheduler', 'MaxScheduledPerBlock')
```
---------
### MaximumWeight
 The maximum weight that may be scheduled per block for any dispatchables.
#### Value
```python
{'proof_size': 4194304, 'ref_time': 400000000000}
```
#### Python
```python
constant = substrate.get_constant('Scheduler', 'MaximumWeight')
```
---------
## Errors

---------
### FailedToSchedule
Failed to schedule a call

---------
### Named
Attempt to use a non-named function on a named task.

---------
### NotFound
Cannot find the scheduled call.

---------
### RescheduleNoChange
Reschedule failed because it does not change scheduled time.

---------
### TargetBlockNumberInPast
Given target block number is in the past.

---------