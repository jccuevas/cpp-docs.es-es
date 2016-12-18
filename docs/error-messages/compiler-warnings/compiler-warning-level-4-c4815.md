---
title: "Advertencia del compilador (nivel 4) C4815 | Microsoft Docs"
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
  - "C4815"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4815"
ms.assetid: 99081928-d7d5-4dce-b4af-7c6a151bfac0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4815
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': la matriz de tamaño cero del objeto de pila no tendrá elementos \(a menos que el objeto sea una función de agregado que se haya agregado inicializada\)  
  
 Una matriz con un número de elementos no definido \(matriz de tamaño cero\) es el último miembro de un tipo y un objeto del tipo se ha creado en la pila.  No se asignará memoria para la matriz.  Si necesita un constructor útil, puede asignar memoria para el struct en el montón.  
  
 El código siguiente genera el error C4815:  
  
```  
// C4815.cpp  
// compile with: /W4  
#include <memory>  
#pragma warning(disable : 4200)  
struct S1  
{  
   int i;  
   char cArr[];  
};  
  
S1 s1_glb;   // C4815 stack object with zero-array (not aggregate inited)  
// try the following line instead  
// S1 s1_glb = { 0, 0, 0 };  
  
struct S2  
{  
   S2(int _i) : i(_i) {}  
   int i;  
   char cArr[];  
};  
  
S2 s2_glb1(10);   // C4815  
// try the following line instead  
// S2 s2_glb1 = { 10 };  // to work, comment the constructor  
  
int main()  
{  
   S1 s1_loc1;   // C4815  
   // try the following line instead  
   // S1 s1_loc1 = { 0 };  
  
   S1 s1_loc2 = { 1, { 'a', 'b', 'c' } };  
  
   S1 s1_loc3 = s1_loc2;   // C4815 truncation when copy ctor called  
   // truncation if call a compiler-generated copy constructor  
   // to copy a struct with a zero sized array in it  
   s1_loc1;  
   s1_loc2;  
   s1_loc3;  
  
   // allocate memory for struct on heap  
   int nEle = 10;   // allocate 10 chars for char array  
   void * pV = malloc (sizeof(S2) + nEle * sizeof(char));  
   S2 *pS1 = new (pV) S2(nEle);  
   pS1;  
}  
```