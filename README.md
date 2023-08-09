# Animal names

> Dataset of 100 common animal names

## Data

### `animals-common`

[![](https://img.shields.io/badge/animal_names-138-brightgreen.svg?style=flat-square)](animals-common.txt)

Handpicked dataset of animals you will know (western perspective).

See: [`txt`](animals-common.txt), [`json`](animals-common.json)

### `animals-unfiltered`

[![](https://img.shields.io/badge/animal_names-1139-brightgreen.svg?style=flat-square)](animals-unfiltered.txt)

Unfiltered list of animal names that include:

- country name prefixed animals (like African ..)
- adjective prefixed animals (like Red .., Bush ..)
- some latin names

See: [`txt`](animals-unfiltered.txt), [`json`](animals-unfiltered.json)

## Source

The orignal data source is: [JustOscarJ1/animals](https://github.com/JustOscarJ1/animals)

## See also

More datasets:

- [nationalities](https://github.com/jneidel/nationalities)
- [job titles](https://github.com/jneidel/job-titles)

## Transforms

These are the transfomations I applied to the data (along with some manual picking out.)

To get `animals-unfiltered.txt` from the source file:

```sh
<SOURCE sed -E "s|,.+$||; s|[^-]+-\S||" | sort | uniq | grep -Fv unidentified | grep -Fv . | grep -ve " .*us$" -e " .*is$" -e "^[a-z]" -e "Western" -e "Southern" -e "Northern" -e "Eastern" -e "^$"
```

From `txt` to `json`:

```sh
<FILE.txt awk -F@ 'BEGIN { print "[" } { print "  \""$1"\"," }' | sed '$ s/,$/\n]/'
```
