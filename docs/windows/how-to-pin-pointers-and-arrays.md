---
title: "C&#243;mo: Anclar punteros y matrices | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [C++], anclaje"
  - "punteros, anclaje"
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# C&#243;mo: Anclar punteros y matrices
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Anclar un sub\- objeto definido en un objeto administrado tiene el efecto de anclaje el objeto completo.  Por ejemplo, si algún elemento de una matriz se ancla, después la matriz entera también se ancla.  No hay extensiones al lenguaje para declarar una matriz anclar.  Anclar una matriz, declara un puntero anclado a su tipo de elemento, y anclar uno de sus elementos.  
  
## Ejemplo  
  
### Código  
  
```  
// pin_ptr_array.cpp  
// compile with: /clr  
#include <stdio.h>  
using namespace System;  
  
int main() {  
   array<Byte>^ arr = gcnew array<Byte>(4);  
   arr[0] = 'C';  
   arr[1] = '+';  
   arr[2] = '+';  
   arr[3] = '\0';  
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned  
   unsigned char * cp = p;  
  
   printf_s("%s\n", cp); // bytes pointed at by cp  
                         // will not move during call  
}  
```  
  
### Resultados  
  
```  
++  
```  
  
## Vea también  
 [pin\_ptr \(C\+\+\/CLI\)](../Topic/pin_ptr%20\(C++-CLI\).md)