---
title: "Paso de argumentos y convenciones de nomenclatura | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pasar argumentos [C++], convenciones"
  - "argumentos [C++], asignar nombre"
  - "argumentos [C++], pasar"
  - "argumentos [C++], de ampliación"
  - "convenciones de código, argumentos"
  - "convenciones [C++], nombres de argumento"
  - "convenciones de nomenclatura [C++], argumentos"
  - "pasar argumentos, convenciones"
  - "registros, valores devueltos"
  - "thiscall (palabra clave) [C++]"
ms.assetid: de468979-eab8-4158-90c5-c198932f93b9
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Paso de argumentos y convenciones de nomenclatura
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Los compiladores de Visual C\+\+ permiten especificar convenciones para pasar argumentos y valores devueltos entre funciones y llamadores.  No todas las convenciones están disponibles en todas las plataformas compatibles y algunas convenciones utilizan implementaciones específicas de la plataforma.  En la mayoría de los casos, se omiten palabras clave o modificadores de compilador que especifican una convención no compatible en una plataforma concreta y se usa la convención predeterminada de la plataforma.  
  
 En plataformas x86, todos los argumentos se amplían a 32 bits cuando se pasan.  Los valores devueltos también se amplían a 32 bits y se devuelven en el registro EAX, salvo las estructuras de 8 bytes, que se devuelven en el par de registros EDX:EAX.  Las estructuras de mayor tamaño se devuelven en el registro EAX como punteros a estructuras de devolución ocultas.  Los parámetros se insertan en la pila de derecha a izquierda.  Las estructuras distintas de POD no se devolverán en registros.  
  
 El compilador genera código de prólogo y epílogo para guardar y restaurar los registros ESI, EDI, EBX y EBP, si se usan en la función.  
  
> [!NOTE]
>  Cuando se devuelve un struct, una unión o una clase desde una función por valor, todas las definiciones del tipo deben ser iguales; de lo contrario, se puede producir un error en el programa en tiempo de ejecución.  
  
 Para obtener información sobre la definición de código propio de epílogo y prólogo de la función, vea [Llamadas a funciones naked](../cpp/naked-function-calls.md).  
  
 Para obtener información sobre las convenciones de llamada predeterminadas en el código destinado a plataformas x64, vea [Información general sobre las convenciones de llamada x64](../build/overview-of-x64-calling-conventions.md).  Para obtener información sobre problemas de convención de llamada en código destinado a plataformas ARM, vea [Problemas comunes de migración de ARM en Visual C\+\+](../build/common-visual-cpp-arm-migration-issues.md).  
  
 El compilador de Visual C\/C\+\+ admite las siguientes convenciones de llamada.  
  
|Palabra clave|Limpieza de la pila|Paso de parámetros|  
|-------------------|-------------------------|------------------------|  
|[\_\_cdecl](../cpp/cdecl.md)|Llamador|Inserta parámetros en la pila, en orden inverso \(de derecha a izquierda\)|  
|[\_\_clrcall](../cpp/clrcall.md)|no disponible|Carga parámetros en la pila de expresiones CLR en orden \(de izquierda a derecha\).|  
|[\_\_stdcall](../cpp/stdcall.md)|Destinatario|Inserta parámetros en la pila, en orden inverso \(de derecha a izquierda\)|  
|[\_\_fastcall](../cpp/fastcall.md)|Destinatario|Almacenado en los registros y luego insertado en la pila|  
|[\_\_thiscall](../cpp/thiscall.md)|Destinatario|Insertado en la pila; puntero **this** almacenado en ECX|  
|[\_\_vectorcall](../cpp/vectorcall.md)|Destinatario|Almacenado en registros y luego insertado en la pila en orden inverso \(de derecha a izquierda\)|  
  
 Para obtener información relacionada, vea [Convenciones de llamada obsoletas](../cpp/obsolete-calling-conventions.md).  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Convenciones de llamada](../cpp/calling-conventions.md)