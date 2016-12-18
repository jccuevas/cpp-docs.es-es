---
title: "Error del compilador C3622 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3622"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3622"
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3622
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase' : no se puede crear una instancia de una clase declarada como 'palabra clave'  
  
 Se ha intentado crear una instancia de una clase marcada como [abstractas](../../windows/abstract-cpp-component-extensions.md) \(o [\_\_abstract](../../misc/abstract.md)\).  Una clase marcada como abstract puede ser una clase base, pero no se pueden crear instancias de ella.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3622.  
  
```  
// C3622.cpp  
// compile with: /clr  
ref class a abstract {};  
  
int main() {  
   a aa;   // C3622  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3622.  
  
```  
// C3622_b.cpp  
// compile with: /clr:oldSyntax  
__abstract class a {  
};  
int main() {  
   a aa;   // C3622  
}  
```