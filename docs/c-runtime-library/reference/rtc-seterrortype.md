---
title: _RTC_SetErrorType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _RTC_SetErrorType
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
- RTC_SetErrorType
- _RTC_SetErrorType
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: da5f95812b750da5f337eb459cf136b7eb827c5c
ms.lasthandoff: 02/24/2017

---
# <a name="rtcseterrortype"></a>_RTC_SetErrorType
Asocia un error que se detecta mediante comprobaciones de errores en tiempo de ejecución (RTC) con un tipo. El controlador de errores procesa cómo mostrar los errores del tipo especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      int _RTC_SetErrorType(  
   _RTC_ErrorNumber errnum,  
   int ErrType   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *errnum*  
 Un número entre cero y uno menos el valor devuelto por [_RTC_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md).  
  
 *ErrType*  
 Valor que se va a asignar a este elemento *errnum*. Por ejemplo, se podría usar **_CRT_ERROR**. Si usa `_CrtDbgReport` como controlador de errores, *ErrType* solo puede ser uno de los símbolos definidos en [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md). Si tiene su propio controlador de errores ([_RTC_SetErrorFunc](../../c-runtime-library/reference/rtc-seterrorfunc.md)), puede disponer de tantos elementos *ErrType* como elementos *errnum* haya.  
  
 Un valor de *ErrType* de _RTC_ERRTYPE_IGNORE tiene un significado especial para `_CrtSetReportMode`; se omite el error.  
  
## <a name="return-value"></a>Valor devuelto  
 El valor anterior del tipo de error `type`.  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, todos los errores se establecen en *ErrType* = 1, que corresponde a **_CRT_ERROR**. Para obtener más información sobre los tipos de errores predeterminados, como **_CRT_ERROR**, vea [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).  
  
 Antes de poder llamar a esta función, primero debe llamar a una de las funciones de inicialización de comprobación de errores en tiempo de ejecución; vea [Uso de comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_RTC_SetErrorType`|\<rtcapi.h>|  
  
 Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [_RTC_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [Comprobar errores en tiempo de ejecución](../../c-runtime-library/run-time-error-checking.md)
