---
title: _splitpath_s, _wsplitpath_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wsplitpath_s
- _splitpath_s
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
- _wsplitpath_s
- splitpath_s
- _splitpath_s
- wsplitpath_s
dev_langs:
- C++
helpviewer_keywords:
- splitpath_s function
- pathnames
- _splitpath_s function
- _wsplitpath_s function
- path names
- wsplitpath_s function
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5fd1407aa6c2b7630e0720eeec179ca27e7d31a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417437"
---
# <a name="splitpaths-wsplitpaths"></a>_splitpath_s, _wsplitpath_s

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

*Unidad*<br/>
Unidad de letra, seguido de dos puntos (**:**). Puede pasar **NULL** para este parámetro si no necesita la letra de unidad.

*driveNumberOfElements*<br/>
El tamaño de la *unidad* búfer en caracteres de byte único o anchos. Si *unidad* es **NULL**, este valor debe ser 0.

*dir*<br/>
Ruta de directorio, incluida la barra diagonal final. Barras diagonales ( **/** ), barras diagonales inversas ( **\\** ), o ambos pueden ser utilizados. Puede pasar **NULL** para este parámetro si no necesita la ruta de acceso de directorio.

*dirNumberOfElements*<br/>
El tamaño de la *dir* búfer en caracteres de byte único o anchos. Si *dir* es **NULL**, este valor debe ser 0.

*fname*<br/>
Nombre de archivo base (sin extensión). Puede pasar **NULL** para este parámetro si no es necesario el nombre de archivo.

*nameNumberOfElements*<br/>
El tamaño de la *fname* búfer en caracteres de byte único o anchos. Si *fname* es **NULL**, este valor debe ser 0.

*ext*<br/>
Extensión de nombre de archivo, incluido el período inicial (**.**). Puede pasar **NULL** para este parámetro si no necesita la extensión de nombre de archivo.

*extNumberOfElements*<br/>
El tamaño de *ext* búfer en caracteres de byte único o anchos. Si *ext* es **NULL**, este valor debe ser 0.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.

### <a name="error-conditions"></a>Condiciones de error

|Condición|Valor devuelto|
|---------------|------------------|
|*ruta de acceso* es **NULL**|**EINVAL**|
|*unidad* es **NULL**, *driveNumberOfElements* es distinto de cero|**EINVAL**|
|*unidad* no es**NULL**, *driveNumberOfElements* es cero|**EINVAL**|
|*dir* es **NULL**, *dirNumberOfElements* es distinto de cero|**EINVAL**|
|*dir* no es**NULL**, *dirNumberOfElements* es cero|**EINVAL**|
|*fname* es **NULL**, *nameNumberOfElements* es distinto de cero|**EINVAL**|
|*fname* no es**NULL**, *nameNumberOfElements* es cero|**EINVAL**|
|*ext* es **NULL**, *extNumberOfElements* es distinto de cero|**EINVAL**|
|*ext* no es**NULL**, *extNumberOfElements* es cero|**EINVAL**|

Si se da alguna de las condiciones anteriores, se invoca al controlador de parámetros no válidos, tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL** y devolver **EINVAL**.

Si cualquiera de los búferes es demasiado corto como para contener el resultado, estas funciones borre todos los búferes para cadenas vacías, establezca **errno** a **ERANGE**y devolver **ERANGE**.

## <a name="remarks"></a>Comentarios

El **_splitpath_s** función divide una ruta de acceso en sus cuatro componentes. **_splitpath_s** controla automáticamente argumentos de cadena de caracteres multibyte según corresponda, reconociendo las secuencias de caracteres multibyte según la página de códigos multibyte actualmente en uso. **_wsplitpath_s** es una versión con caracteres anchos de **_splitpath_s**; los argumentos a **_wsplitpath_s** son cadenas de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

Cada componente de la ruta de acceso completa se almacena en un búfer independiente; las constantes de manifiesto **_MAX_DRIVE**, **_MAX_DIR**, **_MAX_FNAME**, y **_MAX_EXT** (definido en STDLIB. (H) Especifique el tamaño máximo permitido para cada componente de archivo. Los componentes de archivos que son más grandes que las constantes de manifiesto correspondientes provocan daños en el montón.

En la tabla siguiente se enumeran los valores de las constantes de manifiesto.

|nombre|Valor|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

Si la ruta de acceso completa no contiene un componente (por ejemplo, un nombre de archivo), **_splitpath_s** asigna una cadena vacía en el búfer correspondiente.

En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFD. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_splitpath_s**|\<stdlib.h>|
|**_wsplitpath_s**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_makepath_s, _wmakepath_s](makepath-s-wmakepath-s.md).

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
