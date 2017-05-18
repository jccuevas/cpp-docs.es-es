---
title: _get_dstbias | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _get_dstbias
- __dstbias
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
- __dstbias
- _get_dstbias
- get_dstbias
dev_langs:
- C++
helpviewer_keywords:
- __dstbias
- daylight saving time offset
- get_dstbias function
- _get_dstbias function
ms.assetid: e751358c-1ecc-411b-ae2c-81b2ec54ea45
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 51facd97e9e1b7478893c23693d67cd022b5bed7
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="getdstbias"></a>_get_dstbias
Recupera el desplazamiento de horario de verano en segundos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      error_t _get_dstbias(   
    int* seconds  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `seconds`  
 Desplazamiento en segundos del horario de verano.  
  
## <a name="return-value"></a>Valor devuelto  
 Cero si se ejecuta correctamente, o un valor `errno` si se produce un error.  
  
## <a name="remarks"></a>Comentarios  
 La función `_get_dstbias` recupera el número de segundos en el horario de verano como un entero. Si el horario de verano está en vigor, el desplazamiento predeterminado es de 3600 segundos, que es la cantidad de segundos que hay en una hora (si bien en algunas regiones el desplazamiento es de dos horas).  
  
 Si `seconds` es `NULL`, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `EINVAL`.  
  
 Le recomendamos usar esta función en vez de la macro `_dstbias` o la función desusada `__dstbias`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_get_dstbias`|\<time.h>|  
  
 Para obtener más información, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [_get_daylight](../../c-runtime-library/reference/get-daylight.md)   
 [_get_timezone](../../c-runtime-library/reference/get-timezone.md)   
 [_get_tzname](../../c-runtime-library/reference/get-tzname.md)
