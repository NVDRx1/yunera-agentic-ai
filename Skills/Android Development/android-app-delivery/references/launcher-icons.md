# Launcher icon design and checks

## Original-reference workflow

1. Identify only high-level visual cues from supplied art: subject, silhouette, palette family, contrast, and intended mood.
2. Deliberately change the geometry and arrangement. A mark such as scales and laurel can be reinterpreted with a new proportion system, stroke treatment, leaf cadence, and field colour.
3. Exclude all watermark text, stock-site logos, raster texture, and recognisable ornamental pathwork. Do not crop out a watermark and retain the rest.
4. Keep the centre mark within the adaptive-icon safe zone. Use a high-contrast foreground and a simple field so mask shapes and small launcher sizes remain legible.

## Android resource checklist

- Foreground drawable: `res/drawable/ic_launcher_foreground.xml`
- Background drawable: `res/drawable/ic_launcher_background.xml`
- Adaptive icon: `res/mipmap-anydpi-v26/ic_launcher.xml`
- Optional Android 13 themed icon: `res/mipmap-anydpi-v33/ic_launcher.xml` with `monochrome`
- Manifest: `android:icon` and `android:roundIcon` both reference the adaptive icon

After assembly, run `aapt2 dump badging <apk>` and confirm `application-icon` names the adaptive icon. Run `aapt2 dump resources <apk>` and confirm both API-qualified adaptive resources and the foreground drawable are included.
