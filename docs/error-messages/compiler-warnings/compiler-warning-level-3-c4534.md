---
title: "Advertencia del compilador (nivel 3) C4534 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "c4534"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4534"
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (nivel 3) C4534
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'constructor' no será un constructor predeterminado para la clase 'clase' debido al argumento predeterminado  
  
 Una clase no administrada puede tener un constructor con parámetros que posean valores predeterminados, en cuyo caso el compilador lo utilizará como constructor predeterminado.  Una clase marcada con la palabra clave `value` no usará un constructor con valores predeterminados para sus parámetros como un constructor predeterminado.  
  
 Para obtener más información, vea [Clases y structs](../../windows/classes-and-structs-cpp-component-extensions.md).  
  
 El código siguiente genera el error C4534:  
  
```  
// C4534.cpp  
// compile with: /W3 /clr /WX  
value class MyClass {  
public:  
   int ii;  
   MyClass(int i = 9) {   // C4534, will not be the default constructor  
      i++;  
   }  
};  
  
int main() {  
   MyClass ^ xx = gcnew MyClass;  
   xx->ii = 0;  
}  
```