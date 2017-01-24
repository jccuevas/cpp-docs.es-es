---
title: "valarray&lt;bool&gt; (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "valarray<bool>"
  - "valarray/std::valarray<bool>"
  - "std::valarray<bool>"
  - "std.valarray<bool>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "valarray<bool> (clase)"
ms.assetid: fc0e7121-4758-4ea5-86c3-f04448f04acf
caps.latest.revision: 14
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# valarray&lt;bool&gt; (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una versión especializada de la clase de plantilla **valarray\<Type\>** a los elementos de `bool`escrito.  
  
## Sintaxis  
  
```  
  
class valarray<bool>  
  
```  
  
## Ejemplo  
  
```  
// valarray_bool.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   valarray<bool> vaBool ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )   
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )   
      vaL [ i ] =  i;  
   for ( i = 0 ; i < 10 ; i++ )   
      vaR [ i ] =  i;  
  
   cout << "The initial Left valarray is: ( ";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaBool = ( vaL < vaR );  
   cout << "The result of the less-than comparison "  
   << "test is the\n valarray<bool>: ( ";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << vaBool [ i ] << " ";  
   cout << ")." << endl;  
}  
```  
  
  **El inicial Left valarray es: \(0 1 \-2 3 \-4 5 \-6 7 \-8 9\).**  
**El valarray derecho inicial es: \(0 1 2 3 4 5 6 7 8 9\).**  
**El resultado de menos\- que prueba de comparación es**  
 **valarraybool\<\>: \(0 0 1 0 1 0 1 0 1 0\).**   
## Requisitos  
 **Encabezado:** \<valarray\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [valarray \(Clase\)](../standard-library/valarray-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)