---
title: "Error del compilador C3288 | Microsoft Docs"
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
  - "C3288"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3288"
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3288
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo' : desreferenciación no válida a un tipo de identificador  
  
 El compilador ha detectado una desreferenciación no válida a un tipo de identificador.  Puede desreferenciar un tipo de identificador y asignarlo a una referencia.  Para obtener más información, vea [Operador de referencia de seguimiento](../../windows/tracking-reference-operator-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3288.  
  
```  
// C3288.cpp  
// compile with: /clr  
ref class R {};  
int main() {  
   *(System::Object^) nullptr;   // C3288  
  
// OK  
   (System::Object^) nullptr;   // OK  
   R^ r;  
   R% pr = *r;  
}  
```