# foroplus-config

Configuración pública de la app **ForoPlus** (cliente Android no oficial de ForoCoches).

Aquí solo hay **datos**, no código: la app se descarga `fc_config.json` al arrancar y lo usa
para dos cosas.

## `fc_config.json`

**Selectores del foro.** Permiten corregir el parseo si ForoCoches cambia su HTML, sin publicar
una versión nueva en Google Play. Si el fichero no está disponible o no es válido, la app sigue
funcionando con la copia que lleva dentro.

**Aviso de actualización.** El bloque `actualizacion` describe la última versión publicada:

```json
"actualizacion": {
  "code": 29,
  "nombre": "1.4.9",
  "bloqueante": false,
  "notas": ["Lo que cambia", "Otra cosa"]
}
```

- `code` — el `versionCode` de la versión publicada. Las notas solo se muestran si coincide con
  la versión que Google Play ofrece; si no coincide, la app avisa sin detallar en vez de enseñar
  notas equivocadas.
- `bloqueante` — si es `true`, el aviso no se puede cerrar sin actualizar. Reservado para
  actualizaciones importantes.
- `notas` — una línea por cambio.

La app se lo descarga al arrancar y cachea la última copia válida.
