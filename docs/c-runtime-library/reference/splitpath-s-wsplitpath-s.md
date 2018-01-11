---
title: _splitpath_s, _wsplitpath_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- splitpath_s function
- pathnames
- _splitpath_s function
- _wsplitpath_s function
- path names
- wsplitpath_s function
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
caps.latest.revision: "29"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6cfb2d72b728b64aeb00c3b8437f9c47e02fb813
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="splitpaths-wsplitpaths"></a>_splitpath_s, _wsplitpath_s
Divide un nombre de ruta de acceso en componentes. Se trata de versiones de [_splitpath, _wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md) que incluyen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
  
#### <a name="parameters"></a>Parámetros  
 [in] `path`  
 Ruta de acceso completa.  
  
 [out] `drive`  
 Letra de unidad, seguida de dos puntos (`:`). Puede pasar `NULL` para este parámetro si no necesita la letra de unidad.  
  
 [in] `driveNumberOfElements`  
 Tamaño del búfer `drive` en caracteres de un solo byte o en caracteres anchos. Si `drive` es `NULL`, este valor debe ser 0.  
  
 [out] `dir`  
 Ruta de directorio, incluida la barra diagonal final. Se pueden usar las barras diagonales (`/`), las barras diagonales inversas (`\`) o ambas. Puede pasar `NULL` para este parámetro si no necesita la ruta de acceso del directorio.  
  
 [in] `dirNumberOfElements`  
 Tamaño del búfer `dir` en caracteres de un solo byte o en caracteres anchos. Si `dir` es `NULL`, este valor debe ser 0.  
  
 [out] `fname`  
 Nombre de archivo base (sin extensión). Puede pasar `NULL` para este parámetro si no necesita el nombre de archivo.  
  
 [in] `nameNumberOfElements`  
 Tamaño del búfer `fname` en caracteres de un solo byte o en caracteres anchos. Si `fname` es `NULL`, este valor debe ser 0.  
  
 [out] `ext`  
 Extensión de nombre de archivo, incluido el punto inicial (**.**). Puede pasar `NULL` para este parámetro si no necesita la extensión de nombre de archivo.  
  
 [in] `extNumberOfElements`  
 Tamaño del búfer `ext` en caracteres de un solo byte o en caracteres anchos. Si `ext` es `NULL`, este valor debe ser 0.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|Condición|Valor devuelto|  
|---------------|------------------|  
|`path` es `NULL`|`EINVAL`|  
|`drive` es `NULL`, mientras que `driveNumberOfElements` es distinto de cero|`EINVAL`|  
|`drive` es distinto de `NULL`, mientras que `driveNumberOfElements` es cero|`EINVAL`|  
|`dir` es `NULL`, mientras que `dirNumberOfElements` es distinto de cero|`EINVAL`|  
|`dir` es distinto de `NULL`, mientras que `dirNumberOfElements` es cero|`EINVAL`|  
|`fname` es `NULL`, mientras que `nameNumberOfElements` es distinto de cero|`EINVAL`|  
|`fname` es distinto de `NULL`, mientras que `nameNumberOfElements` es cero|`EINVAL`|  
|`ext` es `NULL`, mientras que `extNumberOfElements` es distinto de cero|`EINVAL`|  
|`ext` es distinto de `NULL`, mientras que `extNumberOfElements` es cero|`EINVAL`|  
  
 Si se da alguna de las condiciones anteriores, se invoca al controlador de parámetros no válidos, tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `EINVAL`.  
  
 Si alguno de los búferes es demasiado pequeño para contener el resultado, estas funciones borran todos los búferes en cadenas vacías, establecen `errno` en `ERANGE` y devuelven `ERANGE`.  
  
## <a name="remarks"></a>Comentarios  
 La función `_splitpath_s` divide una ruta de acceso en los cuatro componentes respectivos. `_splitpath_s` controla automáticamente argumentos de cadenas de caracteres multibyte según corresponda, reconociendo secuencias de caracteres multibyte según la página de códigos multibyte actualmente en uso. `_wsplitpath_s` es una versión con caracteres anchos de `_splitpath_s`; los argumentos a `_wsplitpath_s` son cadenas de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tsplitpath_s`|`_splitpath_s`|`_splitpath_s`|`_wsplitpath_s`|  
  
 Cada componente de la ruta de acceso completa se almacena en un búfer independiente; las constantes de manifiesto `_MAX_DRIVE`, `_MAX_DIR`, `_MAX_FNAME` y `_MAX_EXT` (definidas en STDLIB.H) especifican el tamaño máximo permitido para cada componente de archivo. Los componentes de archivos que son más grandes que las constantes de manifiesto correspondientes provocan daños en el montón.  
  
 En la tabla siguiente se enumeran los valores de las constantes de manifiesto.  
  
|nombre|Valor|  
|----------|-----------|  
|_MAX_DRIVE|3|  
|_MAX_DIR|256|  
|_MAX_FNAME|256|  
|_MAX_EXT|256|  
  
 Si la ruta de acceso completa no contiene ningún componente (por ejemplo, un nombre de archivo), `_splitpath_s` asigna una cadena vacía al búfer correspondiente.  
  
 En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
 Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFD. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_splitpath_s`|\<stdlib.h>|  
|`_wsplitpath_s`|\<stdlib.h> o \<wchar.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [_makepath_s, _wmakepath_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [_splitpath, _wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)   
 [_fullpath, _wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_makepath, _wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)