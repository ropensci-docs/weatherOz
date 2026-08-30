# Get or Set Up API Keys

Checks first to get key from your .Rprofile or .Renviron (or similar)
file. If it's not found, then it suggests setting it up. Can be used to
check that your key that R is using is the key that you wish to be using
or for guidance in setting up the keys.

## Usage

``` r
get_key(service = c("DPIRD", "SILO", "METNO"))
```

## Arguments

- service:

  (character) The API host i.e., “DPIRD”, “SILO”, or “METNO”.

## Value

A string value with either a DPIRD Weather 2.0 API, SILO and METNO API
key value.

## Details

The suggestion is to use your .Renviron to set up the API keys. However,
if you regularly interact with the APIs outside of R using some other
language you may wish to set these up in your .bashrc, .zshrc, or
config.fish for cross-language use.

## Examples

``` r
if (FALSE) { # \dontrun{
  get_key(service = "DPIRD")
  get_key(service = "SILO")
  get_key(service = "METNO")
} # }
```
