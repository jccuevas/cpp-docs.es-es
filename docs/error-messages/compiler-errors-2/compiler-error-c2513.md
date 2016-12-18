---
title: "Error del compilador C2513 | Microsoft Docs"
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
  - "C2513"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2513"
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2513
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo' : no hay ninguna variable declarada antes de '\='  
  
 El especificador de tipo aparece en la declaración sin identificador de variable.  
  
 El código siguiente genera el error C2513:  
  
```  
// C2513.cpp  
int main() {  
   int = 9;   // C2513  
   int i = 9;   // OK  
}  
```  
  
 Este error también puede producirse como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003: ya no se permite la inicialización de un tipo typedef.  El estándar no permite la inicialización de un tipo typedef; ahora se genera un error de compilación.  
  
```  
// C2513b.cpp  
// compile with: /c  
typedef struct S {  
   int m_i;  
} S = { 1 };   // C2513  
// try the following line instead  
// } S;  
```  
  
 Una alternativa sería eliminar `typedef` y definir una variable con una lista de inicializador de agregado, pero no es recomendable porque creará una variable con el mismo nombre que el tipo y ocultará el nombre del tipo.