---
title: "Error del compilador C2274 | Microsoft Docs"
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
  - "C2274"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2274"
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2274
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': no es válido como lado derecho del operador '.'  
  
 El operando que aparece a la derecha de un operador de acceso a miembros \(.\) es un tipo.  
  
 Este error puede producirse al intentar el acceso a una conversión de tipos definida por el usuario.  Utilice la palabra clave `operator` entre el punto y `type`.  
  
 El código siguiente genera el error C2286:  
  
```  
// C2274.cpp  
struct MyClass {  
   operator int() {  
      return 0;  
   }  
};  
  
int main() {  
   MyClass ClassName;  
   int i = ClassName.int();   // C2274  
   int j = ClassName.operator int();   // OK  
}  
```