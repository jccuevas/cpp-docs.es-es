---
title: "Uso de registros | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: ce58e2cf-afd3-4068-980e-28a209298265
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Uso de registros
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La arquitectura de [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] proporciona 16 registros de índole general \(a los que nos referiremos en adelante como registros de enteros\), así como otros 16 registros de XMM\/YMM, disponibles para el uso de puntos flotantes.  Los registros volátiles son registros residuales que el llamador da por hecho que van a destruirse a lo largo de la llamada.  En cuanto a los registros no volátiles, es necesarios conservar sus valores a lo largo de la llamada de función, y el destinatario de la llamada debe guardarlos si se usan.  
  
 En la siguiente tabla se explica el uso de cada registro en las llamadas de función:  
  
||||  
|-|-|-|  
|Registro|Estado|Uso|  
|RAX|Volátil|Registro de valor devuelto|  
|RCX|Volátil|Primer argumento de entero|  
|RDX|Volátil|Segundo argumento de entero|  
|R8|Volátil|Tercer argumento de entero|  
|R9|Volátil|Cuarto argumento de entero|  
|R10:R11|Volátil|El llamador debe conservarlo según sea necesario; utilizado en instrucciones syscall\/sysret|  
|R12:R15|No volátil|El destinatario de la llamada debe conservarlo|  
|RDI|No volátil|El destinatario de la llamada debe conservarlo|  
|RSI|No volátil|El destinatario de la llamada debe conservarlo|  
|RBX|No volátil|El destinatario de la llamada debe conservarlo|  
|RBP|No volátil|Se puede usar como un puntero de marco; el destinatario de la llamada debe conservarlo según sea necesario|  
|RSP|No volátil|Puntero de pila|  
|XMM0, YMM0|Volátil|Primer argumento de FP; primer argumento de tipo vectorial cuando se usa `__vectorcall`|  
|XMM1, YMM1|Volátil|Segundo argumento de FP; segundo argumento de tipo vectorial cuando se usa `__vectorcall`|  
|XMM2, YMM2|Volátil|Tercer argumento de FP; tercer argumento de tipo vectorial cuando se usa `__vectorcall`|  
|XMM3, YMM3|Volátil|Cuarto argumento de FP; cuarto argumento de tipo vectorial cuando se usa `__vectorcall`|  
|XMM4, YMM4|Volátil|El llamador debe conservarlo según sea necesario; quinto argumento de tipo vectorial cuando se usa `__vectorcall`|  
|XMM5, YMM5|Volátil|El llamador debe conservarlo según sea necesario; sexto argumento de tipo vectorial cuando se usa `__vectorcall`|  
|XMM6:XMM15, YMM6:YMM15|No volátil \(XMM\), volátil \(mitad superior de YMM\)|El destinatario de la llamada debe conservarlo según sea necesario.  El llamador debe conservar los registros de YMM según sea necesario.|  
  
## Vea también  
 [Convenciones de software x64](../build/x64-software-conventions.md)   
 [\_\_vectorcall](../cpp/vectorcall.md)