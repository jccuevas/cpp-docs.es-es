---
title: _findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _findfirst
- _wfindfirst
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
- findfirst32i64
- wfindfirst32i64
- tfindfirst64
- _findfirst64i32
- _wfindfirst32i64
- _wfindfirsti64
- wfindfirst
- _tfindfirsti64
- findfirst32
- _tfindfirst32
- _findfirsti64
- findfirst
- wfindfirst64
- wfindfirst32
- tfindfirst32
- _wfindfirst64i32
- findfirst64i32
- tfindfirst64i32
- _wfindfirst
- findfirsti64
- _findfirst32i64
- wfindfirst64i32
- _wfindfirst32
- _findfirst32
- _tfindfirst32i64
- tfindfirst
- _tfindfirst64i32
- findfirst64
- _tfindfirst
- _findfirst64
- _tfindfirst64
- tfindfirst32i64
- _findfirst
- _wfindfirst64
dev_langs:
- C++
helpviewer_keywords:
- _tfindfirst64 function
- _wfindfirst64i32 function
- _wfindfirst32i64 function
- wfindfirst32 function
- _findfirst function
- wfindfirst64 function
- _wfindfirst function
- _findfirst64i32 function
- wfindfirst function
- _findfirst64 function
- tfindfirst32 function
- _tfindfirst64i32 function
- findfirst function
- findfirst32i64 function
- tfindfirst64 function
- _tfindfirst32 function
- tfindfirst32i64 function
- tfindfirst64i32 function
- _wfindfirsti64 function
- _findfirst32i64 function
- findfirst32 function
- findfirsti64 function
- findfirst64i32 function
- tfindfirsti64 function
- tfindfirst function
- _wfindfirst32 function
- wfindfirsti64 function
- _tfindfirsti64 function
- _tfindfirst function
- _tfindfirst32i64 function
- findfirst64 function
- _findfirst32 function
- _findfirsti64 function
- wfindfirst32i64 function
- wfindfirst64i32 function
- _wfindfirst64 function
ms.assetid: 9bb46d1a-b946-47de-845a-a0b109a33ead
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 73e513cf4e1d63888f9ad6ef12ed6532b7e158ef
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="findfirst-findfirst32-findfirst32i64-findfirst64-findfirst64i32-findfirsti64-wfindfirst-wfindfirst32-wfindfirst32i64-wfindfirst64-wfindfirst64i32-wfindfirsti64"></a>_findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64
Proporcione información sobre la primera instancia de un nombre de archivo que coincide con el archivo especificado en el argumento `filespec`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
intptr_t _findfirst(  
   const char *filespec,  
   struct _finddata_t *fileinfo   
);  
intptr_t _findfirst32(  
   const char *filespec,  
   struct _finddata32_t *fileinfo   
);  
intptr_t _findfirst64(  
   const char *filespec,  
   struct _finddata64_t *fileinfo   
);  
intptr_t _findfirsti64(  
   const char *filespec,  
   struct _finddatai64_t *fileinfo   
);  
intptr_t _findfirst32i64(  
   const char *filespec,  
   struct _finddata32i64_t *fileinfo   
);  
intptr_t _findfirst64i32(  
   const char *filespec,  
   struct _finddata64i32_t *fileinfo   
);  
intptr_t _wfindfirst(  
   const wchar_t *filespec,  
   struct _wfinddata_t *fileinfo   
);  
intptr_t _wfindfirst32(  
   const wchar_t *filespec,  
   struct _wfinddata32_t *fileinfo   
);  
intptr_t _wfindfirst64(  
   const wchar_t *filespec,  
   struct _wfinddata64_t *fileinfo   
);  
intptr_t _wfindfirsti64(  
   const wchar_t *filespec,  
   struct _wfinddatai64_t *fileinfo   
);  
intptr_t _wfindfirst32i64(  
   const wchar_t *filespec,  
   struct _wfinddata32i64_t *fileinfo   
);  
intptr_t _wfindfirst64i32(  
   const wchar_t *filespec,  
   struct _wfinddata64i32_t *fileinfo   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `filespec`  
 Especificación de archivo de destino (puede incluir caracteres comodín).  
  
 `fileinfo`  
 Búfer de información de archivo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, `_findfirst` devuelve un identificador de búsqueda exclusivo que identifica el archivo o grupo de archivos que coinciden con la especificación `filespec`, que puede usarse en una llamada posterior a [_findnext](../../c-runtime-library/reference/findnext-functions.md) o `_findclose`. En caso contrario, `_findfirst` devuelve -1 y establece `errno` a uno de los siguientes valores.  
  
 `EINVAL`  
 Parámetro no válido: `filespec` o `fileinfo` era `NULL`. O bien, el sistema operativo ha devuelto un error inesperado.  
  
 `ENOENT`  
 Especificación de archivo que no se encuentra.  
  
 `ENOMEM`  
 Memoria insuficiente.  
  
 `EINVAL`  
 Especificación del nombre de archivo no válido o el nombre de archivo indicado era mayor que `MAX_PATH`.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Si se pasa un parámetro no válido, estas funciones invocan al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
## <a name="remarks"></a>Comentarios  
 Debe llamarse a [_findclose](../../c-runtime-library/reference/findclose.md) después de finalizar con la función `_findfirst` o `_findnext` (o cualquiera de sus variantes). Así se liberan los recursos que usan estas funciones de la aplicación.  
  
 Las variaciones de estas funciones que tienen el prefijo `w` son versiones de caracteres anchos; de lo contrario, son idénticas a las correspondientes funciones de un solo byte.  
  
 Las variaciones de estas funciones admiten tipos de tiempo de 32 o 64 bits y tamaños de archivos de 32 o 64 bits. El primer sufijo numérico (`32` o `64`) indica el tamaño del tipo de tiempo usado; el segundo sufijo es `i32` o `i64`, lo que indica si el tamaño del archivo se representa como un entero de 32 o 64 bits. Para obtener información sobre las versiones que admiten tipos de tiempo y tamaños de archivo de 32 bits y 64 bits, consulte la tabla siguiente. El sufijo `i32` o `i64` se omite cuando es igual al tamaño del tipo de tiempo, por lo que `_findfirst64` también admite longitudes de archivo de 64 bits y `_findfirst32` solo admite longitudes de archivo de 32 bits.  
  
 Estas funciones usan diversas formas de la estructura `_finddata_t` para el parámetro `fileinfo`. Para obtener más información sobre la estructura, consulte [Funciones de búsqueda de nombre de archivo](../../c-runtime-library/filename-search-functions.md).  
  
 Las variaciones que usan un tipo de tiempo de 64 bits permiten expresar fechas de creación de archivos hasta las 23:59:59 horas del 31 de diciembre de 3000, UTC. Las que usan un tipo de tiempo de 32 bits, solo representan fechas hasta las 23:59:59 horas del 18 de enero de 2038, UTC. La medianoche del 1 de enero de 1970 es el límite inferior del intervalo de fechas para todas estas funciones.  
  
 A menos que tenga una razón concreta para usar las versiones que especifican el tamaño de tiempo de forma explícita, use `_findfirst` o `_wfindfirst`; si tiene que admitir tamaños de archivo de más de 3 GB, use `_findfirsti64` o `_wfindfirsti64`. Todas estas funciones usan el tipo de tiempo de 64 bits. En versiones anteriores, estas funciones usan un tipo de tiempo de 32 bits. Si se trata de un cambio importante para una aplicación, se podría definir `_USE_32BIT_TIME_T` para revertir al comportamiento anterior. Si se define `_USE_32BIT_TIME_T`, `_findfirst`, `_finfirsti64` y sus correspondientes versiones Unicode usan un tiempo de 32 bits.  
  
### <a name="time-type-and-file-length-type-variations-of-findfirst"></a>Variaciones de tipo de tiempo y tipo de longitud de archivo de _findfirst  
  
|Funciones|¿Se ha definido `_USE_32BIT_TIME_T`?|Tipo de tiempo|Tipo de longitud de archivo|  
|---------------|----------------------------------|---------------|----------------------|  
|`_findfirst`, `_wfindfirst`|No definida|64 bits|32 bits|  
|`_findfirst`, `_wfindfirst`|Definido|32 bits|32 bits|  
|`_findfirst32`, `_wfindfirst32`|No se ve afectada por la definición de macro|32 bits|32 bits|  
|`_findfirst64`, `_wfindfirst64`|No se ve afectada por la definición de macro|64 bits|64 bits|  
|`_findfirsti64`, `_wfindfirsti64`|No definida|64 bits|64 bits|  
|`_findfirsti64`, `_wfindfirsti64`|Definido|32 bits|64 bits|  
|`_findfirst32i64`, `_wfindfirst32i64`|No se ve afectada por la definición de macro|32 bits|64 bits|  
|`_findfirst64i32`, `_wfindfirst64i32`|No se ve afectada por la definición de macro|64 bits|32 bits|  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfindfirst`|`_findfirst`|`_findfirst`|`_wfindfirst`|  
|`_tfindfirst32`|`_findfirst32`|`_findfirst32`|`_wfindfirst32`|  
|`_tfindfirst64`|`_findfirst64`|`_findfirst64`|`_wfindfirst64`|  
|`_tfindfirsti64`|`_findfirsti64`|`_findfirsti64`|`_wfindfirsti64`|  
|`_tfindfirst32i64`|`_findfirst32i64`|`_findfirst32i64`|`_wfindfirst32i64`|  
|`_tfindfirst64i32`|`_findfirst64i32`|`_findfirst64i32`|`_wfindfirst64i32`|  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_findfirst`|\<io.h>|  
|`_findfirst32`|\<io.h>|  
|`_findfirst64`|\<io.h>|  
|`_findfirsti64`|\<io.h>|  
|`_findfirst32i64`|\<io.h>|  
|`_findfirst64i32`|\<io.h>|  
|`_wfindfirst`|\<io.h> o \<wchar.h>|  
|`_wfindfirst32`|\<io.h> o \<wchar.h>|  
|`_wfindfirst64`|\<io.h> o \<wchar.h>|  
|`_wfindfirsti64`|\<io.h> o \<wchar.h>|  
|`_wfindfirst32i64`|\<io.h> o \<wchar.h>|  
|`_wfindfirst64i32`|\<io.h> o \<wchar.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [Llamadas del sistema](../../c-runtime-library/system-calls.md)   
 [Funciones de búsqueda de nombre de archivo](../../c-runtime-library/filename-search-functions.md)