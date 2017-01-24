---
title: "Error del compilador C3392 | Microsoft Docs"
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
  - "C3392"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3392"
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3392
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'arg\_tipo': argumento de tipo no válido para el parámetro genérico 'parámetro' del 'tipo\_genérico' genérico, debe tener un constructor sin parámetros público.  
  
 Se crearon incorrectamente instancias de un tipo genérico.  Compruebe la definición de tipo.  Para obtener más información, vea [Genéricos](../../windows/generics-cpp-component-extensions.md).  
  
## Ejemplo  
 En el ejemplo siguiente, se crea con C\# un componente que contiene un tipo genérico, con ciertas restricciones que no se admiten al crear tipos genéricos en [!INCLUDE[vcprvclong](../../error-messages/compiler-errors-2/includes/vcprvclong_md.md)]. Para obtener más información, vea [Restricciones de tipos de parámetros](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md).  
  
```  
// C3392.cs // compile with: /target:library // a C# program public class GR<C, V, N> where C : class where V : struct where N : new() {}  
```  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3392.  
  
```  
// C3392_b.cpp // compile with: /clr #using <C3392.dll> ref class R { R(int) {} }; ref class N { N() {} }; value class V {}; ref class N2 { public: N2() {} }; ref class R2 { public: R2() {} }; int main () { GR<R^, V, N^>^ gr1;   // C3392 GR<R^, V, N2^>^ gr1a;   // OK GR<R^, N^, N^>^ gr3;   // C3392 GR<R^, V, N2^>^ gr3a;   // OK GR<R^, V, R^>^ gr4;   // C3392 GR<R^, V, R2^>^ gr4a;   // OK }  
```