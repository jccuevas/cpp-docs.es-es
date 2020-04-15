---
title: _splitpath, _wsplitpath
ms.date: 4/2/2020
api_name:
- _wsplitpath
- _splitpath
- _o__splitpath
- _o__wsplitpath
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 6798f93b2d1bc18a190b3b015bf8c882a3fa8a37
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355609"
---
# <a name="_splitpath-_wsplitpath"></a>_splitpath, _wsplitpath

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

*Conducir*<br/>
Letra de unidad, seguida de dos puntos (**:**). Puede pasar **NULL** para este parámetro si no necesita la letra de unidad.

*dir*<br/>
Ruta de directorio, incluida la barra diagonal final. Se pueden **/** utilizar barras diagonales diagonales ( ), barras diagonales inversas ( **\\** ) o ambas. Puede pasar **NULL** para este parámetro si no necesita la ruta de acceso del directorio.

*apellido*<br/>
Nombre de archivo base (sin extensión). Puede pasar **NULL** para este parámetro si no necesita el nombre de archivo.

*Ext*<br/>
Extensión de nombre de archivo, incluido el período inicial (**.**). Puede pasar **NULL** para este parámetro si no necesita la extensión de nombre de archivo.

## <a name="remarks"></a>Observaciones

La función **_splitpath** divide una ruta en sus cuatro componentes. **_splitpath** controla automáticamente los argumentos de cadena de caracteres multibyte según corresponda, reconociendo las secuencias de caracteres multibyte según la página de códigos multibyte actualmente en uso. **_wsplitpath** es una versión de caracteres anchos de **_splitpath;** los argumentos para **_wsplitpath** son cadenas de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

**Nota de seguridad** Estas funciones representan una posible amenaza por un problema de saturación del búfer. Los problemas de saturación del búfer son un método frecuente de ataque del sistema, que produce una elevación de privilegios no justificada. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/win32/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer). Hay disponibles versiones más seguras de estas funciones; ver [_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

Cada componente de la ruta de acceso completa se almacena en un búfer independiente; las constantes de manifiesto **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**y **_MAX_EXT** (definidas en STDLIB. H) especifique el tamaño máximo para cada componente de archivo. Los componentes de archivos que son más grandes que las constantes de manifiesto correspondientes provocan daños en el montón.

Cada búfer debe ser igual de grande que la constante de manifiesto correspondiente con el fin de evitar posibles saturaciones en los búferes.

En la tabla siguiente se enumeran los valores de las constantes de manifiesto.

|Nombre|Value|
|----------|-----------|
|**_MAX_DRIVE**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**_MAX_EXT**|256|

Si la ruta de acceso completa no contiene un componente (por ejemplo, un nombre de archivo), **_splitpath** asigna cadenas vacías a los búferes correspondientes.

Puede pasar **NULL** a **_splitpath** para cualquier parámetro que no sea la ruta de *acceso* que no necesite.

Si *path* es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve **EINVAL**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<stdlib.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_makepath](makepath-wmakepath.md).

## <a name="see-also"></a>Consulte también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
