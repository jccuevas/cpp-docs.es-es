---
title: _splitpath_s, _wsplitpath_s
ms.date: 4/2/2020
api_name:
- _wsplitpath_s
- _splitpath_s
- _o__splitpath_s
- _o__wsplitpath_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wsplitpath_s
- splitpath_s
- _splitpath_s
- wsplitpath_s
helpviewer_keywords:
- splitpath_s function
- pathnames
- _splitpath_s function
- _wsplitpath_s function
- path names
- wsplitpath_s function
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
ms.openlocfilehash: 364544a9423668494747405e801d59b73de4e6c6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355620"
---
# <a name="_splitpath_s-_wsplitpath_s"></a>_splitpath_s, _wsplitpath_s

Divide un nombre de ruta de acceso en componentes. Se trata de versiones de [_splitpath, _wsplitpath](splitpath-wsplitpath.md) que incluyen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _splitpath_s(
   const char * path,
   char * drive,
   size_t driveNumberOfElements,
   char * dir,
   size_t dirNumberOfElements,
   char * fname,
   size_t nameNumberOfElements,
   char * ext,
   size_t extNumberOfElements
);
errno_t _wsplitpath_s(
   const wchar_t * path,
   wchar_t * drive,
   size_t driveNumberOfElements,
   wchar_t *dir,
   size_t dirNumberOfElements,
   wchar_t * fname,
   size_t nameNumberOfElements,
   wchar_t * ext,
   size_t extNumberOfElements
);
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _splitpath_s(
   const char *path,
   char (&drive)[drivesize],
   char (&dir)[dirsize],
   char (&fname)[fnamesize],
   char (&ext)[extsize]
); // C++ only
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _wsplitpath_s(
   const wchar_t *path,
   wchar_t (&drive)[drivesize],
   wchar_t (&dir)[dirsize],
   wchar_t (&fname)[fnamesize],
   wchar_t (&ext)[extsize]
); // C++ only
```

### <a name="parameters"></a>Parámetros

*path*<br/>
Ruta de acceso completa.

*Conducir*<br/>
Letra de unidad, seguida de dos puntos (**:**). Puede pasar **NULL** para este parámetro si no necesita la letra de unidad.

*driveNumberOfElements*<br/>
El tamaño del búfer de *unidad* en caracteres anchos o de un solo byte. Si *la unidad* es **NULL**, este valor debe ser 0.

*dir*<br/>
Ruta de directorio, incluida la barra diagonal final. Se pueden **/** utilizar barras diagonales diagonales ( ), barras diagonales inversas ( **\\** ) o ambas. Puede pasar **NULL** para este parámetro si no necesita la ruta de acceso del directorio.

*dirNumberOfElements*<br/>
El tamaño del búfer *dir* en caracteres anchos o de un solo byte. Si *dir* es **NULL**, este valor debe ser 0.

*apellido*<br/>
Nombre de archivo base (sin extensión). Puede pasar **NULL** para este parámetro si no necesita el nombre de archivo.

*nameNumberOfElements*<br/>
El tamaño del búfer *fname* en caracteres anchos o de un solo byte. Si *fname* es **NULL**, este valor debe ser 0.

*Ext*<br/>
Extensión de nombre de archivo, incluido el período inicial (**.**). Puede pasar **NULL** para este parámetro si no necesita la extensión de nombre de archivo.

*extNumberOfElements*<br/>
El tamaño del búfer *ext* en caracteres anchos o de un solo byte. Si *ext* es **NULL**, este valor debe ser 0.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.

### <a name="error-conditions"></a>Condiciones de error

|Condición|Valor devuelto|
|---------------|------------------|
|*ruta* de acceso es **NULL**|**EINVAL**|
|*unidad* es **NULL**, *driveNumberOfElements* es distinto de cero|**EINVAL**|
|*unidad* no es**NULL**, *driveNumberOfElements* es cero|**EINVAL**|
|*dir* es **NULL**, *dirNumberOfElements* es distinto de cero|**EINVAL**|
|*dir* no es**NULL**, *dirNumberOfElements* es cero|**EINVAL**|
|*fname* es **NULL**, *nameNumberOfElements* es distinto de cero|**EINVAL**|
|*fname* no es**NULL**, *nameNumberOfElements* es cero|**EINVAL**|
|*ext* es **NULL**, *extNumberOfElements* es distinto de cero|**EINVAL**|
|*ext* no es**NULL**, *extNumberOfElements* es cero|**EINVAL**|

Si se da alguna de las condiciones anteriores, se invoca al controlador de parámetros no válidos, tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno en** **EINVAL** y devuelven **EINVAL**.

Si alguno de los búferes es demasiado corto para contener el resultado, estas funciones borran todos los búferes en cadenas vacías, **establecen errno en** **ERANGE**y devuelven **ERANGE**.

## <a name="remarks"></a>Observaciones

La función **_splitpath_s** divide una ruta en sus cuatro componentes. **_splitpath_s** controla automáticamente los argumentos de cadena de caracteres multibyte según corresponda, reconociendo las secuencias de caracteres multibyte según la página de códigos multibyte actualmente en uso. **_wsplitpath_s** es una versión de caracteres anchos de **_splitpath_s**; los argumentos para **_wsplitpath_s** son cadenas de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

Cada componente de la ruta de acceso completa se almacena en un búfer independiente; las constantes de manifiesto **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**y **_MAX_EXT** (definidas en STDLIB. H) especifique el tamaño máximo permitido para cada componente de archivo. Los componentes de archivos que son más grandes que las constantes de manifiesto correspondientes provocan daños en el montón.

En la tabla siguiente se enumeran los valores de las constantes de manifiesto.

|Nombre|Value|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

Si la ruta de acceso completa no contiene un componente (por ejemplo, un nombre de archivo), **_splitpath_s** asigna una cadena vacía al búfer correspondiente.

En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

Las versiones de la biblioteca de depuración de estas funciones rellenan primero el búfer con 0xFE. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_splitpath_s**|\<stdlib.h>|
|**_wsplitpath_s**|\<stdlib.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md).

## <a name="see-also"></a>Consulte también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
