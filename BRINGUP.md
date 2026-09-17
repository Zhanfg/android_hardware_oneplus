# OnePlus hardware support for AOSP 17

This branch contains reusable OnePlus hardware support for the independent AOSP 17 ROM.
It is not allowed to introduce a LineageOS framework/runtime dependency into the shipping image.

## Detached donor modules

The following Lineage-specific build entry points are intentionally removed on this branch while their source remains for reference:

- `aidl/livedisplay/Android.bp`
- `aidl/touch/Android.bp`
- `dirac_gef/Android.bp`
- `packages/Doze/Android.bp`
- `packages/KeyHandler/Android.bp`

Reasons include direct dependencies on `vendor.lineage.*`, `org.lineageos.settings.resources`, or Lineage package namespaces.

## Keep / port

Hardware-only pieces without Lineage runtime identity can be retained when compatible, including OnePlus vendor interfaces, fingerprint support, amplifier/audio helpers, Wi-Fi MAC helpers, and other device-specific low-level components.

When a detached feature is restored, it should use a ROM-owned/AOSP-facing package/interface namespace and must pass the project identity audit before entering `PRODUCT_PACKAGES`.
