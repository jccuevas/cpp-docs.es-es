---
title: _RTC_SetErrorFuncW | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _RTC_SetErrorFuncW
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
- _RTC_SetErrorFuncW
- RTC_SetErrorFuncW
dev_langs: C++
helpviewer_keywords:
- run-time errors
- RTC_SetErrorFuncW function
- _RTC_error_fnW typedef
- _RTC_SetErrorFuncW function
- RTC_error_fnW typedef
ms.assetid: b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4cd751c88e5af3fde5c0f5415520a2c634a1958e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="rtcseterrorfuncw"></a>_RTC_SetErrorFuncW
Designa una función como el controlador de la notificación de comprobaciones de errores en tiempo de ejecución (RTC).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      _RTC_error_fnW _RTC_SetErrorFuncW(  
   _RTC_error_fnW function   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `function`  
 La dirección de la función que controlará las comprobaciones de errores en tiempo de ejecución.  
  
## <a name="return-value"></a>Valor devuelto  
 La función de error definida previamente o `NULL` si no hay ninguna función definida con anterioridad.  
  
## <a name="remarks"></a>Comentarios  
 En el nuevo código, use solo `_RTC_SetErrorFuncW`. `_RTC_SetErrorFunc` solo se incluye en la biblioteca para una compatibilidad con versiones anteriores.  
  
 La devolución de llamada `_RTC_SetErrorFuncW` se aplica solo al componente en el que estaba vinculado, pero no de forma global.  
  
 Asegúrese de que la dirección que pasa a `_RTC_SetErrorFuncW` es la de una función de control de errores válida.  
  
 Si se ha asignado un tipo de -1 a un error mediante el uso de [_RTC_SetErrorType](../../c-runtime-library/reference/rtc-seterrortype.md), no se llama a la función de control de errores.  
  
 Antes de poder llamar a esta función, primero debe llamar a una de las funciones de inicialización de la comprobación de errores en tiempo de ejecución. Para obtener más información, consulta [Using Run-Time Checks Without the C Run-Time Library](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library).  
  
 **_RTC_error_fnW** se define del siguiente modo:  
  
 **typedef int (__cdecl \*_RTC_error_fnW)(int**  `errorType` **, const wchar_t \*** *filename* **, int**  *linenumber* **, const wchar_t \*** `moduleName` **, const wchar_t \*** *format* **, ...);**  
  
 donde:  
  
 `errorType`  
 El tipo de error que especifica [_RTC_SetErrorType](../../c-runtime-library/reference/rtc-seterrortype.md).  
  
 *filename*  
 El archivo de origen donde se produjo el error, o null si no hay información de depuración.  
  
 *linenumber*  
 La línea de *filename* donde se produjo el error, o 0 si no hay información de depuración disponible.  
  
 `moduleName`  
 El nombre del archivo DLL o del ejecutable en el que se produjo el error.  
  
 *format*  
 cadena de estilo printf para mostrar un mensaje de error, usando los parámetros restantes. El primer argumento de VA_ARGLIST es el número de errores de RTC que se produjeron.  
  
 Para ver un ejemplo en el que se muestra cómo usar **_RTC_error_fnW**, vea [Personalización de las comprobaciones nativas en tiempo de ejecución](/visualstudio/debugger/native-run-time-checks-customization).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_RTC_SetErrorFuncW`|\<rtcapi.h>|  
  
 Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vea también  
 [_CrtDbgReport, _CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)   
 [Comprobar errores en tiempo de ejecución](../../c-runtime-library/run-time-error-checking.md)