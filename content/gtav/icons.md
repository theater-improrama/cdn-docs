---
title: 'Icons'
date: 2026-02-27T00:50:13+01:00
---

Wir stellen öffentlich zugängliche Icons für GTA V Fahrzeuge und Klamotten zur Verfügung. Die Icons können frei in eigene Projekte (z.B. Inventar-Systeme, Kleidungsshops oder Fahrzeug-Menüs) eingebunden werden – eine Authentifizierung ist nicht erforderlich.

## Lizenz

Alle von uns bereitgestellten Bilder, Icons, usw. sind lizenziert unter der [CC BY 4.0](/licenses/cc-by-4.0-intl.txt).

Diese Icons entstehen in ehrenamtlicher Arbeit – als gemeinnützige Organisation finanzieren wir uns ausschließlich über Spenden. Damit wir dieses Angebot langfristig aufrechterhalten können, sind wir auf Sichtbarkeit angewiesen. Daher ist eine Namensnennung Voraussetzung für die Nutzung: beispielsweise in einem „Über"-Bereich oder einer Lizenzseite. Sofern eine Projektwebseite vorhanden ist, muss die Nennung dort ebenfalls erfolgen.

Wir bitten darum, zur Namensnennung folgende Angaben zu verwenden:

> **Theater Improrama gUG** – [https://improrama.de/](https://improrama.de/)

## Viewer

{{< icon-viewer >}}

## Nutzung unserer CDN-Icons

Die Gesamtgröße der von uns erstellten Icons beträgt ca. 6 GB und wird in vier Auflösungen bereitgestellt: **64px**, **128px**, **256px** und **512px**. Alle Icons sind im PNG-Format verfügbar.

Die Parameter in den URLs entsprechen den Werten, die auch in den GTA V Native Functions verwendet werden. Eine vollständige Referenz aller Native Functions findest du unter [docs.fivem.net/natives](https://docs.fivem.net/natives/).

### Vollständiger Download

Alle Icons stehen auch als ZIP-Archive zum Offline-Gebrauch zur Verfügung:

| Archiv | Prüfsumme |
|---|---|
| [clothing.zip](https://cdn.improrama.de/assets/gta5/clothing.zip) | [clothing.zip.sha256](https://cdn.improrama.de/assets/gta5/clothing.zip.sha256) |
| [vehicle.zip](https://cdn.improrama.de/assets/gta5/vehicle.zip) | [vehicle.zip.sha256](https://cdn.improrama.de/assets/gta5/vehicle.zip.sha256) |

---

### Klamotten

```
https://cdn.improrama.de/assets/gta5/clothing/icons/{componentId}/{sex}/{drawableId}/{textureId}/{size}x.png
```

GTA V organisiert Kleidung in einem hierarchischen System: Jeder **Component** (z.B. Oberkörper, Hose, Schuhe) enthält mehrere **Drawables** (einzelne Kleidungsstücke), und jedes Drawable kann wiederum mehrere **Textures** haben (Farb- oder Mustervarianten desselben Stücks). Männliche und weibliche Ped-Models (`mp_m_freemode_01` / `mp_f_freemode_01`) haben jeweils eigene Drawables und Texturen.

#### Parameter

| Parameter | Typ | Beschreibung |
|---|---|---|
| `componentId` | `int` | Körperteil-Slot, siehe Tabelle unten. Entspricht dem `componentId`-Parameter von [`SET_PED_COMPONENT_VARIATION`](https://docs.fivem.net/natives/?_0x262B14F48D29DE80). Es werden nicht alle Component IDs unterstützt. |
| `sex` | `int` | `0` = männlich (`mp_m_freemode_01`), `1` = weiblich (`mp_f_freemode_01`) |
| `drawableId` | `int` | Kleidungsstück-Variante innerhalb des Components. Bezeichnet ein konkretes Kleidungsstück (z.B. T-Shirt vs. Jacke). Die Anzahl der verfügbaren Drawables pro Component lässt sich via [`GET_NUMBER_OF_PED_DRAWABLE_VARIATIONS`](https://docs.fivem.net/natives/?_0x27561561732A7842) ermitteln. |
| `textureId` | `int` | Textur-Variante des Drawables – also z.B. eine andere Farbe oder ein anderes Muster desselben Kleidungsstücks. Anzahl abrufbar via [`GET_NUMBER_OF_PED_TEXTURE_VARIATIONS`](https://docs.fivem.net/natives/?_0x8F7156A3142A6BAD). |
| `size` | | `64`, `128`, `256` oder `512` |

#### Component IDs

| ID | Name | Beschreibung |
|---|---|---|
| 1 | Mask | Maske |
| 4 | Leg | Hose |
| 5 | Parachute / Bag | Fallschirm / Rucksack |
| 6 | Shoes | Schuhe |
| 7 | Accessory | Accessoire |
| 8 | Undershirt | Unterhemd |
| 9 | Kevlar | Körperpanzerung |
| 11 | Torso 2 | Oberkörper (sekundär) |

#### Beispiel

```
https://cdn.improrama.de/assets/gta5/clothing/icons/11/0/39/1/256x.png
```

![Beispiel: Klamotten-Icon](https://cdn.improrama.de/assets/gta5/clothing/icons/11/0/39/1/256x.png)

> Männliche Oberkörper (Component `11`), Drawable `39`, Textur `1` in 256px.

---

### Fahrzeuge

```
https://cdn.improrama.de/assets/gta5/vehicle/icons/{hash}/{size}x.png
```

Jedes Fahrzeugmodell in GTA V wird intern durch einen numerischen Hash identifiziert. Dieser Hash wird aus dem Spawn-Namen des Fahrzeugs berechnet und dient als eindeutiger Schlüssel in der URL.

#### Parameter

| Parameter | Typ | Beschreibung |
|---|---|---|
| `hash` | `uint` | Fahrzeug-Model-Hash. Kann im Code via [`GET_HASH_KEY`](https://docs.fivem.net/natives/?_0xD24D37CC275948CC) aus dem Spawn-Namen des Fahrzeugs (z.B. `adder`, `zentorno`) berechnet werden. Alternativ lässt sich der Hash eines Fahrzeugs, in dem der Spieler gerade sitzt, mit [`GET_ENTITY_MODEL`](https://docs.fivem.net/natives/?_0x9F47B058362C84B5) auslesen. |
| `size` | | `64`, `128`, `256` oder `512` |

#### Beispiel

```
https://cdn.improrama.de/assets/gta5/vehicle/icons/2891838741/256x.png
```

→ Fahrzeug-Icon für den Hash `2891838741` (`zentorno`) in 256px.

![Beispiel: Fahrzeug-Icon](https://cdn.improrama.de/assets/gta5/vehicle/icons/2891838741/256x.png)

---

{{< callout type="info" >}}
Nutze den [Icon Viewer](../icon-viewer), um Icons direkt im Browser anzusehen.
{{< /callout >}}

{{< callout >}}
Fehlende Icons? Erstelle ein Issue auf [GitHub](https://github.com/theater-improrama/cdn-docs/issues).
{{< /callout >}}
