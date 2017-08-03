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
ms.sourcegitcommit: 3c1955bece0c8cdadb4a151ee06fa006402666a4
ms.openlocfilehash: 3aa56b70b02500998665289e69480570cfa39166
ms.contentlocale: es-es
ms.lasthandoff: 06/08/2017

---
# <a name="run-time-error-checking"></a>Comprobar errores en tiempo de ejecución
La biblioteca de tiempo de ejecución de C contiene las funciones que admiten las comprobaciones de errores en tiempo de ejecución. La comprobación de errores en tiempo de ejecución permite compilar el programa de manera que se notifiquen determinados tipos de errores en tiempo de ejecución. El usuario especifica cómo se notifican los errores y qué tipos de errores se notifican. Para más información, vea [Cómo: Utilizar comprobaciones nativas en tiempo de ejecución](/visualstudio/debugger/how-to-use-native-run-time-checks).  
  
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
 [Rutinas de depuración](../c-runtime-library/debug-routines.md)
