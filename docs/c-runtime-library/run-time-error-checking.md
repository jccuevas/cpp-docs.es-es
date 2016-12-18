---
title: "Comprobar errores en tiempo de ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.runtime"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "comprobar errores en tiempo de ejecución"
  - "errores en tiempo de ejecución, comprobar"
ms.assetid: c965dd01-57ad-4a3c-b1d6-5aa04f920501
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Comprobar errores en tiempo de ejecuci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La biblioteca en tiempo de ejecución de C contiene funciones que las comprobaciones de errores en tiempo de ejecución admiten \(RTC\).  La comprobación de errores en tiempo de ejecución permite compilar el programa tales que ciertos tipos de errores en tiempo de ejecución se comunican.  Especifica cómo se notifican errores pero que se informa de las clases de errores.  Para obtener más información, vea [Comprobaciones de errores en tiempo de ejecución](../Topic/How%20to:%20Use%20Native%20Run-Time%20Checks.md).  
  
 Utilice las siguientes funciones para personalizar la manera en que el programa haga la comprobación de errores en tiempo de ejecución.  
  
### Comprobación de errores en tiempo de ejecución funciones  
  
|Función|Utilice|Equivalente de .NET Framework|  
|-------------|-------------|-----------------------------------|  
|[\_RTC\_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md)|Devuelve una descripción breve de un tipo de comprobación de errores en tiempo de ejecución.||  
|[\_RTC\_NumErrors](../c-runtime-library/reference/rtc-numerrors.md)|Devuelve el número total de errores que puedan detectar por las comprobaciones de errores en tiempo de ejecución.||  
|[\_RTC\_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md)|Señala una función como el controlador para la notificación de comprobaciones de errores en tiempo de ejecución.||  
|[\_RTC\_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md)|Asocia un error que sea detectado por las comprobaciones de errores en tiempo de ejecución con un tipo.||  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)   
 [\/RTC \(Comprobaciones de errores en tiempo de ejecución\)](../build/reference/rtc-run-time-error-checks.md)   
 [runtime\_checks](../preprocessor/runtime-checks.md)   
 [RTC sample](http://msdn.microsoft.com/es-es/b3415b09-f6fd-43dc-8c02-9a910bc2574e)   
 [Rutinas de depuración](../c-runtime-library/debug-routines.md)