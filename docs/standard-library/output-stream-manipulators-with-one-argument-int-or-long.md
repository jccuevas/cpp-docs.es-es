---
title: Manipuladores de flujos de salida con un argumento (int o long)
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
ms.openlocfilehash: e093512af2741329c58db0b613453f3388bacdf2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530997"
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>Manipuladores de flujos de salida con un argumento (int o long)

La biblioteca de clases iostream proporciona un conjunto de macros para crear manipuladores parametrizados. Manipuladores con un único **int** o **largo** argumento son un caso especial. Para crear un manipulador de flujo de salida que acepta un único **int** o **largo** argumento (al igual que `setw`), debe usar la macro _Smanip, que se define en \<iomanip >. Este ejemplo define un manipulador `fillblank` que inserta un número específico de espacios en blanco en la secuencia:

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

[Manipuladores personalizados con argumentos](../standard-library/custom-manipulators-with-arguments.md)<br/>
