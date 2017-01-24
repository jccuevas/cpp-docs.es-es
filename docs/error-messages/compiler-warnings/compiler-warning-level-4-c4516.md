---
title: "Advertencia del compilador (nivel 4) C4516 | Microsoft Docs"
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
  - "C4516"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4516"
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4516
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase::símbolo' : las declaraciones de acceso han quedado obsoletas; las declaraciones using de miembros son una alternativa mejor  
  
 El comité de ANSI C\+\+ ha declarado obsoletas las declaraciones de acceso \(que modifican el acceso de un miembro en una clase derivada sin la palabra clave [using](../../cpp/using-declaration.md).  Puede que las declaraciones de acceso dejen de ser compatibles con las futuras versiones de C\+\+.  
  
 El código siguiente genera el error C4516:  
  
```  
// C4516.cpp  
// compile with: /W4  
class A  
{  
public:  
   void x(char);  
};  
  
class B : protected A  
{  
public:  
   A::x;  // C4516 on access-declaration  
   // use the following line instead  
   // using A::x; // using-declaration, ok  
};  
  
int main()  
{  
}  
```