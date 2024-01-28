# accessibility.h
**************************************************************

  Specifies the variables available in the FREX shader API
  to describe accessibility preferences that affect visuals.


  See FREX Shader API.md for license and general informaiton.
**************************************************************
## `const float frx_fovEffects `

  FOV Effects.


  Defaults to 1.0 when unavailable.

## `const float frx_distortionEffects `

  Distortion Effects.


  Defaults to 1.0 when unavailable.

## `const int frx_hideLightningFlashes `

  Hide Lightning Flashes. 1 when ON, 0 otherwise.


  This setting's effect is precomputed in frx_skyFlashStrength.
  No need to multiply it manually to that variable.


  Defaults to 0 when unavailable.

## `const float frx_darknessPulsing `

  Darkness Pulsing.


  This setting's effect is precomputed in frx_darknessEffectFactor.
  No need to blend it manually to that variable.


  Defaults to 1.0 when unavailable.

## `const int frx_highContrast `

  High Contrast. 1 when ON, 0 otherwise.


  Defaults to 0 when unavailable.

## `const float frx_damageTilt `

  Damage Tilt.


  Defaults to 1.0 when unavailable.

## `const float frx_glintStrength `

  Glint Strength.


  Defaults to 1.0 when unavailable.

## `const float frx_glintSpeed `

  Glint Speed.


  Defaults to 1.0 when unavailable.

