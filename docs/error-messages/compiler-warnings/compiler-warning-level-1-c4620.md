---
title: "Advertencia del compilador (nivel 1) C4620 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4620"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4620"
ms.assetid: fed29934-b797-47e8-bbea-c7e5f8dd6e93
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4620
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se encontró ninguna forma postfija de 'operador \+\+' para el tipo 'tipo'; con la forma de prefijo.  
  
 No hay ningún operador de incremento postfijo definido para el tipo dado. El compilador usa el operador prefijo sobrecargado.  
  
 Esta advertencia puede evitarse definiendo un operador `++` postfijo. Cree una versión de dos argumentos del operador `++` tal como se muestra aquí:  
  
```  
// C4620.cpp // compile with: /W1 class A { public: A(int nData) : m_nData(nData) { } A operator++() { m_nData -= 1; return *this; } // A operator++(int) // { //    A tmp = *this; //    m_nData -= 1; //    return tmp; // } private: int m_nData; }; int main() { A a(10); ++a; a++;   // C4620 }  
```