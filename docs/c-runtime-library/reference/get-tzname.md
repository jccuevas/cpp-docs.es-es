---
title: _get_tzname | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _get_tzname
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_tzname
- get_tzname
dev_langs:
- C++
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
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
ms.openlocfilehash: 2a7712c311c5007b2d50578d78452d6c989a7ad1
ms.lasthandoff: 02/24/2017

---
# <a name="gettzname"></a>_get_tzname
Recupera la representación de cadena de caracteres del nombre de zona horaria o el nombre de zona de hora estándar de horario de verano (DST).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t _get_tzname(  
    size_t* pReturnValue,  
    char* timeZoneName,  
    size_t sizeInBytes,  
    int index      
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `pReturnValue`  
 Longitud de cadena de `timeZoneName` que incluye un terminador NULL.  
  
 [out] `timeZoneName`  
 Dirección de una cadena de caracteres para la representación del nombre de zona horaria o el nombre de zona de hora estándar de horario de verano (DST), en función de `index`.  
  
 [in] `sizeInBytes`  
 Tamaño de la cadena de caracteres `timeZoneName` en bytes.  
  
 [in] `index`  
 Índice de uno de los dos nombres de zona horaria que se van a recuperar.  
  
## <a name="return-value"></a>Valor devuelto  
 Cero si se ejecuta correctamente; en caso contrario, un valor de tipo `errno`.  
  
 Si `timeZoneName` es `NULL` o `sizeInBytes` es cero o menor que cero (pero no ambas cosas), se invoca a un controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `EINVAL`.  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|`pReturnValue`|`timeZoneName`|`sizeInBytes`|`index`|Valor devuelto|Contenido de `timeZoneName`|  
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|  
|tamaño de nombre de ZH|`NULL`|0|0 o 1|0|no modificado|  
|tamaño de nombre de ZH|any|> 0|0 o 1|0|Nombre de ZH|  
|no modificado|`NULL`|> 0|cualquiera|`EINVAL`|no modificado|  
|no modificado|any|cero|cualquiera|`EINVAL`|no modificado|  
|no modificado|any|> 0|> 1|`EINVAL`|no modificado|  
  
## <a name="remarks"></a>Comentarios  
 La función `_get_tzname` recupera la representación de cadena de caracteres del nombre de zona horaria o el nombre de zona de hora estándar de horario de verano (DST) en la dirección de `timeZoneName` en función del valor de índice, junto con el tamaño de la cadena en `pReturnValue`. Si `timeZoneName` es `NULL` y `sizeInBytes` es cero, en `pReturnValue` solo se devuelve el tamaño de la cadena de cualquiera de las zonas horarias en bytes. Los valores de índice deben ser 0 para la zona horaria estándar o 1 para la zona de hora estándar de horario de verano; todos los demás valores de índice tienen resultados indeterminados.  
  
### <a name="index-values"></a>Valores de índice  
  
|`index`|Contenido de `timeZoneName`|Valor predeterminado `timeZoneName`|  
|-------------|--------------------------------|----------------------------------|  
|0|Nombre de zona horaria|"PST"|  
|1|Nombre de zona de hora estándar de horario de verano|"PDT"|  
|> 1 o < 0|`errno` se establece en `EINVAL`|no modificado|  
  
 A menos que los valores se cambien explícitamente durante el tiempo de ejecución, los valores predeterminados son "PST" y "PDT", respectivamente.  El tamaño de estas matrices de caracteres se rige por el valor `TZNAME_MAX`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_get_tzname`|\<time.h>|  
  
 Para obtener más información, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [_get_daylight](../../c-runtime-library/reference/get-daylight.md)   
 [_get_dstbias](../../c-runtime-library/reference/get-dstbias.md)   
 [_get_timezone](../../c-runtime-library/reference/get-timezone.md)   
 [TZNAME_MAX](../../c-runtime-library/tzname-max.md)
