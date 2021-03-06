
# Library Functions

--------------------------------------------------------------------------------

## dot()

The dot product can be performed for vector and quaternion types.

```lua
local foo = luacml.vector3(1,2,3)
local bar = luacml.vector3(1,2,3)
print(luacml.dot(foo, bar)) -- prints: 14
```

### Note

Only the following types are supported:

**Vectors**: `vector2`, `vector3`, `vector4`
**Quaternions**: `quat`, `quat_p`, `quat_n`

### Parameters

-   2 vectors of same type.
-   or 2 quaternions of same type.

### Returns

Returns the dot product as a number.

### Errors

-   Missing arguments.
-   Extra arguments.
-   Invalid argument type.

--------------------------------------------------------------------------------

## cross()

The cross product can be performed for the `vector3` type.

```lua
local foo = luacml.vector3(1,2,3)
local bar = luacml.vector3(3,2,1)
print(luacml.cross(foo, bar)) -- prints: vector3:<-4,8,-4>
```
### Note

Only the `vector3` type supports cross product.

### Parameters

-   2 vectors of type `vector3`.

### Returns

Returns the cross product as a `vector3`.

### Errors

-   Missing arguments.
-   Extra arguments.
-   Invalid argument type.

--------------------------------------------------------------------------------

## outer()

The outer product can be performed for vector types.

```lua
local foo = luacml.vector3(1,2,3)
local bar = luacml.vector3(3,2,1)
print(luacml.outer(foo, bar)) -- prints: matrix33:|3,2,1|6,4,2|9,6,3|
```

### Note

Only the following types are supported:

**Vectors**: `vector2`, `vector3`, `vector4`

### Parameters

-   2 vectors of same type.

### Returns

Returns the outer product as a matrix of size *NxN* for vectors of size *N*.

### Errors

-   Missing arguments.
-   Extra arguments.
-   Invalid argument type.

--------------------------------------------------------------------------------

## perp_dot()

The perpendicular dot product can be performed for Vector2.

```lua
local left = luacml.vector2(1,2)
local right = luacml.vector2(3,4)
print(luacml.perp_dot(left, right)) -- prints: -2
```

### Note

Only the `vector2` type is supported.

The result is the dot product of `right` and the perpendicular vector to `left`.

### Parameters

-   2 `vector2`.

### Returns

Returns the perpendicular dot product of the two input vectors.

### Errors

-   Missing arguments.
-   Extra arguments.
-   Invalid argument type.

--------------------------------------------------------------------------------

## triple_product()

The triple product can be performed for three `vector3` objects.

```lua
local A = luacml.vector3(1,2,3)
local B = luacml.vector3(4,5,6)
local C = luacml.vector3(7,8,9)
print(luacml.triple_product(A, B, C)) -- prints: 0
```

### Note

Only the `vector3` type is supported.

The result is equivalent to

```lua
luacml.dot(A, luacml.cross(B,C))
```

### Parameters

-   3 `vector3`.

### Returns

Returns the triple product of the three input vectors.

### Errors

-   Missing arguments.
-   Extra arguments.
-   Invalid argument type.

--------------------------------------------------------------------------------

## unit_cross()

The normalized cross product between two `vector3`.

```lua
local A = luacml.vector3(10,0,0)
local B = luacml.vector3(0,10,0)
print(luacml.unit_cross(A, B)) -- prints: vector3:<0,0,1>
```

### Note

Only the `vector3` type is supported.

The result is equivalent to

```lua
luacml.cross(B,C):normalize()
```

### Parameters

-   2 `vector3`.

### Returns

Returns the normalized cross product of the two input vectors.

### Errors

-   Missing arguments.
-   Extra arguments.
-   Invalid argument type.

--------------------------------------------------------------------------------

## cross_cardinal()

The cross product between a `vector3` and a cardinal axis.

