
# AcalaOracle

---------
## Calls

---------
### feed_values
#### Attributes
| Name | Type |
| -------- | -------- | 
| values | `BoundedVec<(T::OracleKey, T::OracleValue), T::MaxFeedValues>` | 

#### Python
```python
call = substrate.compose_call(
    'AcalaOracle', 'feed_values', {
    'values': [
        (
            {
                'DexShare': (
                    {
                        'Erc20': '[u8; 20]',
                        'ForeignAsset': 'u16',
                        'LiquidCrowdloan': 'u32',
                        'StableAssetPoolToken': 'u32',
                        'Token': 'scale_info::54',
                    },
                    {
                        'Erc20': '[u8; 20]',
                        'ForeignAsset': 'u16',
                        'LiquidCrowdloan': 'u32',
                        'StableAssetPoolToken': 'u32',
                        'Token': 'scale_info::54',
                    },
                ),
                'Erc20': '[u8; 20]',
                'ForeignAsset': 'u16',
                'LiquidCrowdloan': 'u32',
                'StableAssetPoolToken': 'u32',
                'Token': (
                    'ACA',
                    'AUSD',
                    'DOT',
                    'LDOT',
                    'TAP',
                    'KAR',
                    'KUSD',
                    'KSM',
                    'LKSM',
                    'TAI',
                    'BNC',
                    'VSKSM',
                    'PHA',
                    'KINT',
                    'KBTC',
                ),
            },
            'u128',
        ),
    ],
}
)
```

---------
## Events

---------
### NewFeedData
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| sender | `T::AccountId` | ```AccountId```
| values | `Vec<(T::OracleKey, T::OracleValue)>` | ```[({'Token': ('ACA', 'AUSD', 'DOT', 'LDOT', 'TAP', 'KAR', 'KUSD', 'KSM', 'LKSM', 'TAI', 'BNC', 'VSKSM', 'PHA', 'KINT', 'KBTC'), 'DexShare': ({'Token': 'scale_info::54', 'Erc20': '[u8; 20]', 'LiquidCrowdloan': 'u32', 'ForeignAsset': 'u16', 'StableAssetPoolToken': 'u32'}, {'Token': 'scale_info::54', 'Erc20': '[u8; 20]', 'LiquidCrowdloan': 'u32', 'ForeignAsset': 'u16', 'StableAssetPoolToken': 'u32'}), 'Erc20': '[u8; 20]', 'StableAssetPoolToken': 'u32', 'LiquidCrowdloan': 'u32', 'ForeignAsset': 'u16'}, 'u128')]```

---------
## Storage functions

---------
### HasDispatched

#### Python
```python
result = substrate.query(
    'AcalaOracle', 'HasDispatched', []
)
```

#### Return value
```python
['AccountId']
```
---------
### RawValues

#### Python
```python
result = substrate.query(
    'AcalaOracle', 'RawValues', [
    'AccountId',
    {
        'DexShare': (
            {
                'Erc20': '[u8; 20]',
                'ForeignAsset': 'u16',
                'LiquidCrowdloan': 'u32',
                'StableAssetPoolToken': 'u32',
                'Token': (
                    'ACA',
                    'AUSD',
                    'DOT',
                    'LDOT',
                    'TAP',
                    'KAR',
                    'KUSD',
                    'KSM',
                    'LKSM',
                    'TAI',
                    'BNC',
                    'VSKSM',
                    'PHA',
                    'KINT',
                    'KBTC',
                ),
            },
            {
                'Erc20': '[u8; 20]',
                'ForeignAsset': 'u16',
                'LiquidCrowdloan': 'u32',
                'StableAssetPoolToken': 'u32',
                'Token': (
                    'ACA',
                    'AUSD',
                    'DOT',
                    'LDOT',
                    'TAP',
                    'KAR',
                    'KUSD',
                    'KSM',
                    'LKSM',
                    'TAI',
                    'BNC',
                    'VSKSM',
                    'PHA',
                    'KINT',
                    'KBTC',
                ),
            },
        ),
        'Erc20': '[u8; 20]',
        'ForeignAsset': 'u16',
        'LiquidCrowdloan': 'u32',
        'StableAssetPoolToken': 'u32',
        'Token': (
            'ACA',
            'AUSD',
            'DOT',
            'LDOT',
            'TAP',
            'KAR',
            'KUSD',
            'KSM',
            'LKSM',
            'TAI',
            'BNC',
            'VSKSM',
            'PHA',
            'KINT',
            'KBTC',
        ),
    },
]
)
```

#### Return value
```python
{'timestamp': 'u64', 'value': 'u128'}
```
---------
### Values

#### Python
```python
result = substrate.query(
    'AcalaOracle', 'Values', [
    {
        'DexShare': (
            {
                'Erc20': '[u8; 20]',
                'ForeignAsset': 'u16',
                'LiquidCrowdloan': 'u32',
                'StableAssetPoolToken': 'u32',
                'Token': (
                    'ACA',
                    'AUSD',
                    'DOT',
                    'LDOT',
                    'TAP',
                    'KAR',
                    'KUSD',
                    'KSM',
                    'LKSM',
                    'TAI',
                    'BNC',
                    'VSKSM',
                    'PHA',
                    'KINT',
                    'KBTC',
                ),
            },
            {
                'Erc20': '[u8; 20]',
                'ForeignAsset': 'u16',
                'LiquidCrowdloan': 'u32',
                'StableAssetPoolToken': 'u32',
                'Token': (
                    'ACA',
                    'AUSD',
                    'DOT',
                    'LDOT',
                    'TAP',
                    'KAR',
                    'KUSD',
                    'KSM',
                    'LKSM',
                    'TAI',
                    'BNC',
                    'VSKSM',
                    'PHA',
                    'KINT',
                    'KBTC',
                ),
            },
        ),
        'Erc20': '[u8; 20]',
        'ForeignAsset': 'u16',
        'LiquidCrowdloan': 'u32',
        'StableAssetPoolToken': 'u32',
        'Token': (
            'ACA',
            'AUSD',
            'DOT',
            'LDOT',
            'TAP',
            'KAR',
            'KUSD',
            'KSM',
            'LKSM',
            'TAI',
            'BNC',
            'VSKSM',
            'PHA',
            'KINT',
            'KBTC',
        ),
    },
]
)
```

#### Return value
```python
{'timestamp': 'u64', 'value': 'u128'}
```
---------
## Constants

---------
### MaxFeedValues
#### Value
```python
10
```
#### Python
```python
constant = substrate.get_constant('AcalaOracle', 'MaxFeedValues')
```
---------
### MaxHasDispatchedSize
#### Value
```python
20
```
#### Python
```python
constant = substrate.get_constant('AcalaOracle', 'MaxHasDispatchedSize')
```
---------
### RootOperatorAccountId
#### Value
```python
'26fFquxSECczieT6xrgG9uvg7LaEc1vj5M6SmX5K6QYN6TGZ'
```
#### Python
```python
constant = substrate.get_constant('AcalaOracle', 'RootOperatorAccountId')
```
---------
## Errors

---------
### AlreadyFeeded

---------
### NoPermission

---------