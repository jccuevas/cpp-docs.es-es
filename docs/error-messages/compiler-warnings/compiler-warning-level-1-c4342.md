---
title: Advertencia del compilador (nivel 1) C4342
ms.date: 11/04/2016
f1_keywords:
- C4342
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
ms.openlocfilehash: 439c4976f25688fd9220c3f58ceb933266b5f15c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187514"
---
# <a name="compiler-warning-level-1-c4342"></a>Advertencia del compilador (nivel 1) C4342

cambio de comportamiento: '*función*' llama a, pero se llamó a un operador de miembro en las versiones anteriores

En las versiones de Visual C++ antes de Visual Studio 2002, se llama a un miembro, pero este comportamiento se ha cambiado y ahora, el compilador busca a la mejor coincidencia en el ámbito de espacio de nombres.

Si se encontró un operador de miembro, el compilador no consideraría previamente cualquier espacio de nombres de los operadores de ámbito. Si hay una coincidencia mejor en el ámbito del espacio de nombres, el compilador actual llama correctamente, mientras que los compiladores anteriores no lo consideraría.

Después de que traslada correctamente el código a la versión actual, se debe deshabilitar esta advertencia.  El compilador puede proporcionar falsos positivos, generando esta advertencia para el código que no hay ningún cambio de comportamiento.

De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

El ejemplo siguiente genera C4342:

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