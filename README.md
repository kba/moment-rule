moment-rule
-----------

[![Build Status](https://img.shields.io/travis/kba/moment-rule/master.svg)](https://travis-ci.org/kba/moment-rule)

Extended ranges and date/time rules for [Moment.js](https://momenjs.com).

**Alpha quality, API not stable yet**

## Table of Contents

* [Description](#description)
* ~~[Terminology](#terminology)~~
* ~~[Installation](#installation)~~
* ~~[API](#api)~~
  * ~~[Range](#range)~~
  * ~~[Rule](#rule)~~
  * ~~[Ruleset](#ruleset)~~
* [TODO](#todo)
* [License](#license)


## Description

Building on the power of [Moment.js](https://momentjs.com) and
[moment-range](https://github.com/gf3/moment-range), moment-rule allows the
definition of complex rules to accomodate recurring events, opening hours and
other non-trivial ranges.

Consider a snippet of JSON defining opening hours:

```js
{
    "Mo-Th": "08:00-12:00, 14:00-19:30",
    "Fr:": "15:00-19:00",
    "Sa": "09:30-12:00",
    "So,Holidays": false
    "2016-12-25 - 2017-01-04": false
}
```

These can be expanded to a set of disjunctions of weekday ranges, holiday ranges and time ranges:

```perl
    "(weekday(Mo-Th) AND time(08:00-12:00))" => true
    "(weekday(Mo-Th) AND time(14:00-19:30))" => true
    [...]
    "(weekday(So))" => false
    "(holiday)" => false
```


This module can parse those ranges and answer questions such as:

* Which rules, if any, resulting in what data, is valid on `2016-02-02` at `16:00`?
* Which rules match on tuesdays?
* What time constraints for wednesdays?
* How long will the rule be valid, e.g. will I still reach the place before it closes?

## TODO

- [ ] Documentation
- [ ] Full test coverage
- [ ] Parse rules
- [ ] Search rules for ranges matching criteria

## License

(c) 2016 Konstantin Baierer.

Code released under the [MIT license](./LICENSE).
