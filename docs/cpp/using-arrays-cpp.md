---
title: "Utilizar matrices (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [C++]"
ms.assetid: 7818a7fe-7e82-4881-a3d1-7d25162b7fc7
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizar matrices (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se puede obtener acceso a los elementos individuales de una matriz mediante el operador de subíndice de matriz \(`[ ]`\).  Si se utiliza una matriz unidimensional en una expresión que no tiene subíndice, el nombre de la matriz se evalúa como un puntero al primer elemento de la matriz.  
  
```  
// using_arrays.cpp  
int main() {  
   char chArray[10];  
   char *pch = chArray;   // Evaluates to a pointer to the first element.  
   char   ch = chArray[0];   // Evaluates to the value of the first element.  
   ch = chArray[3];   // Evaluates to the value of the fourth element.  
}  
```  
  
 Cuando se utilizan matrices multidimensionales, se pueden emplear varias combinaciones en las expresiones.  
  
```  
// using_arrays_2.cpp  
// compile with: /EHsc /W1  
#include <iostream>  
using namespace std;  
int main() {  
   double multi[4][4][3];   // Declare the array.  
   double (*p2multi)[3];  
   double (*p1multi);  
  
   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.  
   p2multi = multi[3];               // Make p2multi point to  
                                     // fourth "plane" of multi.  
   p1multi = multi[3][2];            // Make p1multi point to  
                                     // fourth plane, third row  
                                     // of multi.  
}  
```  
  
 En el código anterior, `multi` es una matriz tridimensional de tipo `double`.  El puntero `p2multi` apunta a una matriz de tipo `double` de tamaño tres.  En este ejemplo, la matriz se utiliza con uno, dos y tres subíndices.  Aunque es más frecuente especificar todos los subíndices, como en la instrucción `cout`, a veces es útil seleccionar un subconjunto concreto de elementos de la matriz, como se muestra en las instrucciones que hay después de `cout`.  
  
## Vea también  
 [Matrices](../cpp/arrays-cpp.md)