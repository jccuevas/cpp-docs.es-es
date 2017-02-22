---
title: "Error del compilador C3072 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3072"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3072"
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Error del compilador C3072
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el operador 'operador' no se puede aplicar a una instancia de una clase ref  
  
 utilice el operador unario de '`operator`' para convertir una instancia de una clase ref en un tipo de identificador  
  
 Un tipo CLR requiere operadores CLR, no operadores nativos \(o estándar\).  Para obtener más información, vea [Operador de referencia de seguimiento](../../windows/tracking-reference-operator-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3072.  
  
```  
// C3072.cpp  
// compile with: /clr  
ref class R {};  
  
int main() {  
   R r1;  
   R^ r2 = &r1;   // C3072  
   R^ r3 = %r1;   // OK  
}  
```