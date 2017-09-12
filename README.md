# vy_range_collection

## Fork from range_collection by kseo

A collection library for Range data type. 
This project is heavily inspired by Guava's [Range][range], [RangeSet][rangeset] and [RangeMap][rangemap] classes.
Forked because it seems no more maintained.

[![Build Status](https://travis-ci.org/giorgiofran/vy_range_collection.svg)](https://travis-ci.org/kseo/range_collection)
[![Coverage Status](https://coveralls.io/repos/giorgiofran/vy_range_collection/badge.svg?branch=master&service=github)](https://coveralls.io/github/kseo/range_collection?branch=master)

[range]: https://github.com/google/guava/wiki/RangesExplained
[rangeset]: https://github.com/google/guava/wiki/NewCollectionTypesExplained#rangeset
[rangemap]: https://github.com/google/guava/wiki/NewCollectionTypesExplained#rangemap

## Usage

A simple usage example:

```dart
import 'package:vy_range_collection/vy_range_collection.dart';

main() {
  RangeSet<int> rangeSet = new SkipListRangeSet<int>();
  rangeSet.add(new Range.closed(1, 10));
  print(rangeSet); // {[1, 10]}

  rangeSet.add(new Range.closedOpen(11, 15));
  print(rangeSet); // disconnected range; {[1, 10], [11, 15)}

  rangeSet.add(new Range.closedOpen(15, 20));
  print(rangeSet); // connected range; {[1, 10], [11, 20)}

  rangeSet.add(new Range.openClosed(0, 0));
  print(rangeSet); // empty range; {[1, 10], [11, 20)}

  rangeSet.remove(new Range.open(5, 10));
  print(rangeSet); // splits [1, 10]; {[1, 5], [10, 10], [11, 20)}}
}
```

## Features and bugs

Please file feature requests and bugs at the [issue tracker][tracker].

[tracker]: https://github.com/giorgiofran/vy_range_collection/issues
