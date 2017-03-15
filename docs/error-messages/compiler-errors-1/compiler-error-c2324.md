---
title: "Error del compilador C2324 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2324"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2324"
ms.assetid: 215f0544-85b0-452d-825f-17a388b6a61c
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C2324
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : no se esperaba a la derecha de 'nombre'  
  
 Se llama a un destructor que utiliza un identificador incorrecto.  
  
 El código siguiente genera el error C2324:  
  
```  
// C2324.cpp  
class A {};  
typedef A* pA_t;  
int i;  
  
int main() {  
   pA_t * ppa = new pA_t;  
   ppa->~i;   // C2324  
   ppa->~pA_t();   // OK  
}  
```