# Changes for ring-middleware-format

## 0.3.3a (2014-03-24)
### Features
  - Switch to GSON for json parsing

## 0.3.2 (2013-10-29)
### Bugfixes
  - Removed deprecated usage of cheshire.custom (__Simon Belak__)
  - Added sanity check to make sure the encoding returned by ICU4J can actually be decoded by the JVM

## 0.3.1 (2013-08-19)
### Features
  - Added `:pretty` option to JSON ( _Ian Eure_ )

### Bugfixes
  - Worked around incompatibility with _org.apache.catalina.connector.CoyoteInputStream_. Should work fine in Immutant now. ( _Roman Scherer_ )
  - Do not serialize body if entire response is nil ( _Justin Balthrop_ )

### Other
  - Fallback to looking inside `:headers` if `:content-type` is not defined at the root


## 0.3.0
### Breaking Changes
  - `wrap-format-response` encodes the body with the first format
  (`:json` by default) when unable to find an encoder matching the
  request instead of returning **306** HTTP error code

### Features
  - Added custom error handling
  - Added a `ring.middleware.format` namespace for simplified usage
  - Added a `:formats` param to customize which formats are handled
  - Use `clojure.tools.reader` for safer reading of edn
  - Added `:json-kw` and `:yaml-kw` formats and wrapper to have
    keywords keys in `:params` and `:body-params`

### Bugfixes
  - Use readers in `*data-readers*` for *edn* ( _Roman Scherer_ )

### Other
  - Better formatted doctrings ( _Anthony Grimes_ )

## 0.2.4
### Bugfixes
  - Allow empty request body as per Ring Spec ( _Roman Scherer_ )

## 0.2.3
### Bugfixes
  - Fixed bug with long request bodies when guessing character encoding

## 0.2.2
### Bugfixes
  - Fixed bug with character encoding guessing

## 0.2.1
### Features
  - Tries to guess character encoding when unspecified
  - Easier custom json types ( _Jeremy W. Sherman_ )

### Bugfixes
  - Do not try to merge vectors into :params ( _Ian Eure_ )

## 0.2.0
### Features
  - Chooses format response according to the sort order defined by Accept header ( _Jani Rahkola_ )

### Bugfixes
  - Properly lowercases header according to Ring spec ( _Luke Amdor_ )
  - Safely handles code for clojure format ( _Paul M Bauer_ )
  - safely handle empty request bodies ( _Philip Aston_ )
