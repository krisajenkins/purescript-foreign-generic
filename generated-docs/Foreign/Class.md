## Module Foreign.Class

This module is provided for backwards-compatibility with the old API.

It is liable to be removed in a future release. 


### Re-exported from Foreign.Generic.Class:

#### `Decode`

``` purescript
class Decode a  where
  decode :: Foreign -> F a
```

The `Decode` class is used to generate decoding functions
of the form `Foreign -> F a` using `generics-rep` deriving.

First, derive `Generic` for your data:

```purescript
import Data.Generic.Rep

data MyType = MyType ...

derive instance genericMyType :: Generic MyType _
```

You can then use the `genericDecode` and `genericDecodeJSON` functions
to decode your foreign/JSON-encoded data.

##### Instances
``` purescript
Decode Void
Decode Unit
Decode Foreign
Decode String
Decode Char
Decode Boolean
Decode Number
Decode Int
(Decode a) => Decode (Identity a)
(Decode a) => Decode (Array a)
(Decode a) => Decode (Maybe a)
(Decode v) => Decode (Object v)
(RowToList r rl, DecodeRecord r rl) => Decode {  | r }
```

#### `Encode`

``` purescript
class Encode a  where
  encode :: a -> Foreign
```

The `Encode` class is used to generate encoding functions
of the form `a -> Foreign` using `generics-rep` deriving.

First, derive `Generic` for your data:

```purescript
import Data.Generic.Rep

data MyType = MyType ...

derive instance genericMyType :: Generic MyType _
```

You can then use the `genericEncode` and `genericEncodeJSON` functions
to encode your data as JSON.

##### Instances
``` purescript
Encode Void
Encode Unit
Encode Foreign
Encode String
Encode Char
Encode Boolean
Encode Number
Encode Int
(Encode a) => Encode (Identity a)
(Encode a) => Encode (Array a)
(Encode a) => Encode (Maybe a)
(Encode v) => Encode (Object v)
(RowToList r rl, EncodeRecord r rl) => Encode {  | r }
```