```lua
local foo = luacml.vector3(1,2,3)
-- A cross X
print(luacml.cross_cardinal(A, 1)) -- prints: vector3:<0,3,-2>

-- A cross Y
print(luacml.cross_cardinal(A, 2)) -- prints: vector3:<-3,0,1>

-- A cross Z
print(luacml.cross_cardinal(A, 3)) -- prints: vector3:<2,-1,0>

-- X cross A
print(luacml.cross_cardinal(1, A)) -- prints: vector3:<0,-3,2>

-- Y cross A
print(luacml.cross_cardinal(2, A)) -- prints: vector3:<3,0,-1>

-- Z cross A
print(luacml.cross_cardinal(3, A)) -- prints: vector3:<-2,1,0>
```

### Note

Only the `vector3` type is supported.

Only the indices `1,2,3` are valid for cardinal axes.

### Parameters

-   1 `vector3`, and 1 integer between 1 and 3.
-   or 1 integer between 1 and 3, and 1 `vector3`.

### Returns

Returns the cross product between the input `vector3` and the cardinal axis that
corresponds to the input index.

### Errors

-   Missing arguments.
-   Extra arguments.
-   Invalid argument type.

--------------------------------------------------------------------------------

## length_squared()

The squared length of a vector type.

```lua
local foo = luacml.vector2(1,2)
print(luacml.length_squared(foo)) -- prints: 5

local bar = luacml.vector3(1,2,3)
print(luacml.length_squared(bar)) -- prints: 14

local baz = luacml.vector4(1,2,3,4)
print(luacml.length_squared(baz)) -- prints: 30
```

### Note

This is functionally identical to calling the length_squared() method for each
respective vector type.

```lua
local foo = luacml.vector3(1,2,3)
assert(foo:length_squared() == luacml.length_squared(foo))
```

### Parameters

-   1 `vector2`.
-   or 1 `vector3`.
-   or 1 `vector4`.

### Returns

Returns the squared length (or squared magnitude) of the input vector.

### Errors

-   Missing arguments.
-   Extra arguments.
-   Invalid argument type.

--------------------------------------------------------------------------------

## length()

The length of a vector.

```lua
local foo = luacml.vector2(1,2)
print(luacml.length(foo)) -- prints: sqrt(5)

local bar = luacml.vector3(1,2,3)
print(luacml.length(bar)) -- prints: sqrt(14)

local baz = luacml.vector4(1,2,3,4)
print(luacml.length(baz)) -- prints: sqrt(30)
```

### Note

This is functionally identical to calling the length() method for each
respective vector type.

```lua
local foo = luacml.vector3(1,2,3)
assert(foo:length() == luacml.length(foo))
```

### Parameters

-   1 `vector2`.
-   or 1 `vector3`.
-   or 1 `vector4`.

### Returns

Returns the length (or magnitude) of the input vector.

### Errors

-   Missing arguments.
-   Extra arguments.
-   Invalid argument type.

--------------------------------------------------------------------------------

## normalize()

Get the unit length vector for an the input vector.

```lua
local foo = luacml.vector2(1,2)
print(luacml.normalize(foo)) -- prints: sqrt(5)

local bar = luacml.vector3(1,2,3)
print(luacml.normalize(bar)) -- prints: sqrt(14)

local baz = luacml.vector4(1,2,3,4)
print(luacml.normalize(baz)) -- prints: sqrt(30)
```

### Note

This function is similar to calling the respective `normalize()` functions for
each vector type, however the input vector is left unchanged.

```lua
local foo = luacml.vector3(10,0,0)
local bar = luacml.normalize(foo)
print(foo) -- prints: vector3<10,0,0>
print(bar) -- prints: vector3<1,0,0>
```

Also note that no checking for zero magnitude is performed; As such, possible to
yield vectors with NaN in them.

### Parameters

-   1 `vector2`.
-   or 1 `vector3`.
-   or 1 `vector4`.

### Returns

Returns a new normlized vector from the input vector.

### Errors

-   Missing arguments.
-   Extra arguments.
-   Invalid argument type.

--------------------------------------------------------------------------------

## project_to_hplane()

Project a vector orthographically onto a hyperplane with the input normal.

