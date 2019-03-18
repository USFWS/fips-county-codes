A tool for looking up FIPS county codes.

## Example

```
const fips = require('fips-county-codes');

fips.get({
  "state": "AL",
  "county": "Chambers"
});

// 017

fips.get({
  "fips": "017"
});

// {
//   "state": "AL",
//   "county": "Chambers"
// }
```

## Options

| Option | Description                  | type   |
| ------ | ---------------------------- | ------ |
| fips   | A three digit fips code      | string |
| state  | Two letter state abbrviation | string |
| county | County name                  | string |

## Source

[U.S. Census Bureau](https://www.census.gov/geo/reference/codes/cou.html) (2010). Here is the [CSV data](https://www2.census.gov/geo/docs/reference/codes/files/national_county.txt) for all of the United States.

## Data manipulation

The only change I made to the dataset was to include a header row in the CSV file; I use [csv2json](https://www.npmjs.com/package/csv2json) to convert dataset to JSON. **I did not attempt to change types. All fields are of type `String`.**

## Field descriptions

| Field Name | Field Description | Example        |
| ---------- | ----------------- | -------------- |
| state      | State Postal Code | FL             |
| statefp    | State FIPS Code   | 12             |
| countyfp   | County FIPS Code  | 011            |
| countyname | County name       | Broward County |
| classfp    | FIPS Class Code   | H1             |

### FIPS Class Codes

- H1:  identifies an active county or statistically equivalent entity that does not qualify under subclass C7 or H6.
- H4:  identifies a legally defined inactive or nonfunctioning county or statistically equivalent entity that does not qualify under subclass H6.
- H5:  identifies census areas in Alaska, a statistical county equivalent entity.
- H6:  identifies a county or statistically equivalent entity that is areally coextensive or governmentally consolidated with an incorporated place, part of an incorporated place, or a consolidated city.
- C7:  identifies an incorporated place that is an independent city; that is, it also serves as a county equivalent because it is not part of any county, and a minor civil division (MCD) equivalent because it is not part of any MCD.

## Browser support

All modern browsers. For IE11 support, you must polyfill `Array.find()`.

## Tests

`npm test`

## License

MIT