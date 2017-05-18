---
title: _RTC_SetErrorType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 78f056e65523a39477bf138e6bd1664e0945a899
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

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
 Un número entre cero y el valor devuelto por [_RTC_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md)menos uno.  
  
 *ErrType*  
 Valor que se va a asignar a este elemento *errnum*. Por ejemplo, se podría usar **_CRT_ERROR**. Si está utilizando `_CrtDbgReport` como el controlador de errores *ErrType* solo puede tener uno de los símbolos definidos en [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md). Si tiene su propio controlador de errores ([_RTC_SetErrorFunc](../../c-runtime-library/reference/rtc-seterrorfunc.md)), puede disponer de tantos elementos *ErrType*como elementos *errnum*haya.  
  
 Un valor de *ErrType* de _RTC_ERRTYPE_IGNORE tiene un significado especial para `_CrtSetReportMode`; se omite el error.  
  
## <a name="return-value"></a>Valor devuelto  
 El valor anterior del tipo de error `type`.  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, todos los errores se establecen en *ErrType* = 1, que corresponde a **_CRT_ERROR**. Para más información sobre los tipos de errores predeterminados de tipos, como **_CRT_ERROR**, consulte [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).  
  
 Antes de poder llamar a esta función, primero debe llamar a una de las funciones de inicialización de comprobación de errores en tiempo de ejecución; vea [Uso de comprobaciones en tiempo de ejecución sin la biblioteca en tiempo de ejecución de C](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_RTC_SetErrorType`|\<rtcapi.h>|  
  
 Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vea también  
 [_RTC_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [Comprobar errores en tiempo de ejecución](../../c-runtime-library/run-time-error-checking.md)
