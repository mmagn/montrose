### 0.9.0 - (2019-03-11)

* enhancements
  * enables support for ActiveRecord 6

* bug fixes
  * Fixes bug for nth day of month when used with yearly interval

* breaking changes
  * using selected with :month with :day as a Hash will now enforce the
    `NthDayOfMonth` recurrence rule
  * drops official support for Ruby 2.1 and 2.2

### 0.8.2 - (2018-08-02)

* bug fixes
  * Fixes use of :at when time of day earlier than :starts

### 0.8.1 - (2018-07-27)

* bug fixes
  * Fixes interval comparisons for secondly, hourly, minutely by zeroing usec
    for recurrence start and end times

### 0.8.0 - (2018-05-29)

* enhancements
  * Parsing the `:at` option now initializes recurrence by the hour-minute-second
  * Support activesupport-5.2 (by @zokioki)
  * Support ruby-2.5
  * Support YAML.safe_load for Recurrence#to_yaml

### 0.7.0 - (2017-09-18)

* enhancements
  * Adds the :exclude_end option can be used to determine whether :until value
    is included in the recurrence. Mimics the API to Ruby's Range.
  * Support activesupport-5.1 (by @fauxparse)
  * Support ruby-2.4

* bug fixes
  * Recurrence#to_json accepts arguments for JSON.dump

* breaking changes
  * Previously, the :between option served as a shorthand for :starts to :until.
    Now, when both :starts and :between are provided, the recurrence will behave
as if anchored by the given :starts option, but filtered through the given
:betweeen option.
  * The :exclude_end option changes the default behavior of :until--when the
    timestamp of the interval matches the :until timestamp, it will be included
by default unless the :exclude_end option is set to true.

### 0.6.0 - (2017-01-05)

* enhancements
  * Alias `every` to `frequency`
  * Handle JSON and hashes in Recurrence serialization
  * Handle blank and nil objects in Recurrence deserialization

### 0.5.0 - (2016-11-23)

* enhancements
  * Adds `Recurrence#include?`
  * Improved documentation

### 0.4.3 - (2016-11-20)

* enhancements
  * Add CI support for ActiveSupport 4.1, 4.2, 5.0 (by @phlipper)

### 0.4.2 - (2016-07-27)

* bug fixes
  * Respect `ActiveSupport::TimeWithZone` objects for casting time objects (by
    @tconst)

### 0.4.1 - (2016-07-04)

* enhancements
  * Support `Montrose.every(:second)`

* bug fixes
  * Ensure `ActiveSupport::Duration` parts are used; fixes 'every 30 days' bug

### 0.4.0 - (2016-04-20)

* enhancements
  * Respect configured time zone by using `Time.current` from `ActiveSupport`
  * Adds `Montrose::Recurrence#to_json` method
  * Additional tests for utils methods (by @AlexWheeler)

### 0.3.0 - (2016-02-19)

* enhancements
  * Adds `:except` option and chainable method to filter timestamps by date (by
    @thewatts)
* bug fixes
  * Fix recurrences when specifying both `:starts` and `:at` by treating
    `:starts` value like a date
  * Respect recurrence rules using multiple `:at` values
  * Using `Montrose.r` without any arguments no longer throws `ArgumentError`

### 0.2.2 - 2016-02-08

* bug fixes
  * Handle `Hash` in `Montrose::Chainable` methods that support varargs
* enhancements
  * Adds `Montrose.r` method for starting a new recurrence
  * Adds `Chainable` alias methods including `#starts`, `#until`, `#repeat`
  * README updates (by @thegcat)

### 0.2.1 - 2016-02-03

* bug fixes
  * Handle `nil` in `Montrose::Options` constructor

### 0.2.0 - 2016-02-03

* enhancements
  * extend `Montrose::Schedule` api for building and adding recurrences
  * add more details to chainable docs
  * merge default options at enumeration time for more consistent serialization

### 0.1.1 - 2016-25-01

* bug fixes
  * add missing `require "forwardable"`
* enhancements
  * add better `#inspect` methods in `Recurrence` and `Options`
  * use refinement to refactor Options internal arg merging
  * support ruby 2.3.0 in travis builds

### 0.1.0 - 2016-18-01

* initial release
