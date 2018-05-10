---
title: Manipuladores de flujos de salida con un argumento (int o long) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3238ffcbd03f40c6eac0423d0212a65719fb33d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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

[Manipuladores personalizados con argumentos](../standard-library/custom-manipulators-with-arguments.md)<br/>
