---
title: Advertencia del compilador (nivel 1) C4342
ms.date: 11/04/2016
f1_keywords:
- C4342
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
ms.openlocfilehash: 8ac00d3d57f8cf7d6c85f3106dbe9b8c3cb9adf0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162925"
---
# <a name="compiler-warning-level-1-c4342"></a>Advertencia del compilador (nivel 1) C4342

cambio de comportamiento: se llamó a '*función*', pero se llamó a un operador de miembro en versiones anteriores

En las versiones de C++ visual anteriores a visual Studio 2002, se llamó a un miembro, pero se ha cambiado este comportamiento y el compilador ahora encuentra la mejor coincidencia en el ámbito de espacio de nombres.

Si se encuentra un operador de miembro, el compilador no consideraría anteriormente ningún operador de ámbito de espacio de nombres. Si hay una coincidencia mejor en el ámbito del espacio de nombres, el compilador actual lo llama correctamente, mientras que los compiladores anteriores no lo consideran.

Esta advertencia debe deshabilitarse después de que el código se haya trasladado correctamente a la versión actual.  El compilador puede proporcionar falsos positivos y generar esta advertencia para el código en el que no hay ningún cambio de comportamiento.

De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

En el ejemplo siguiente se genera C4342:

```cpp
// C4342.cpp
// compile with: /EHsc /W1
#include <fstream>
#pragma warning(default: 4342)
using namespace std;
struct X : public ofstream {
   X();
};

X::X() {
   open( "ofs_bug_ev.txt." );
   if ( is_open() ) {
      *this << "Text" << "<-should be text" << endl;   // C4342
      *this << ' ' << "<-should be space symbol" << endl;   // C4342
   }
}

int main() {
   X b;
   b << "Text" << "<-should be text" << endl;
   b << ' ' << "<-should be space symbol" << endl;
}
```
