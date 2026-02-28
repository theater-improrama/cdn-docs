---
title: 'Icons'
date: 2026-02-27T00:50:13+01:00
---

We provide publicly accessible icons for GTA V vehicles and clothing. The icons can be freely integrated into your own projects (e.g. inventory systems, clothing shops or vehicle menus) – no authentication is required.

## License

All images, icons, etc. provided by us are licensed under [CC BY 4.0](/licenses/cc-by-4.0-intl.txt).

These icons are created through volunteer work – as a non-profit organization, we are funded exclusively through donations. In order to sustain this offering long-term, we depend on visibility. Therefore, attribution is a requirement for usage: for example in an "About" section or a license page. If a project website exists, attribution should be included there as well.

We kindly ask you to use the following details for attribution:

> **Theater Improrama gUG** – [https://improrama.de/](https://improrama.de/)

## Viewer

{{< icon-viewer >}}

## Using our CDN Icons

The total size of the icons we provide is approximately 6 GB, available in four resolutions: **64px**, **128px**, **256px** and **512px**. All icons are provided in PNG format.

The URL parameters correspond to the values used in the GTA V Native Functions. A complete reference of all Native Functions can be found at [docs.fivem.net/natives](https://docs.fivem.net/natives/).

### Full Download

All icons are also available as ZIP archives for offline use:

| Archive | Checksum |
|---|---|
| [clothing.zip](https://cdn.improrama.de/assets/gta5/clothing.zip) | [clothing.zip.sha256](https://cdn.improrama.de/assets/gta5/clothing.zip.sha256) |
| [vehicle.zip](https://cdn.improrama.de/assets/gta5/vehicle.zip) | [vehicle.zip.sha256](https://cdn.improrama.de/assets/gta5/vehicle.zip.sha256) |

---

### Clothing

```
https://cdn.improrama.de/assets/gta5/clothing/icons/{componentId}/{sex}/{drawableId}/{textureId}/{size}x.png
```

GTA V organizes clothing in a hierarchical system: each **Component** (e.g. upper body, pants, shoes) contains multiple **Drawables** (individual clothing items), and each Drawable can have multiple **Textures** (color or pattern variants of the same item). Male and female ped models (`mp_m_freemode_01` / `mp_f_freemode_01`) each have their own set of Drawables and Textures.

#### Parameters

| Parameter | Type | Description |
|---|---|---|
| `componentId` | `int` | Body part slot, see table below. Corresponds to the `componentId` parameter of [`SET_PED_COMPONENT_VARIATION`](https://docs.fivem.net/natives/?_0x262B14F48D29DE80). Not all component IDs are supported. |
| `sex` | `int` | `0` = male (`mp_m_freemode_01`), `1` = female (`mp_f_freemode_01`) |
| `drawableId` | `int` | Clothing item variant within the component. Refers to a specific clothing item (e.g. T-shirt vs. jacket). The number of available Drawables per component can be retrieved via [`GET_NUMBER_OF_PED_DRAWABLE_VARIATIONS`](https://docs.fivem.net/natives/?_0x27561561732A7842). |
| `textureId` | `int` | Texture variant of the Drawable – e.g. a different color or pattern of the same clothing item. The count can be retrieved via [`GET_NUMBER_OF_PED_TEXTURE_VARIATIONS`](https://docs.fivem.net/natives/?_0x8F7156A3142A6BAD). |
| `size` | | `64`, `128`, `256` or `512` |

#### Component IDs

| ID | Name | Description |
|---|---|---|
| 1 | Mask | Mask |
| 4 | Leg | Pants |
| 5 | Parachute / Bag | Parachute / Backpack |
| 6 | Shoes | Shoes |
| 7 | Accessory | Accessory |
| 8 | Undershirt | Undershirt |
| 9 | Kevlar | Body armor |
| 11 | Torso 2 | Upper body (secondary) |

#### Example

```
https://cdn.improrama.de/assets/gta5/clothing/icons/11/0/39/1/256x.png
```

→ Male torso 2 (Component `11`), Drawable `39`, Texture `1` at 256px.

![Example: Clothing icon](https://cdn.improrama.de/assets/gta5/clothing/icons/11/0/39/1/256x.png)

---

### Vehicles

```
https://cdn.improrama.de/assets/gta5/vehicle/icons/{hash}/{size}x.png
```

Each vehicle model in GTA V is internally identified by a numeric hash. This hash is computed from the vehicle's spawn name and serves as a unique key in the URL. The hash is an **unsigned 32-bit integer** (`uint32`). Native functions like `GET_HASH_KEY` may return a signed value (`int32`) in some environments – this must be converted to `uint32` before use in the URL (e.g. `hash >>> 0` in JavaScript).

#### Parameters

| Parameter | Type | Description |
|---|---|---|
| `hash` | `uint` | Vehicle model hash. Can be computed in code via [`GET_HASH_KEY`](https://docs.fivem.net/natives/?_0xD24D37CC275948CC) using the vehicle's spawn name (e.g. `adder`, `zentorno`). Alternatively, the hash of a vehicle the player is currently sitting in can be retrieved with [`GET_ENTITY_MODEL`](https://docs.fivem.net/natives/?_0x9F47B058362C84B5). |
| `size` | | `64`, `128`, `256` or `512` |

#### Example

```
https://cdn.improrama.de/assets/gta5/vehicle/icons/2891838741/256x.png
```

→ Vehicle icon for hash `2891838741` (`zentorno`) at 256px.

![Example: Vehicle icon](https://cdn.improrama.de/assets/gta5/vehicle/icons/2891838741/256x.png)

---

{{< callout type="info" >}}
Use the [Icon Viewer](../icon-viewer) to preview icons directly in your browser.
{{< /callout >}}

{{< callout >}}
Missing icons? Create an issue on [GitHub](https://github.com/theater-improrama/cdn-docs/issues).
{{< /callout >}}
