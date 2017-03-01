---
title: _splitpath, _wsplitpath | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs:
- C++
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
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: af46452d23eb6194a0562dc37bbe082a56762a2b
ms.lasthandoff: 02/24/2017

---
# <a name="splitpath-wsplitpath"></a>_splitpath, _wsplitpath
Divida un nombre de ruta de acceso en componentes. Hay disponibles versiones más seguras de estas funciones; vea [_splitpath_s, _wsplitpath_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
  
#### <a name="parameters"></a>Parámetros  
 `path`  
 Ruta de acceso completa.  
  
 `drive`  
 Letra de unidad, seguida de dos puntos (`:`). Puede pasar `NULL` para este parámetro si no necesita la letra de unidad.  
  
 `dir`  
 Ruta de directorio, incluida la barra diagonal final. Se pueden usar las barras diagonales (`/`), las barras diagonales inversas (`\`) o ambas. Puede pasar `NULL` para este parámetro si no necesita la ruta de acceso del directorio.  
  
 `fname`  
 Nombre de archivo base (sin extensión). Puede pasar `NULL` para este parámetro si no necesita el nombre de archivo.  
  
 `ext`  
 Extensión de nombre de archivo, incluido el punto inicial (`.`). Puede pasar `NULL` para este parámetro si no necesita la extensión de nombre de archivo.  
  
## <a name="remarks"></a>Comentarios  
 La función `_splitpath` divide una ruta de acceso en los cuatro componentes respectivos. `_splitpath` controla automáticamente los argumentos de cadenas de caracteres multibyte según corresponda, reconociendo las secuencias de caracteres multibyte de acuerdo con la página de códigos multibyte actualmente en uso. `_wsplitpath` es una versión con caracteres anchos de `_splitpath`; los argumentos a `_wsplitpath` son cadenas de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.  
  
 **Nota de seguridad** Estas funciones representan una posible amenaza por un problema de saturación del búfer. Los problemas de saturación del búfer son un método frecuente de ataque del sistema, que produce una elevación de privilegios no justificada. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer). Hay disponibles versiones más seguras de estas funciones; vea [_splitpath_s, _wsplitpath_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md).  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tsplitpath`|`_splitpath`|`_splitpath`|`_wsplitpath`|  
  
 Cada componente de la ruta de acceso completa se almacena en un búfer independiente; las constantes de manifiesto `_MAX_DRIVE`, `_MAX_DIR`, `_MAX_FNAME` y `_MAX_EXT` (definidas en STDLIB.H) especifican el tamaño máximo para cada componente de archivo. Los componentes de archivos que son más grandes que las constantes de manifiesto correspondientes provocan daños en el montón.  
  
 Cada búfer debe ser igual de grande que la constante de manifiesto correspondiente con el fin de evitar posibles saturaciones en los búferes.  
  
 En la tabla siguiente se enumeran los valores de las constantes de manifiesto.  
  
|Nombre|Valor|  
|----------|-----------|  
|_MAX_DRIVE|3|  
|_MAX_DIR|256|  
|_MAX_FNAME|256|  
|_MAX_EXT|256|  
  
 Si la ruta de acceso completa no contiene ningún componente (por ejemplo, un nombre de archivo), `_splitpath` asigna cadenas vacías a los búferes correspondientes.  
  
 Puede pasar `NULL` a `_splitpath` para cualquier parámetro distinto de `path` que no necesite.  
  
 Si `path` es `NULL`, se invoca el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `EINVAL`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_splitpath`|\<stdlib.h>|  
|`_wsplitpath`|\<stdlib.h> o \<wchar.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [_makepath](../../c-runtime-library/reference/makepath-wmakepath.md).  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [_fullpath, _wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_makepath, _wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [_splitpath_s, _wsplitpath_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)
