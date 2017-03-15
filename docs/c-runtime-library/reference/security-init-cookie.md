---
title: "__security_init_cookie | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__security_init_cookie"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "security_init_cookie"
  - "__security_init_cookie"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__security_init_cookie (función)"
  - "cookie de seguridad global"
  - "cookie de seguridad [C++]"
  - "security_init_cookie (función)"
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __security_init_cookie
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Inicializa la cookie de seguridad global.  
  
## Sintaxis  
  
```  
void __security_init_cookie(void);  
```  
  
## Comentarios  
 La cookie de seguridad global se usa para la protección de saturación del búfer en código compilado con [\/GS \(Comprobación de seguridad del búfer\)](../../build/reference/gs-buffer-security-check.md) y en código que usa el control de excepciones.  En la entrada a una función con protección de saturación, la cookie se coloca en la pila y, en la salida, el valor de la pila se compara con la cookie global.  Cualquier diferencia en la comparación indica que se ha producido una saturación del búfer y da lugar a la finalización inmediata del programa.  
  
 Normalmente, el CRT llama a `__security_init_cookie` al inicializarse.  Si se omite la inicialización de CRT \(por ejemplo, si utiliza [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) para especificar un punto de entrada\), se deberá llamar a `__security_init_cookie` explícitamente.  Si no se llama a `__security_init_cookie`, la cookie de seguridad global se configura en un valor predeterminado y se pone en peligro la protección de saturación del búfer  Dado que un atacante puede aprovechar este valor de cookie predeterminado para invalidar las comprobaciones de saturación del búfer, se recomienda que llame siempre a `__security_init_cookie` al definir su propio punto de entrada.  
  
 La llamada a `__security_init_cookie` se debe hacer antes de especificar ninguna función de protección contra saturación, ya que de lo contrario se detecta una saturación del búfer falsa.  Para obtener más información, vea [Error en tiempo de ejecución de C R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md).  
  
## Ejemplo  
 Consulte los ejemplos de [Error en tiempo de ejecución de C R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`__security_init_cookie`|\<process.h\>|  
  
 `__security_init_cookie` es una extensión de Microsoft de la biblioteca estándar en tiempo de ejecución de C.  Para obtener información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Solo se debe llamar a esta función desde código nativo, no administrado.  
  
## Vea también  
 [Comprobación de seguridad exhaustiva del compilador](http://go.microsoft.com/fwlink/?linkid=7260)