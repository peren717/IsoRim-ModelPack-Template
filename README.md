# IsoRim Waylith model pack template

A minimal model pack for [IsoRim Waylith](https://github.com/peren717/IsoRim-1.7) (RimWorld 1.7): XML and `.obj` files that
give things their own 3D model in IsoRim's 3D view. No code of your own.

**Guide:** [Docs/ModelPacks.md](https://github.com/peren717/IsoRim-1.7/blob/master/Docs/ModelPacks.md) in IsoRim (axes,
scale, origin, materials, the ModelDef fields, version gating, pitfalls, and the dev-mode model binder that writes packs
like this one for you).

## What is in it

| Path | |
|---|---|
| `About/About.xml` | Your mod. Replace `YourName` / `MyModelPack`; add the mod whose things you model as a dependency |
| `Defs/MyPack_Models.xml` | Two samples: a building (`AncientMechGestatorTank`, 2x2) and an item (`AIPersonaCore`), WITHOUT `<thingDef>` |
| `Patches/MyPack_Models.xml` | Adds each `<thingDef>` through `IsoRimPackGate.PatchOperation_IfIsoRimApi` when IsoRim's Api is new enough |
| `Models/` | `mypack_tank.obj`, `mypack_case.obj` and their materials `mypack.mtl` (red marker = the model's north side) |
| `1.7/Assemblies/IsoRimPackGate.dll` | The patch class. Every pack ships the same file; it works without IsoRim (does nothing) |
| `Source/PackGate/` | Its source, only needed to rebuild it |

## Make it yours

1. Rename the pack in `About/About.xml`.
2. Put your `.obj` and `.mtl` files in `Models/`, one `IsoRim.ModelDef` per thing in `Defs/` (defName `R3D_<YourPack>_<thing>`),
   one `PatchOperationAdd` per thing in `Patches/`. Delete the samples.
3. Load the pack after IsoRim and after the mod whose things you model.

Quicker: in game with development mode on, Debug actions → **IsoRim → Model binder...** on a building or item, pick your
`.obj`, place it live, and **Export**: it writes the Defs, Patches and Models of a pack like this one.
