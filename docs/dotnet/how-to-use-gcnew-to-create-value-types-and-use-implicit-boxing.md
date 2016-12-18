---
title: "C&#243;mo: Usar gcnew para crear tipos de valor y usar la conversi&#243;n boxing impl&#237;cita | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "boxing (conversión), implícita"
  - "gcnew (palabra clave) [C++], crear tipos de valor"
  - "tipos de valor, crear"
ms.assetid: ceb48841-d6bd-47be-a167-57f44c961603
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Usar gcnew para crear tipos de valor y usar la conversi&#243;n boxing impl&#237;cita
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Mediante [gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md) en un tipo de valor creará un tipo de valor de conversión boxing, que después puede estar en el administrado, pila basura\- obtenida.  
  
## Ejemplo  
  
```  
// vcmcppv2_explicit_boxing4.cpp  
// compile with: /clr  
public value class V {  
public:  
   int m_i;  
   V(int i) : m_i(i) {}  
};  
  
public ref struct TC {  
   void do_test(V^ v) {  
      if (v != nullptr)  
         ;  
      else  
         ;  
   }  
};  
  
int main() {  
   V^ v = gcnew V(42);  
   TC^ tc = gcnew TC;  
   tc->do_test(v);  
}  
```  
  
## Vea también  
 [Conversión boxing](../windows/boxing-cpp-component-extensions.md)