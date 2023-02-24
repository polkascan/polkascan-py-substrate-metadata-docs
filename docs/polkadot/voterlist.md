
# VoterList

---------
## Calls

---------
### put_in_front_of
Move the caller&\#x27;s Id directly in front of `lighter`.

The dispatch origin for this call must be _Signed_ and can only be called by the Id of
the account going in front of `lighter`.

Only works if
- both nodes are within the same bag,
- and `origin` has a greater `Score` than `lighter`.
#### Attributes
| Name | Type |
| -------- | -------- | 
| lighter | `AccountIdLookupOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'VoterList', 'put_in_front_of', {
    'lighter': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
### rebag
Declare that some `dislocated` account has, through rewards or penalties, sufficiently
changed its score that it should properly fall into a different bag than its current
one.

Anyone can call this function about any potentially dislocated account.

Will always update the stored score of `dislocated` to the correct score, based on
`ScoreProvider`.

If `dislocated` does not exists, it returns an error.
#### Attributes
| Name | Type |
| -------- | -------- | 
| dislocated | `AccountIdLookupOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'VoterList', 'rebag', {
    'dislocated': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
## Events

---------
### Rebagged
Moved an account from one bag to another.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| who | `T::AccountId` | ```AccountId```
| from | `T::Score` | ```u64```
| to | `T::Score` | ```u64```

---------
### ScoreUpdated
Updated the score of some account to the given amount.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| who | `T::AccountId` | ```AccountId```
| new_score | `T::Score` | ```u64```

---------
## Storage functions

---------
### CounterForListNodes
Counter for the related counted storage map

#### Python
```python
result = substrate.query(
    'VoterList', 'CounterForListNodes', []
)
```

#### Return value
```python
'u32'
```
---------
### ListBags
 A bag stored in storage.

 Stores a `Bag` struct, which stores head and tail pointers to itself.

#### Python
```python
result = substrate.query(
    'VoterList', 'ListBags', ['u64']
)
```

#### Return value
```python
{'head': (None, 'AccountId'), 'tail': (None, 'AccountId')}
```
---------
### ListNodes
 A single node, within some bag.

 Nodes store links forward and back within their respective bags.

#### Python
```python
result = substrate.query(
    'VoterList', 'ListNodes', ['AccountId']
)
```

#### Return value
```python
{
    'bag_upper': 'u64',
    'id': 'AccountId',
    'next': (None, 'AccountId'),
    'prev': (None, 'AccountId'),
    'score': 'u64',
}
```
---------
## Constants

---------
### BagThresholds
 The list of thresholds separating the various bags.

 Ids are separated into unsorted bags according to their score. This specifies the
 thresholds separating the bags. An id&#x27;s bag is the largest bag for which the id&#x27;s score
 is less than or equal to its upper threshold.

 When ids are iterated, higher bags are iterated completely before lower bags. This means
 that iteration is _semi-sorted_: ids of higher score tend to come before ids of lower
 score, but peer ids within a particular bag are sorted in insertion order.

 \# Expressing the constant

 This constant must be sorted in strictly increasing order. Duplicate items are not
 permitted.

 There is an implied upper limit of `Score::MAX`; that value does not need to be
 specified within the bag. For any two threshold lists, if one ends with
 `Score::MAX`, the other one does not, and they are otherwise equal, the two
 lists will behave identically.

 \# Calculation

 It is recommended to generate the set of thresholds in a geometric series, such that
 there exists some constant ratio such that `threshold[k + 1] == (threshold[k] *
 constant_ratio).max(threshold[k] + 1)` for all `k`.

 The helpers in the `/utils/frame/generate-bags` module can simplify this calculation.

 \# Examples

 - If `BagThresholds::get().is_empty()`, then all ids are put into the same bag, and
   iteration is strictly in insertion order.
 - If `BagThresholds::get().len() == 64`, and the thresholds are determined according to
   the procedure given above, then the constant ratio is equal to 2.
 - If `BagThresholds::get().len() == 200`, and the thresholds are determined according to
   the procedure given above, then the constant ratio is approximately equal to 1.248.
 - If the threshold list begins `[1, 2, 3, ...]`, then an id with score 0 or 1 will fall
   into bag 0, an id with score 2 will fall into bag 1, etc.

 \# Migration

 In the event that this list ever changes, a copy of the old bags list must be retained.
 With that `List::migrate` can be called, which will perform the appropriate migration.
#### Value
```python
[
    10000000000,
    11131723507,
    12391526824,
    13793905044,
    15354993703,
    17092754435,
    19027181634,
    21180532507,
    23577583160,
    26245913670,
    29216225417,
    32522694326,
    36203364094,
    40300583912,
    44861495728,
    49938576656,
    55590242767,
    61881521217,
    68884798439,
    76680653006,
    85358782760,
    95019036859,
    105772564622,
    117743094401,
    131068357174,
    145901671259,
    162413706368,
    180794447305,
    201255379901,
    224031924337,
    249386143848,
    277609759981,
    309027509097,
    344000878735,
    382932266827,
    426269611626,
    474511545609,
    528213132664,
    587992254562,
    654536720209,
    728612179460,
    811070932564,
    902861736593,
    1005040721687,
    1118783542717,
    1245398906179,
    1386343627960,
    1543239395225,
    1717891425287,
    1912309236147,
    2128729767682,
    2369643119512,
    2637821201686,
    2936349627828,
    3268663217709,
    3638585517729,
    4050372794022,
    4508763004364,
    5019030312352,
    5587045771074,
    6219344874498,
    6923202753807,
    7706717883882,
    8578905263043,
    9549800138161,
    10630573468586,
    11833660457397,
    13172903628838,
    14663712098160,
    16323238866411,
    18170578180087,
    20226985226447,
    22516120692255,
    25064322999817,
    27900911352605,
    31058523077268,
    34573489143434,
    38486252181966,
    42841831811331,
    47690342626046,
    53087570807094,
    59095615988698,
    65783605766662,
    73228491069308,
    81515931542404,
    90741281135191,
    101010685227495,
    112442301921293,
    125167661548718,
    139333180038781,
    155101843555358,
    172655083789626,
    192194865483744,
    213946010204502,
    238158783103893,
    265111772429462,
    295115094915607,
    328513963936552,
    365692661475578,
    407078959611349,
    453149042394237,
    504432984742966,
    561520851400862,
    625069486125324,
    695810069225823,
    774556530406243,
    862214913708369,
    959793802308039,
    1068415923109985,
    1189331064661951,
    1323930457019515,
    1473762779014021,
    1640551977100649,
    1826217100807404,
    2032894383008501,
    2262961819074188,
    2519066527700738,
    2804155208229882,
    3121508044894685,
    3474776448088622,
    3868025066902796,
    4305778556320752,
    4793073637166665,
    5335517047800242,
    5939350054341159,
    6611520261667250,
    7359761551432161,
    8192683066856378,
    9119868268136230,
    10151985198186376,
    11300909227415580,
    12579859689817292,
    14003551982487792,
    15588366878604342,
    17352539001951086,
    19316366631550092,
    21502445250375680,
    23935927525325748,
    26644812709737600,
    29660268798266784,
    33016991140790860,
    36753601641491664,
    40913093136236104,
    45543324061189736,
    50697569104240168,
    56435132174936472,
    62822028745677552,
    69931745415056768,
    77846085432775824,
    86656109914600688,
    96463185576826656,
    107380151045315664,
    119532615158469088,
    133060402202199856,
    148119160705543712,
    164882154307451552,
    183542255300186560,
    204314163786713728,
    227436877985347776,
    253176444104585088,
    281829017427734464,
    313724269827691328,
    349229182918168832,
    388752270484770624,
    432748278778513664,
    481723418752617984,
    536241190443833600,
    596928866512693376,
    664484709541257600,
    739686006129409280,
    823398010228713984,
    916583898614395264,
    1020315853041475584,
    1135787396594579584,
    1264327126171442688,
    1407413999103859968,
    1566694349801462272,
    1744000832209069824,
    1941373506026471680,
    2161083309305266176,
    2405658187494662656,
    2677912179572818944,
    2980977795924034048,
    3318342060496414208,
    3693886631935247360,
    4111932465319354368,
    4577289528371127808,
    5095312144166932480,
    5671960597112134656,
    6313869711009142784,
    7028425188266614784,
    7823848588596424704,
    8709291924949524480,
    9694942965096232960,
    10792142450433898496,
    12013514580722579456,
    13373112266084982784,
    14886578817516689408,
    16571327936291497984,
    18446744073709551615,
]
```
#### Python
```python
constant = substrate.get_constant('VoterList', 'BagThresholds')
```
---------
## Errors

---------
### List
A error in the list interface implementation.

---------