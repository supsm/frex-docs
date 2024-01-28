# noisecommon.glsl
****************************************************

frex:shaders/lib/noise/noisecommon.glsl
External MIT noise library - bundled for convenience.
Modifications include:
+ remove the #version header
+ add this comment block
+ move some shared functions to this file
+ use #define for some small functions
*****************************************************
## Preprocessor: `#define mod289(x) (x - floor(x * (1.0 / 289.0)) * 289.0) // Modulo 289 without a division (only multiplications)`
## Preprocessor: `#define mod7(x) (x - floor(x * (1.0 / 7.0)) * 7.0) // Modulo 7 without a division`
## Preprocessor: `#define taylorInvSqrt(r) (1.79284291400159 - 0.85373472095314 * r)`
## `permute(vec4 x)`
 Permutation polynomial: (34x^2 + x) mod 289, ring size 289 = 17*17
 Can't be defined because used recursively
```glsl
{ return mod289((34.0 * x + 1.0) * x); }
```

## `permute(vec3 x)`
```glsl
{ return mod289((34.0 * x + 1.0) * x); }
```

## `permute(float x)`
```glsl
{ return mod289(((x*34.0)+1.0)*x); }
```

