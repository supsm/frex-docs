# color.glsl
****************************************************

frex:shaders/lib/color.glsl
Common color processing functions.
Portions taken from Wisdom Shaders by Cheng (Bob) Cao, Apache 2.0 license
https://github.com/bobcao3/Wisdom-Shaders
*****************************************************
## Preprocessor: `#define FRX_GAMMA 2.4`
## Preprocessor: `#define FRX_INVERSE_GAMMA (1.0 / FRX_GAMMA)`
## `frx_fromGamma(vec4 c)`
```glsl
{
	return pow(c, vec4(FRX_GAMMA));
}
```

## `frx_toGamma(vec4 c)`
```glsl
{
	return pow(c, vec4(FRX_INVERSE_GAMMA));
}
```

## `frx_fromGamma(vec3 c)`
```glsl
{
	return pow(c, vec3(FRX_GAMMA));
}
```

## `frx_toGamma(vec3 c)`
```glsl
{
	return pow(c, vec3(FRX_INVERSE_GAMMA));
}
```

## `const mat3 FRX_ACES_INPUT_MATRIX = mat3 ( vec3 ( 0 . 5 9 7 1 9 , 0 . 0 7 6 0 0 , 0 . 0 2 8 4 0 ) , vec3 ( 0 . 3 5 4 5 8 , 0 . 9 0 8 3 4 , 0 . 1 3 3 8 3 ) , vec3 ( 0 . 0 4 8 2 3 , 0 . 0 1 5 6 6 , 0 . 8 3 7 7 7 ) ) `
float frx_luma(vec3 c) {
    return dot(c, vec3(0.2126, 0.7152, 0.0722));
}
## `const mat3 FRX_ACES_OUTPUT_MATRIX = mat3 ( vec3 ( 1 . 6 0 4 7 5 , -0 . 1 0 2 0 8 , -0 . 0 0 3 2 7 ) , vec3 ( -0 . 5 3 1 0 8 , 1 . 1 0 8 1 3 , -0 . 0 7 2 7 6 ) , vec3 ( -0 . 0 7 3 6 7 , -0 . 0 0 6 0 5 , 1 . 0 7 6 0 2 ) ) `
 ODT_SAT => XYZ => D60_2_D65 => sRGB
## `FRX_RRT_AND_ODTF_FIT(vec3 v)`
```glsl
{
	vec3 a = v * (v + 0.0245786f) - 0.000090537f;
	vec3 b = v * (0.983729f * v + 0.4329510f) + 0.238081f;
	return a / b;
}
```

## `frx_toneMap(vec3 color)`
```glsl
{
	color = FRX_ACES_INPUT_MATRIX * color;
	color = FRX_RRT_AND_ODTF_FIT(color);
	return FRX_ACES_OUTPUT_MATRIX * color;
}
```

