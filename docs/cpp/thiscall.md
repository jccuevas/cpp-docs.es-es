---
title: "__thiscall | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__thiscall"
  - "__thiscall_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__thiscall (palabra clave) [C++]"
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __thiscall
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 La convención de llamada `__thiscall` se utiliza en funciones miembro y es la convención de llamada predeterminada que emplean las funciones miembro de C\+\+ que no utilizan argumentos de variable.  En `__thiscall`, el destinatario limpia la pila, lo que es imposible para las funciones `vararg`.  Los argumentos se insertan en la pila de derecha a izquierda; el puntero `this` se pasa a través del registro ECX, y no en la pila, en la arquitectura x86.  
  
 Un motivo para utilizar `__thiscall` son las clases cuyas funciones miembro utilizan `__clrcall` de forma predeterminada.  En ese caso, puede utilizar `__thiscall` para crear funciones miembro individuales que se puedan llamar desde código nativo.  
  
 Al compilar con [\/clr:pure](../build/reference/clr-common-language-runtime-compilation.md), todas las funciones y los punteros a función son `__clrcall` a menos que se especifique lo contrario.  
  
 En las versiones anteriores a Visual C\+\+ 2005, la convención de llamada thiscall no se podía especificar explícitamente en un programa, ya que `thiscall` no era una palabra clave.  
  
 Las funciones miembro `vararg` usan la convención de llamada `__cdecl`.  Todos los argumentos de función se insertan en la pila, colocándose el puntero `this` en el último lugar de la pila.  
  
 Como esta convención de llamada solo se aplica a C\+\+, no hay ningún esquema de decoración de nombres de C.  
  
 En equipos ARM y [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)], el compilador acepta y omite `__thiscall`.  
  
 En el caso de funciones de clase no estáticas, si la función se define fuera de línea, no es necesario especificar el modificador de convención de llamada en la definición fuera de línea.  Es decir, para los métodos miembro no estáticos de clase, en el momento de la definición se supone la convención de llamada especificada durante la declaración.  
  
## Ejemplo  
  
```  
// thiscall_cc.cpp  
// compile with: /c /clr:oldSyntax  
struct CMyClass {  
   void __thiscall mymethod();  
   void __clrcall mymethod2();  
};  
```  
  
## Específicos de Microsoft: END  
  
## Vea también  
 [Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)