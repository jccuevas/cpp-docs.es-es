---
title: _splitpath, _wsplitpath
ms.date: 11/04/2016
apiname:
- _wsplitpath
- _splitpath
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wsplitpath
- _splitpath
- splitpath
- _wsplitpath
- _tsplitpath
helpviewer_keywords:
- _splitpath function
- pathnames
- wsplitpath function
- splitpath function
- _wsplitpath function
- tsplitpath function
- path names
- _tsplitpath function
ms.assetid: 32bd76b5-1385-4ee8-a64c-abcb541cd2e4
ms.openlocfilehash: d079bd17912c0711a4e1fbadadf12430520f2c96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62355008"
---
# <a name="splitpath-wsplitpath"></a>_splitpath, _wsplitpath

Divida un nombre de ruta de acceso en componentes. Hay disponibles versiones más seguras de estas funciones; vea [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md).

## <a name="syntax"></a>Sintaxis

```C
void _splitpath(
   const char *path,
   char *drive,
   char *dir,
   char *fname,
   char *ext
);
void _wsplitpath(
   const wchar_t *path,
   wchar_t *drive,
   wchar_t *dir,
   wchar_t *fname,
   wchar_t *ext
);
```

### <a name="parameters"></a>Parámetros

*path*<br/>
Ruta de acceso completa.

*drive*<br/>
Letra de unidad, seguida de dos puntos (**:**). Puede pasar **NULL** para este parámetro si no necesita la letra de unidad.

*dir*<br/>
Ruta de directorio, incluida la barra diagonal final. Barras diagonales ( **/** ), barras diagonales inversas ( **\\** ), o ambos pueden ser utilizados. Puede pasar **NULL** para este parámetro si no necesita la ruta de acceso de directorio.

*fname*<br/>
Nombre de archivo base (sin extensión). Puede pasar **NULL** para este parámetro si no es necesario el nombre de archivo.

*ext*<br/>
Extensión de nombre de archivo, incluido el punto inicial (**.**). Puede pasar **NULL** para este parámetro si no necesita la extensión de nombre de archivo.

## <a name="remarks"></a>Comentarios

El **_splitpath** función divide una ruta de acceso en los cuatro componentes respectivos. **_splitpath** controla automáticamente argumentos de cadena de caracteres multibyte según corresponda, reconociendo las secuencias de caracteres multibyte según la página de códigos multibyte actualmente en uso. **_wsplitpath** es una versión con caracteres anchos de **_splitpath**; los argumentos de **_wsplitpath** son cadenas de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

**Nota de seguridad** Estas funciones representan una posible amenaza por un problema de saturación del búfer. Los problemas de saturación del búfer son un método frecuente de ataque del sistema, que produce una elevación de privilegios no justificada. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/desktop/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer). Hay disponibles versiones más seguras de estas funciones; vea [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

Cada componente de la ruta de acceso completa se almacena en un búfer independiente; las constantes de manifiesto **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**, y **_MAX_EXT** (definido en STDLIB. (H) Especifique el tamaño máximo para cada componente de archivo. Los componentes de archivos que son más grandes que las constantes de manifiesto correspondientes provocan daños en el montón.

Cada búfer debe ser igual de grande que la constante de manifiesto correspondiente con el fin de evitar posibles saturaciones en los búferes.

En la tabla siguiente se enumeran los valores de las constantes de manifiesto.

|Name|Valor|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

Si la ruta de acceso completa no contiene ningún componente (por ejemplo, un nombre de archivo), **_splitpath** asigna cadenas vacías a los búferes correspondientes.

Puede pasar **NULL** a **_splitpath** para cualquier parámetro distinto *ruta de acceso* que no es necesario.

Si *ruta* es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve **EINVAL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_makepath](makepath-wmakepath.md).

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