```lua
local foo = luacml.vector2(1,2)
local n = luacml.vector2(1,0)
print(luacml.project_to_hplane(foo, n)) -- prints: vector2:<0,2>

local bar = luacml.vector3(1,2,3)
local n = luacml.vector3(0,1,0)
print(luacml.project_to_hplane(bar, n)) -- prints: vector3:<1,0,3>

local baz = luacml.vector4(1,2,3,4)
local n = luacml.vector4(0,0,1,0)
print(luacml.project_to_hplane(baz, n)) -- prints: vector4:<1,2,0,4>
```

### Note

This function does not normalize the second argument (input normal).

### Parameters

-   2 `vector2`.
-   or 2 `vector3`.
-   or 2 `vector4`.

### Returns

Returns a new vector projected onto the hyperplane described by the input normal
vector.

### Errors

-   Missing arguments.
-   Extra arguments.
-   Invalid argument type.

--------------------------------------------------------------------------------

## perp()

Get a perpendicular vector to a `vector2`.

```lua
print(luacml.perp(luacml.vector2(1,2)))   -- prints: vector2:<-2,1>
print(luacml.perp(luacml.vector2(-2,1)))  -- prints: vector2:<-1,-2>
print(luacml.perp(luacml.vector2(-1,-2))) -- prints: vector2:<2,-1>
print(luacml.perp(luacml.vector2(2,-1)))  -- prints: vector2:<1,2>
```

### Note

This function is only available for `vector2` types.

The result follows a convention of (-y,x) from the input vector.

### Parameters

-   1 `vector2`.

### Returns

Returns a new `vector2` that is perpendicular to the input vector.

### Errors

-   Missing arguments.
-   Extra arguments.
-   Invalid argument type.

--------------------------------------------------------------------------------

## rotate_vector()

Rotate a `vector3` around a unit `vector3` by a specified angle.

```lua
local foo = luacml.vector3(1,2,3)
local n = lua.vector3(0,1,0)
print(luacml.rotate_vector(foo, n, math.rad(90))) -- prints: vector3:<3,2,-1>
```

### Note

This function is only available for `vector3` types.

The input normal (argument 2) is not normalized by the library.

The input angle (argument 3) is expected to be in **radians**.

### Parameters

-   2 `vector3` and 1 number.

### Returns

Returns a new `vector3` that is the input vector rotated by an angle around an
input normal vector.

### Errors

-   Missing arguments.
-   Extra arguments.
-   Invalid argument type.

--------------------------------------------------------------------------------

## rotate_vector_2D()

Rotate a `vector2` by a specified angle.

```lua
local foo = luacml.vector2(1,2)
print(luacml.rotate_vector_2D(foo, math.rad(90))) -- prints: vector2:<-2,1>
```

### Note

This function is only available for `vector2` types.

The input angle (argument 2) is expected to be in **radians**.

### Parameters

-   1 `vector2` and 1 number.

### Returns

Returns a new `vector2` that is the input vector rotated by an angle.

### Errors

-   Missing arguments.
-   Extra arguments.
-   Invalid argument type.

--------------------------------------------------------------------------------

## random_unit()

Set an input vector to a random unit vector.

Set to a random unit vector:

```lua
local foo = luacml.vector2()
luacml.random_unit(foo)
print(foo, foo:length()) -- prints: vector2:<#,#> 1.0
```

Set to a random unit vector within *theta* radians of *axis*:

```lua
local foo = luacml.vector2()
luacml.random_unit(foo, luacml.vector2(1,0), math.rad(90))
print(foo, foo:length()) -- prints: vector2:<#,#> 1.0
```

### Note

This function is only available for `vector2` and `vector3` types.

The input vector (argument 1) is modified in place.

The input axis vector (argument 2) is expected to be same type as argument 1.

The input angle (argument 3) is expected to be in **radians**.

### Parameters

-   1 `vector2`.
-   or 1 `vector3`.
-   or 2 `vector2` and 1 number.
-   or 2 `vector3` and 1 number.

### Returns

(None)

### Errors

-   Missing arguments.
-   Extra arguments.
-   Invalid argument type.

--------------------------------------------------------------------------------
