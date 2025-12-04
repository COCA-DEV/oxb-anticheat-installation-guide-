# OxB Anticheat - Documentación de Usuario

**Versión:** 1.0.0  
**Autor:** OxbAnticheat  
**Descripción:** El anticheat más avanzado para FiveM

---

## 📋 Tabla de Contenidos

1. [Instalación](#instalación)
2. [Configuración Inicial](#configuración-inicial)
3. [Comandos Disponibles](#comandos-disponibles)
4. [Comandos Indispensables](#comandos-indispensables)
5. [Gestión de Administradores](#gestión-de-administradores)
6. [Sistema Shield](#sistema-shield)
7. [Solución de Problemas](#solución-de-problemas)

---

## 🚀 Instalación

### Paso 1: Colocar el Recurso

1. Coloca la carpeta `anticheat` en tu carpeta `resources` del servidor
2. Asegúrate de que el nombre del recurso sea exactamente `anticheat` (o el nombre que hayas configurado)

### Paso 2: Agregar al server.cfg

Agrega la siguiente línea en tu `server.cfg`:

```cfg
ensure anticheat
```

### Paso 3: Configurar la Key de Licencia

El anticheat se conectará automáticamente al panel de administración usando la key de licencia configurada en el servidor. Asegúrate de tener:

- Una key de licencia válida
- Acceso al panel web de administración
- El servidor debe tener conexión a internet

### Paso 4: Instalar Shield Protection (OBLIGATORIO)

**⚠️ ESTE PASO ES INDISPENSABLE** - Debes ejecutar este comando para proteger todos tus recursos:

```
oxbac:install
```

Este comando:
- Instala automáticamente la protección Shield en todos tus recursos
- Modifica los `fxmanifest.lua` de cada recurso para incluir la protección
- Protege contra exploits y manipulaciones de eventos

**Nota:** Después de ejecutar `oxbac:install`, debes **reiniciar el servidor** para que los cambios surtan efecto.

---

## ⚙️ Configuración Inicial

### Configuración de Administradores

Antes de usar el anticheat, debes configurar al menos un **Owner** (propietario):

1. Conéctate a tu servidor
2. Ejecuta el comando para agregarte como owner:
   ```
   oxbac:addadmin [TU_ID] owner
   ```
   Reemplaza `[TU_ID]` con tu ID de jugador (puedes verlo con `status` en la consola)

### Verificar Configuración

Para verificar que todo está configurado correctamente:

```
oxbac:checkadmin
```

Este comando te mostrará tu rol actual (admin/owner).

---

## 📝 Comandos Disponibles

### Comandos de Instalación y Configuración

#### `oxbac:install`
**Descripción:** Instala la protección Shield en todos los recursos del servidor.  
**Uso:** `oxbac:install`  
**Permisos:** Solo Owners  
**Indispensable:** ✅ **SÍ** - Debe ejecutarse después de la instalación inicial

**Ejemplo:**
```
oxbac:install
```

**Nota:** Después de ejecutar este comando, reinicia el servidor.

---

### Comandos de Gestión de Administradores

#### `oxbac:addadmin`
**Descripción:** Agrega un jugador como administrador u owner.  
**Uso:** `oxbac:addadmin <playerID> <role>`  
**Permisos:** Solo Owners  
**Parámetros:**
- `<playerID>`: ID del jugador en el servidor
- `<role>`: `admin` o `owner`

**Ejemplo:**
```
oxbac:addadmin 1 owner
oxbac:addadmin 2 admin
```

#### `oxbac:removeadmin`
**Descripción:** Elimina un administrador u owner.  
**Uso:** `oxbac:removeadmin <playerID o license>`  
**Permisos:** Solo Owners  
**Parámetros:**
- `<playerID o license>`: ID del jugador o su license identifier

**Ejemplo:**
```
oxbac:removeadmin 1
oxbac:removeadmin license:abc123def456
```

#### `oxbac:listadmins`
**Descripción:** Lista todos los administradores y owners configurados.  
**Uso:** `oxbac:listadmins`  
**Permisos:** Admins y Owners

**Ejemplo:**
```
oxbac:listadmins
```

**Salida:**
```
========================================
  OxB AC - Admins & Owners List
========================================
1. NombreJugador (OWNER)
   License: abc123def456
2. OtroJugador (ADMIN)
   License: xyz789ghi012
========================================
```

#### `oxbac:checkadmin`
**Descripción:** Verifica si un jugador es administrador u owner.  
**Uso:** 
- En consola: `oxbac:checkadmin <playerID>`
- En juego: `oxbac:checkadmin` (verifica tu propio estado)

**Permisos:** Todos (pero solo muestra tu propio estado si no eres admin)

**Ejemplo:**
```
oxbac:checkadmin 1
```

#### `oxbac:exportadmins`
**Descripción:** Exporta la lista de administradores a un archivo JSON.  
**Uso:** `oxbac:exportadmins`  
**Permisos:** Solo Owners

**Ejemplo:**
```
oxbac:exportadmins
```

**Resultado:** Crea un archivo `oxbac_admin_identifiers.json` en la carpeta del recurso.

#### `oxbac:adminids`
**Descripción:** Muestra todos los identificadores de un administrador (license, steam, discord, etc.).  
**Uso:** `oxbac:adminids <license>`  
**Permisos:** Solo Owners  
**Parámetros:**
- `<license>`: License identifier del administrador

**Ejemplo:**
```
oxbac:adminids abc123def456
```

**Salida:**
```
========================================
Admin Identifiers for: NombreJugador
========================================
License: abc123def456
Steam: steam:110000123456789
Discord: discord:123456789012345678
Xbox: xbl:1234567890123456
IP: 192.168.1.1
========================================
```

---

## ⭐ Comandos Indispensables

Estos son los comandos que **DEBES** usar para que el anticheat funcione correctamente:

### 1. `oxbac:install` ⚠️ OBLIGATORIO
**Cuándo usarlo:** Inmediatamente después de instalar el anticheat por primera vez.  
**Frecuencia:** Solo una vez (o cuando agregues nuevos recursos)  
**Por qué es indispensable:** Sin este comando, tus recursos no estarán protegidos por el sistema Shield.

### 2. `oxbac:addadmin` ⚠️ OBLIGATORIO
**Cuándo usarlo:** Al configurar el anticheat por primera vez.  
**Frecuencia:** Al menos una vez para agregarte como owner  
**Por qué es indispensable:** Sin un owner configurado, no podrás gestionar el anticheat.

---

## 👥 Gestión de Administradores

### Roles Disponibles

- **Owner (Propietario):** Acceso completo, puede agregar/eliminar admins, ejecutar instalación, etc.
- **Admin (Administrador):** Puede ver la lista de admins y verificar estados, pero no puede modificar la configuración.

### Flujo de Configuración Recomendado

1. **Instalar el anticheat** en el servidor
2. **Agregarte como owner:**
   ```
   oxbac:addadmin [TU_ID] owner
   ```
3. **Instalar Shield Protection:**
   ```
   oxbac:install
   ```
4. **Reiniciar el servidor**
5. **Verificar que eres owner:**
   ```
   oxbac:checkadmin
   ```
6. **Agregar otros administradores si es necesario:**
   ```
   oxbac:addadmin [ID] admin
   ```

---

## 🛡️ Sistema Shield

El sistema Shield es una protección automática que se instala en todos tus recursos mediante el comando `oxbac:install`.

### ¿Qué hace Shield?

- Protege contra manipulaciones de eventos (`TriggerServerEvent`, `RegisterNetEvent`, etc.)
- Detecta y bloquea exploits comunes
- Implementa rate limiting para prevenir spam
- Valida tipos de datos en eventos
- Detecta intentos de modificación de funciones críticas

### Recursos Protegidos Automáticamente

El comando `oxbac:install` protege automáticamente:
- ✅ Todos los recursos en la carpeta `resources`
- ✅ Recursos en subcarpetas como `[esx]`, `[ox]`, `[qb]`, etc.
- ❌ Excluye recursos del sistema (monitor, rconlog, etc.)

### Verificar Instalación de Shield

Después de ejecutar `oxbac:install`, puedes verificar que Shield está instalado revisando cualquier `fxmanifest.lua` de tus recursos. Deberías ver una línea como:

```lua
shared_scripts { "@anticheat/src/shared/main.lua" }
```

Esta línea debe estar al inicio del archivo, antes de `fx_version`.

---

## 🔧 Solución de Problemas

### El anticheat no se conecta al panel

**Problema:** El anticheat no se conecta al servidor de la API.

**Soluciones:**
1. Verifica que tengas una key de licencia válida
2. Verifica que el servidor tenga conexión a internet
3. Revisa los logs del servidor para ver errores de conexión
4. Asegúrate de que el panel web esté funcionando

### El comando `oxbac:install` no funciona

**Problema:** El comando no instala Shield o da errores.

**Soluciones:**
1. Verifica que seas owner: `oxbac:checkadmin`
2. Si no eres owner, agrega un owner primero
3. Verifica que el servidor tenga permisos de escritura en la carpeta `resources`
4. Revisa los logs del servidor para ver errores específicos

### No puedo agregar administradores

**Problema:** El comando `oxbac:addadmin` no funciona.

**Soluciones:**
1. Verifica que seas owner: `oxbac:checkadmin`
2. Verifica que el ID del jugador sea correcto (usa `status` en consola)
3. Asegúrate de usar el formato correcto: `oxbac:addadmin [ID] [role]`

### Shield no está protegiendo mis recursos

**Problema:** Los recursos no tienen la línea de Shield en su `fxmanifest.lua`.

**Soluciones:**
1. Ejecuta `oxbac:install` nuevamente
2. Verifica que el recurso tenga un `fxmanifest.lua` válido
3. Algunos recursos pueden estar en subcarpetas - el comando los busca automáticamente
4. Reinicia el servidor después de ejecutar `oxbac:install`

### No puedo ver la lista de administradores

**Problema:** El comando `oxbac:listadmins` no muestra nada o da error.

**Soluciones:**
1. Verifica que seas admin u owner: `oxbac:checkadmin`
2. Si no hay administradores, agrega uno primero con `oxbac:addadmin`
3. Verifica que el sistema de almacenamiento KVP esté funcionando

---

## 📞 Soporte

Si tienes problemas que no se resuelven con esta documentación:

1. Revisa los logs del servidor para errores específicos
2. Verifica que todos los pasos de instalación se hayan completado
3. Asegúrate de haber ejecutado `oxbac:install` y reiniciado el servidor
4. Contacta al soporte técnico con:
   - Versión del anticheat (1.0.0)
   - Logs del servidor
   - Descripción detallada del problema
   - Pasos que ya intentaste

---

## 📌 Resumen Rápido

### Instalación Inicial (Pasos Obligatorios)

1. ✅ Colocar recurso en `resources/anticheat`
2. ✅ Agregar `ensure anticheat` en `server.cfg`
3. ✅ Iniciar servidor
4. ✅ Ejecutar `oxbac:addadmin [TU_ID] owner`
5. ✅ Ejecutar `oxbac:install`
6. ✅ Reiniciar servidor
7. ✅ Verificar con `oxbac:checkadmin`

### Comandos Más Usados

- `oxbac:install` - Instalar protección (solo una vez)
- `oxbac:addadmin [ID] [role]` - Agregar administrador
- `oxbac:listadmins` - Ver lista de administradores
- `oxbac:checkadmin` - Verificar tu estado

---

**Última actualización:** Versión 1.0.0  
**Mantenido por:** Coca Dev

