---
title: _findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wfindnext
- _findnext
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
- findnext
- _wfindnext32i64
- _tfindnext64i32
- findnext32
- findnext32i64
- wfindnext64i32
- _wfindnext
- tfindnext64
- findnexti64
- _findnexti64
- _tfindnexti64
- _findnext64i32
- tfindnexti64
- tfindnext32
- _wfindnext64i32
- findnext64i32
- _findnext
- _tfindnext32i64
- _wfindnext64
- wfindnext
- wfindnext32
- tfindnext32i64
- _findnext64
- _tfindnext64
- _wfindnext32
- findnext64
- _findnext32i64
- tfindnext
- wfindnexti64
- tfindnext64i32
- _tfindnext32
- wfindnext32i64
- wfindnext64
- _wfindnexti64
- _tfindnext
- _findnext32
dev_langs: C++
helpviewer_keywords:
- _wfindnexti64 function
- _tfindnext32 function
- wfindnexti64 function
- _wfindnext32i64 function
- findnext32i64 function
- tfindnext64i32 function
- _tfindnext64i32 function
- _findnext function
- findnext64i32 function
- _tfindnext function
- findnext32 function
- tfindnext32 function
- _findnext32 function
- _tfindnext32i64 function
- _wfindnext function
- tfindnext function
- _findnext64 function
- findnext64 function
- _findnext64i32 function
- wfindnext32i64 function
- findnext function
- wfindnext32 function
- _wfindnext64i32 function
- findnexti64 function
- _wfindnext64 function
- _findnext32i64 function
- _findnexti64 function
- _tfindnext64 function
- wfindnext64i32 function
- tfindnexti64 function
- wfindnext64 function
- wfindnext function
- tfindnext64 function
- _wfindnext32 function
- tfindnext32i64 function
- _tfindnexti64 function
ms.assetid: 75d97188-5add-4698-a46c-4c492378f0f8
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6fbb76781c04afb1de970cde3d233d54909b64a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="findnext-findnext32-findnext32i64-findnext64-findnext64i32-findnexti64-wfindnext-wfindnext32-wfindnext32i64-wfindnext64-wfindnext64i32-wfindnexti64"></a>_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64
Buscan el nombre siguiente, si procede, que coincide con el argumento `filespec` en una llamada anterior a [_findfirst](../../c-runtime-library/reference/findfirst-functions.md) y luego modifican el contenido de la estructura `fileinfo` en consecuencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _findnext(  
   intptr_t handle,  
   struct _finddata_t *fileinfo   
);  
int _findnext32(  
   intptr_t handle,  
   struct _finddata32_t *fileinfo   
);  
int _findnext64(  
   intptr_t handle,  
   struct __finddata64_t *fileinfo   
);  
int _findnexti64(  
   intptr_t handle,  
   struct __finddatai64_t *fileinfo   
);  
int _findnext32i64(  
   intptr_t handle,  
   struct _finddata32i64_t *fileinfo   
);  
int _findnext64i32(  
   intptr_t handle,  
   struct _finddata64i32_t *fileinfo   
);  
int _wfindnext(  
   intptr_t handle,  
   struct _wfinddata_t *fileinfo   
);  
int _wfindnext32(  
   intptr_t handle,  
   struct _wfinddata32_t *fileinfo   
);  
int _wfindnext64(  
   intptr_t handle,  
   struct _wfinddata64_t *fileinfo   
);  
int _wfindnexti64(  
   intptr_t handle,  
   struct _wfinddatai64_t *fileinfo   
);  
int _wfindnext32i64(  
   intptr_t handle,  
   struct _wfinddatai64_t *fileinfo   
);  
int _wfindnext64i32(  
   intptr_t handle,  
   struct _wfinddata64i32_t *fileinfo   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `handle`  
 Identificador de búsqueda devuelto por una llamada anterior a `_findfirst`.  
  
 `fileinfo`  
 Búfer de información de archivo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve 0. En caso contrario, devuelve -1 y establece `errno` en un valor que indica la naturaleza del error. En la siguiente tabla se muestran los posibles códigos de error.  
  
 `EINVAL`  
 Parámetro no válido: `fileinfo` era `NULL`. O bien, el sistema operativo ha devuelto un error inesperado.  
  
 `ENOENT`  
 No se han encontrado más archivos coincidentes.  
  
 `ENOMEM`  
 No hay suficiente memoria o la longitud del nombre de archivo supera a `MAX_PATH`.  
  
 Si se pasa un parámetro no válido, estas funciones invocan al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
## <a name="remarks"></a>Comentarios  
 Debe llamarse a [_findclose](../../c-runtime-library/reference/findclose.md) después de finalizar con la función `_findfirst` o `_findnext` (o cualquiera de sus variantes). Así se liberan los recursos que usan estas funciones de la aplicación.  
  
 Las variaciones de estas funciones con el prefijo `w` son versiones de caracteres anchos; de lo contrario, son idénticas a las correspondientes funciones de un solo byte.  
  
 Las variaciones de estas funciones admiten tipos de tiempo de 32 o 64 bits y tamaños de archivos de 32 o 64 bits. El primer sufijo numérico (`32` o `64`) indica el tamaño del tipo de tiempo usado; el segundo sufijo es `i32` o `i64`, lo que indica si el tamaño del archivo se representa como un entero de 32 o 64 bits. Para obtener información sobre las versiones que admiten tipos de tiempo y tamaños de archivo de 32 bits y 64 bits, consulte la tabla siguiente. Las variaciones que usan un tipo de tiempo de 64 bits permiten expresar fechas de creación de archivos hasta las 23:59:59 horas del 31 de diciembre de 3000, UTC; mientras que las que usan un tipo de tiempo de 32 bits solo representan fechas hasta las 23:59:59 horas del 18 de enero de 2038, UTC. La medianoche del 1 de enero de 1970 es el límite inferior del intervalo de fechas para todas estas funciones.  
  
 A menos que tenga una razón concreta para usar las versiones que especifican el tamaño de tiempo de forma explícita, use `_findnext` o `_wfindnext`; si tiene que admitir tamaños de archivo de más de 3 GB, use `_findnexti64` o `_wfindnexti64`. Todas estas funciones usan el tipo de tiempo de 64 bits. En versiones anteriores, estas funciones usan un tipo de tiempo de 32 bits. Si se trata de un cambio importante para una aplicación, se podría definir `_USE_32BIT_TIME_T` para obtener al comportamiento anterior. Si se define `_USE_32BIT_TIME_T`, `_findnext`, `_finnexti64` y sus correspondientes versiones Unicode usan un tiempo de 32 bits.  
  
### <a name="time-type-and-file-length-type-variations-of-findnext"></a>Variaciones de tipo de tiempo y tipo de longitud de archivo de _findnext  
  
|Funciones|¿Se ha definido `_USE_32BIT_TIME_T`?|Tipo de tiempo|Tipo de longitud de archivo|  
|---------------|----------------------------------|---------------|----------------------|  
|`_findnext`, `_wfindnext`|No definida|64 bits|32 bits|  
|`_findnext`, `_wfindnext`|Definido|32 bits|32 bits|  
|`_findnext32`, `_wfindnext32`|No se ve afectada por la definición de macro|32 bits|32 bits|  
|`_findnext64`, `_wfindnext64`|No se ve afectada por la definición de macro|64 bits|64 bits|  
|`_findnexti64`, `_wfindnexti64`|No definida|64 bits|64 bits|  
|`_findnexti64`, `_wfindnexti64`|Definido|32 bits|64 bits|  
|`_findnext32i64`, `_wfindnext32i64`|No se ve afectada por la definición de macro|32 bits|64 bits|  
|`_findnext64i32`, `_wfindnext64i32`|No se ve afectada por la definición de macro|64 bits|32 bits|  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfindnext`|`_findnext`|`_findnext`|`_wfindnext`|  
|`_tfindnext32`|`_findnext32`|`_findnext32`|`_wfindnext32`|  
|`_tfindnext64`|`_findnext64`|`_findnext64`|`_wfindnext64`|  
|`_tfindnexti64`|`_findnexti64`|`_findnexti64`|`_wfindnexti64`|  
|`_tfindnext32i64`|`_findnext32i64`|`_findnext32i64`|`_wfindnext32i64`|  
|`_tfindnext64i32`|`_findnext64i32`|`_findnext64i32`|`_wfindnext64i32`|  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_findnext`|\<io.h>|  
|`_findnext32`|\<io.h>|  
|`_findnext64`|\<io.h>|  
|`_findnexti64`|\<io.h>|  
|`_findnext32i64`|\<io.h>|  
|`_findnext64i32`|\<io.h>|  
|`_wfindnext`|\<io.h> o \<wchar.h>|  
|`_wfindnext32`|\<io.h> o \<wchar.h>|  
|`_wfindnext64`|\<io.h> o \<wchar.h>|  
|`_wfindnexti64`|\<io.h> o \<wchar.h>|  
|`_wfindnext32i64`|\<io.h> o \<wchar.h>|  
|`_wfindnext64i32`|\<io.h> o \<wchar.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vea también  
 [Llamadas del sistema](../../c-runtime-library/system-calls.md)   
 [Funciones de búsqueda de nombre de archivo](../../c-runtime-library/filename-search-functions.md)