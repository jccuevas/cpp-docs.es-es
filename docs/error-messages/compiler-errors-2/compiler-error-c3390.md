---
title: "Error del compilador C3390 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3390"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3390"
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3390
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type\_arg': argumento de tipo no válido para el parámetro genérico 'param' de 'generic\_type' genérico; debe ser un tipo de referencia  
  
 Se crearon instancias de un tipo genérico incorrectamente.  Compruebe la definición de tipo.  Para obtener más información, consulta [Genéricos](../../windows/generics-cpp-component-extensions.md).  
  
## Ejemplo  
 En el ejemplo siguiente, se crea con C\# un componente que contiene un tipo genérico, con ciertas restricciones que no se admiten al crear tipos genéricos en [!INCLUDE[vcprvclong](../../error-messages/compiler-errors-2/includes/vcprvclong_md.md)]. Para más información, vea [Restricciones de tipos de parámetros](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md).  
  
```  
// C3390.cs // compile with: /target:library // a C# program public class GR<C, V, N> where C : class where V : struct where N : new() {}  
```  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3390.  
  
```  
// C3390_b.cpp // compile with: /clr #using <C3390.dll> ref class R { R(int) {} }; value class V {}; ref struct N { N() {} }; int main () { GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type GR<R^, V, N^>^ gr2b;   // OK }  
```