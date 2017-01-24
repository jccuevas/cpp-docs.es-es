---
title: "conform | Microsoft Docs"
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
  - "conform_CPP"
  - "vc-pragma.conform"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "conform (pragma)"
  - "forScope conform (pragma)"
  - "pragma (directivas), conform"
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# conform
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Especifica el comportamiento en tiempo de ejecución de la opción del compilador [\/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md).  
  
## Sintaxis  
  
```  
#pragma conform(name [, show ] [, on | off ] [ [, push | pop ] [, identifier ] ] )  
```  
  
#### Parámetros  
 *name*  
 Especifica el nombre de la opción del compilador que se va a modificar.  El único valor válido para *name* es `forScope`.  
  
 **show** \(opcional\)  
 Hace que el valor actual de *name* \(true o false\) se muestre mediante un mensaje de advertencia durante la compilación.  Por ejemplo: `#pragma conform(forScope, show)`.  
  
 **on, off**\(opcional\)  
 Al establecer *name* en **on** se habilita la opción del compilador [\/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md).  El valor predeterminado es **off**.  
  
 **push** \(opcional\)  
 Inserta el valor actual de *name* en la pila interna del compilador.  Si se especifica *identifier*, puede especificar el valor de **on** o de **off** para que *name* se inserte en la pila.  Por ejemplo: `#pragma conform(forScope, push, myname, on)`.  
  
 **pop** \(opcional\)  
 Establece el valor de *name* en el valor situado en la parte superior de la pila interna del compilador y luego extrae la pila.  Si el identificador se especifica con **pop**, la pila se vuelve a extraer hasta encontrar el registro con *identifier*, que también se extrae; el valor actual de *name* en el registro siguiente de la pila se convierte en el nuevo valor de *name*.  Si especifica pop con un *identifier* que no está en un registro de la pila, se omite **pop**.  
  
 *identifier*\(opcional\)  
 Se puede incluir con un comando **push** o **pop**.  Si se utiliza *identifier*, también se puede usar un especificador **on** u **off**.  
  
## Ejemplo  
  
```  
// pragma_directive_conform.cpp  
// compile with: /W1  
// C4811 expected  
#pragma conform(forScope, show)  
#pragma conform(forScope, push, x, on)  
#pragma conform(forScope, push, x1, off)  
#pragma conform(forScope, push, x2, off)  
#pragma conform(forScope, push, x3, off)  
#pragma conform(forScope, show)  
#pragma conform(forScope, pop, x1)  
#pragma conform(forScope, show)  
  
int main() {}  
```  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)