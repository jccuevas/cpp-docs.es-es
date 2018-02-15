---
title: _RTC_GetErrDesc | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _RTC_GetErrDesc
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
apitype: DLLExport
f1_keywords:
- RTC_GetErrDesc
- _RTC_GetErrDesc
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- _RTC_GetErrDesc function
- RTC_GetErrDesc function
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ba19cb678ab92f45f65aee4c22c28ef0908b32e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="rtcgeterrdesc"></a>_RTC_GetErrDesc
Devuelve una breve descripción de un tipo de comprobación de error en tiempo de ejecución (RTC).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      const char * _RTC_GetErrDesc(  
   _RTC_ErrorNumber errnum   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *errnum*  
 Un número entre cero y el valor devuelto por `_RTC_NumErrors`menos uno.  
  
## <a name="return-value"></a>Valor devuelto  
 Una cadena de caracteres que contiene una descripción breve de uno de los tipos de error que detectó el sistema de comprobación de errores en tiempo de ejecución. Si el error es menor que cero o mayor o igual que el valor devuelto por [_RTC_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md), `_RTC_GetErrDesc` devuelve NULL.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_RTC_GetErrDesc`|\<rtcapi.h>|  
  
 Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vea también  
 [_RTC_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md)   
 [Comprobar errores en tiempo de ejecución](../../c-runtime-library/run-time-error-checking.md)