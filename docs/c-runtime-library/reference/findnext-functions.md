---
title: _findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64
ms.date: 4/2/2020
api_name:
- _findnext
- _findnext32
- _findnext32i64
- _findnext64
- _findnext64i32
- _findnexti64
- _wfindnext
- _wfindnext32
- _wfindnext32i64
- _wfindnext64
- _wfindnext64i32
- _wfindnexti64
- _o__findnext32
- _o__findnext32i64
- _o__findnext64
- _o__findnext64i32
- _o__wfindnext32
- _o__wfindnext32i64
- _o__wfindnext64
- _o__wfindnext64i32
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: acb680db3b07b0f600b758401f1270deccf03da7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911659"
---
# <a name="_findnext-_findnext32-_findnext32i64-_findnext64-_findnext64i32-_findnexti64-_wfindnext-_wfindnext32-_wfindnext32i64-_wfindnext64-_wfindnext64i32-_wfindnexti64"></a>_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64

Busque el siguiente nombre, si lo hay, que coincida con el argumento *filespec* en una llamada anterior a [_findfirst](findfirst-functions.md)y, a continuación, modifique el contenido de la estructura *FileInfo* en consecuencia.

## <a name="syntax"></a>Sintaxis

```C
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

### <a name="parameters"></a>Parámetros

*asa*<br/>
Identificador de búsqueda devuelto por una llamada anterior a **_findfirst**.

*FileInfo*<br/>
Búfer de información de archivo.

## <a name="return-value"></a>Valor devuelto

Si la operación se realiza correctamente, devuelve 0. De lo contrario, devuelve-1 y establece **errno** en un valor que indica la naturaleza del error. En la siguiente tabla se muestran los posibles códigos de error.

|valor de errno|Condición|
|-|-|
| **EINVAL** | Parámetro no válido: *FileInfo* era **null**. O bien, el sistema operativo ha devuelto un error inesperado. |
| **ENOENT** | No se han encontrado más archivos coincidentes. |
| **ENOMEM** | Memoria insuficiente o la longitud del nombre de archivo superó **MAX_PATH**. |

Si se pasa un parámetro no válido, estas funciones invocan al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Observaciones

Debe llamar a [_findclose](findclose.md) cuando haya terminado de usar la función **_findfirst** o **_findnext** (o cualquier variante). Así se liberan los recursos que usan estas funciones de la aplicación.

Las variaciones de estas funciones con el prefijo **w** son versiones con caracteres anchos; de lo contrario, son idénticas a las funciones de un solo byte correspondientes.

Las variaciones de estas funciones admiten tipos de tiempo de 32 o 64 bits y tamaños de archivos de 32 o 64 bits. El primer sufijo numérico (**32** o **64**) indica el tamaño del tipo de tiempo utilizado. el segundo sufijo es **I32** o **i64**, que indica si el tamaño del archivo se representa como un entero de 32 bits o 64 bits. Para obtener información sobre las versiones que admiten tipos de tiempo y tamaños de archivo de 32 bits y 64 bits, consulte la tabla siguiente. Las variaciones que usan un tipo de tiempo de 64 bits permiten expresar fechas de creación de archivos hasta las 23:59:59 horas del 31 de diciembre de 3000, UTC; mientras que las que usan un tipo de tiempo de 32 bits solo representan fechas hasta las 23:59:59 horas del 18 de enero de 2038, UTC. La medianoche del 1 de enero de 1970 es el límite inferior del intervalo de fechas para todas estas funciones.

A menos que tenga una razón concreta para usar las versiones que especifican el tamaño de tiempo de forma explícita, use **_findnext** o **_wfindnext** o, si necesita admitir tamaños de archivo superiores a 3 GB, use **_findnexti64** o **_wfindnexti64**. Todas estas funciones usan el tipo de tiempo de 64 bits. En versiones anteriores, estas funciones usan un tipo de tiempo de 32 bits. Si se trata de un cambio importante para una aplicación, puede definir **_USE_32BIT_TIME_T** para obtener el comportamiento anterior. Si se define **_USE_32BIT_TIME_T** , **_findnext**, **_finnexti64** y sus correspondientes versiones unicode usan un tiempo de 32 bits.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_findnext"></a>Variaciones de tipo de tiempo y tipo de longitud de archivo de _findnext

|Functions|¿ **_USE_32BIT_TIME_T** definido?|Tipo de tiempo|Tipo de longitud de archivo|
|---------------|----------------------------------|---------------|----------------------|
|**_findnext**, **_wfindnext**|No definida|64 bits|32 bits|
|**_findnext**, **_wfindnext**|Definido|32 bits|32 bits|
|**_findnext32**, **_wfindnext32**|No se ve afectada por la definición de macro|32 bits|32 bits|
|**_findnext64**, **_wfindnext64**|No se ve afectada por la definición de macro|64 bits|64 bits|
|**_findnexti64**, **_wfindnexti64**|No definida|64 bits|64 bits|
|**_findnexti64**, **_wfindnexti64**|Definido|32 bits|64 bits|
|**_findnext32i64**, **_wfindnext32i64**|No se ve afectada por la definición de macro|32 bits|64 bits|
|**_findnext64i32**, **_wfindnext64i32**|No se ve afectada por la definición de macro|64 bits|32 bits|

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindnext**|**_findnext**|**_findnext**|**_wfindnext**|
|**_tfindnext32**|**_findnext32**|**_findnext32**|**_wfindnext32**|
|**_tfindnext64**|**_findnext64**|**_findnext64**|**_wfindnext64**|
|**_tfindnexti64**|**_findnexti64**|**_findnexti64**|**_wfindnexti64**|
|**_tfindnext32i64**|**_findnext32i64**|**_findnext32i64**|**_wfindnext32i64**|
|**_tfindnext64i32**|**_findnext64i32**|**_findnext64i32**|**_wfindnext64i32**|

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_findnext**|\<io.h>|
|**_findnext32**|\<io.h>|
|**_findnext64**|\<io.h>|
|**_findnexti64**|\<io.h>|
|**_findnext32i64**|\<io.h>|
|**_findnext64i32**|\<io.h>|
|**_wfindnext**|\<io.h> o \<wchar.h>|
|**_wfindnext32**|\<io.h> o \<wchar.h>|
|**_wfindnext64**|\<io.h> o \<wchar.h>|
|**_wfindnexti64**|\<io.h> o \<wchar.h>|
|**_wfindnext32i64**|\<io.h> o \<wchar.h>|
|**_wfindnext64i32**|\<io.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Consulta también

[Llamadas del sistema](../../c-runtime-library/system-calls.md)<br/>
[Funciones de búsqueda de nombre de archivo](../../c-runtime-library/filename-search-functions.md)<br/>
