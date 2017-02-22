---
title: "Error del compilador C3367 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3367"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3367"
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3367
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función\_miembro\_estática': no se puede usar la función estática para crear un delegado sin enlazar.  
  
 Cuando se llama a un delegado sin enlazar, debe pasar una instancia de un objeto. Puesto que se llama a una función miembro estática a través del nombre de clase, solo puede crear una instancia de un delegado sin enlazar con una función miembro de instancia.  
  
 Para obtener más información, consulta [Delegados sin enlazar](../../misc/unbound-delegates.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3367.  
  
```  
// C3367.cpp // compile with: /clr ref struct R { void b() {} static void f() {} }; delegate void Del(R^); int main() { Del ^ a = gcnew Del(&R::b);   // OK Del ^ b = gcnew Del(&R::f);   // C3367 }  
```