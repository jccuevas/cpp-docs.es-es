---
title: "Error del compilador C2764 | Microsoft Docs"
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
  - "C2764"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2764"
ms.assetid: 3754f5af-e094-4425-be20-d0c9a9b5baec
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2764
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'parámetro' : parámetro de plantilla no utilizado o deducible en la especialización parcial 'especialización'  
  
 No se ha utilizado un parámetro de plantilla en una especialización parcial.  Esto hace que la especificación parcial quede inutilizable, ya que no se puede deducir el parámetro de plantilla.  
  
## Ejemplo  
 El código siguiente genera el error C2764:  
  
```  
// C2764.cpp  
#include <stdio.h>  
template <class T1, class T2>  
struct S  {  
   int m_i;  
};  
  
template <class T1, class T2>  
struct S<int, T2*> {   // C2764  
// try the following line instead  
// struct S<T1(*)(T2), T2*> {  
   char m_c;  
};  
  
int main() {  
   S<int, char> s1;  
   S<void (*)(short), short *> s2;  
   s2.m_c = 10;  
   s1.m_i = s2.m_c;  
   printf_s("%d\n", s1.m_i);  
}  
```