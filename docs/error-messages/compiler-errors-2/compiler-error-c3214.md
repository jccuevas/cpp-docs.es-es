---
title: "Error del compilador C3214 | Microsoft Docs"
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
  - "C3214"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3214"
ms.assetid: 49ee4a9a-2549-4adb-9d3a-38e154303c2e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3214
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': el argumento de tipo no válido para el parámetro genérico 'param' de 'generic\_type' genérico no cumple la restricción 'constraint'  
  
 Se especificó el tipo de creación de instancias de una clase genérica que no cumple la restricción de la clase genérica.  
  
 El ejemplo siguiente genera la advertencia C3214:  
  
```  
// C3214.cpp // compile with: /clr interface struct A {}; generic <class T> where T : A ref class C {}; ref class X : public A {}; int main() { C<int>^ c = new C<int>;   // C3214 C<X ^> ^ c2 = new C<X^>;   // OK }  
```