---
title: Manipuladores de flujos de salida con un argumento (int o long) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c13d6352fcd3b2df26e9585b74e17b549106d19b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>Manipuladores de flujos de salida con un argumento (int o long)
La biblioteca de clases iostream proporciona un conjunto de macros para crear manipuladores parametrizados. Los manipuladores con un solo argumento `int` o `long` son un caso especial. Para crear un manipulador de flujo de salida que acepte un solo argumento `int` o `long` (como `setw`), debe usar la macro _Smanip, que se define en \<iomanip>. Este ejemplo define un manipulador `fillblank` que inserta un número específico de espacios en blanco en la secuencia:  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
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
  
## <a name="see-also"></a>Vea también  
 [Manipuladores personalizados con argumentos](../standard-library/custom-manipulators-with-arguments.md)

