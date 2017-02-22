---
title: "Manipuladores de flujos de salida con un argumento (int o long) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "flujos de salida, manipuladores de argumentos int o long"
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Manipuladores de flujos de salida con un argumento (int o long)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La biblioteca de clases iostream proporciona un conjunto de macros para crear los manipuladores con parámetros.  Los manipuladores con solo `int` o argumento de `long` son un caso especial.  Para crear un manipulador del flujo de salida que acepte solo `int` o argumento de `long` \(como `setw`\), debe utilizar la macro de \_Smanip, que se define en \<iomanip\>.  Este ejemplo define un manipulador de `fillblank` que inserta un número especificado de espacios en blanco en la secuencia:  
  
## Ejemplo  
  
```  
// output_stream_manip.cpp  
// compile with: /GR /EHsc  
#include <iostream>  
#include <iomanip>  
using namespace std;  
  
void fb( ios_base& os, int l )  
{  
   ostream *pos = dynamic_cast<ostream*>(&os);  
   if (pos)  
   {  
      for( int i=0; i < l; i++ )  
      (*pos) << ' ';  
   };  
}  
  
_Smanip<int>  
   __cdecl fillblank(int no)  
   {     
   return (_Smanip<int>(&fb, no));  
   }  
  
int main( )  
{  
   cout << "10 blanks follow" << fillblank( 10 ) << ".\n";  
}  
```  
  
## Vea también  
 [Manipuladores personalizados con argumentos](../standard-library/custom-manipulators-with-arguments.md)