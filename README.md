# node-proc-manager

TUI en bash puro (sin dependencias) para ver y cerrar procesos `node`, `npm`, `npx`, `yarn` o `pnpm` que se quedan colgados en el sistema. Solo usa herramientas ya presentes en macOS: `bash`, `ps`, `lsof`, `awk`, `sed`, `tput`.

## Por qué

Si trabajas con varios proyectos Node en paralelo (Expo, servidores MCP vía `npx`, bundlers, etc.) es fácil acabar con procesos `node`/`npm`/`npx` huérfanos que se quedan corriendo en segundo plano. Esta herramienta los lista todos, muestra de dónde viene cada uno (comando completo, directorio de trabajo, puertos en escucha) y permite cerrarlos sin tener que hacer `ps aux | grep` + `kill` a mano.

## Requisitos

Ninguna dependencia externa: usa `bash`, `ps`, `lsof`, `awk`, `sed` y `tput`, ya presentes en cualquier macOS. Pensado y probado en macOS (bash 3.2 de Apple); en Linux debería funcionar igual si esas herramientas están instaladas.

## Uso

```
./nproc
```

Para tenerlo disponible desde cualquier sitio, cópialo o enlázalo en un directorio de tu `$PATH`, p. ej.:

```
ln -s ~/herramientas/node-proc-manager/nproc /usr/local/bin/nproc
```

## Controles

**Lista principal**
- `↑`/`↓` (o `k`/`j`, estilo vim): moverse
- `Enter` / `→`: ver detalle del proceso seleccionado
- `r`: refrescar
- `q`: salir

**Vista de detalle** (PID, PPID, usuario, tiempo, puertos en escucha, directorio de trabajo, comando completo)
- `k`: cerrar el proceso (SIGTERM), pide confirmación (usa `Shift+K` para la mayúscula)
- `K`: forzar cierre (SIGKILL), pide confirmación
- `←` / `borrar` / `b`: volver a la lista
- `r`: refrescar detalle

## Licencia

MIT, ver [LICENSE](LICENSE).
