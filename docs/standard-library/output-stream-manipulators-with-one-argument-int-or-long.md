---
title: Manipuladores de flujos de salida con un argumento (int o long)
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
ms.openlocfilehash: 93e4de25323514eb4105814b565dc3ddc3fbb737
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453007"
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>Manipuladores de flujos de salida con un argumento (int o long)

La biblioteca de clases iostream proporciona un conjunto de macros para crear manipuladores parametrizados. Los manipuladores con un solo argumento **int** o **Long** son un caso especial. Para crear un manipulador de flujo de salida que acepte un solo argumento **int** o `setw` **Long** (como), debe usar la macro _Smanip, que se \<define en iomanip >. Este ejemplo define un manipulador `fillblank` que inserta un número específico de espacios en blanco en la secuencia:

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
