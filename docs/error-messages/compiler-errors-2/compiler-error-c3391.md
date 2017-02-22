---
title: "Error del compilador C3391 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3391"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3391"
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3391
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type\_arg': argumento de tipo no válido para el parámetro genérico 'param' de 'generic\_type' genérico; debe ser un tipo de valor que no acepte valores NULL  
  
 Se crearon instancias de un tipo genérico incorrectamente.  Compruebe la definición de tipo.  Para obtener más información, vea <xref:System.Nullable> y [Genéricos](../../windows/generics-cpp-component-extensions.md).  
  
## Ejemplo  
 En el ejemplo siguiente, se crea con C\# un componente que contiene un tipo genérico, con ciertas restricciones que no se admiten al crear tipos genéricos en [!INCLUDE[vcprvclong](../../error-messages/compiler-errors-2/includes/vcprvclong_md.md)]. Para más información, vea [Restricciones de tipos de parámetros](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md).  
  
```  
// C3391.cs // compile with: /target:library // a C# program public class GR<N> where N : struct {}  
```  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3391.  
  
```  
// C3391_b.cpp // compile with: /clr #using <C3391.dll> using namespace System; value class VClass {}; int main() { GR< Nullable<VClass> >^ a = gcnew GR< Nullable<VClass> >();   // C3391 can't be Nullable GR<VClass>^ aa = gcnew GR<VClass>();   // OK }  
```