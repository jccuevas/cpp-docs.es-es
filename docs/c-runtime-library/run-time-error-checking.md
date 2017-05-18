---
title: "Comprobación de errores en tiempo de ejecución | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.runtime
dev_langs:
- C++
helpviewer_keywords:
- run-time error checking
- run-time errors, checking
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
caps.latest.revision: 7
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
ms.translationtype: Human Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: eb9db9ea42d50faa6e7a693c95795036e650a760
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="run-time-error-checking"></a>Comprobar errores en tiempo de ejecución
La biblioteca de tiempo de ejecución de C contiene las funciones que admiten las comprobaciones de errores en tiempo de ejecución. La comprobación de errores en tiempo de ejecución permite compilar el programa de manera que se notifiquen determinados tipos de errores en tiempo de ejecución. El usuario especifica cómo se notifican los errores y qué tipos de errores se notifican. Para obtener más información, consulte [/RTC (Comprobaciones de errores en tiempo de ejecución)](http://msdn.microsoft.com/Library/dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1).  
  
 Utilice las siguientes funciones para personalizar la forma en que el programa realiza la comprobación de errores en tiempo de ejecución.  
  
### <a name="run-time-error-checking-functions"></a>Funciones de comprobación de errores en tiempo de ejecución  
  
|Función|Uso|  
|--------------|---------|  
|[_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|Devuelve una breve descripción de un tipo de comprobación de error en tiempo de ejecución.|  
|[_RTC_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|Devuelve el número total de errores que se pueden detectar mediante las comprobaciones de errores en tiempo de ejecución.|  
|[_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|Designa una función como el controlador para notificar comprobaciones de errores en tiempo de ejecución.|  
|[_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|Asocia un error que se detecta mediante comprobaciones de errores en tiempo de ejecución con un tipo.|  
  
## <a name="see-also"></a>Vea también  
 [Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)   
 [RTC (Comprobaciones de errores en tiempo de ejecución)](../build/reference/rtc-run-time-error-checks.md)   
 [runtime_checks](../preprocessor/runtime-checks.md)   
 [RTC sample](http://msdn.microsoft.com/en-us/b3415b09-f6fd-43dc-8c02-9a910bc2574e)  (Ejemplo de RTC)  
 [Rutinas de depuración](../c-runtime-library/debug-routines.md)
