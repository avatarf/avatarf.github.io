## How to ucs endpoint

The `ucs endpoint` is a centralized system to recive orders from the netpincer and from websites hosted by the ucs company.


## Terminal endpoints


### Get netpincer orders

Path: `/ucs_eps/v1/<token>/orders/<object_id>`
- `token` -- letters, numbers
- `object_id` -- number

Accepted params:
- `count` -- the max number of returned items (max 100!) | integer
- `start_time` -- orders after this time | format 2018-07-29T14:44:30
`end_time` -- orders before this time | format 2018-07-30T14:44:30
