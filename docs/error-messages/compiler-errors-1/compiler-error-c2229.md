---
title: "Error del compilador C2229 | Microsoft Docs"
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
  - "C2229"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2229"
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2229
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

tipo 'identificador' tiene una matriz de tamaño cero no válida  
  
 Un miembro de un struct o campo de bits contiene una matriz de tamaño cero que no es el último miembro.  
  
 Al ser posible tener una matriz de tamaño cero como último miembro del struct, se debe especificar su tamaño al asignar el struct.  
  
 Si la matriz de tamaño cero no es el último miembro del struct, el compilador no puede calcular el desplazamiento para los campos restantes.  
  
 El código siguiente genera el error C2229:  
  
```  
// C2229.cpp  
struct S {  
   int a[0];  // C2229  zero-sized array  
   int b[1];  
};  
  
struct S2 {  
   int a;  
   int b[0];  
};  
  
int main() {  
   // allocate 7 elements for b field  
   S2* s2 = (S2*)new int[sizeof(S2) + 7*sizeof(int)];  
   s2->b[6] = 100;  
}  
```