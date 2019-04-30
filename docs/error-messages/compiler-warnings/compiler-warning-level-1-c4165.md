---
title: Compilador advertencia (nivel 1) C4165
ms.date: 11/04/2016
f1_keywords:
- C4165
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
ms.openlocfilehash: 4d6377730e262efafb38f5e714989e9075a77a04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391743"
---
# <a name="compiler-warning-level-1-c4165"></a>Compilador advertencia (nivel 1) C4165

'HRESULT' se está convirtiendo en 'bool'; ¿está seguro de que desea realizar esta operación?

Cuando se usa un valor HRESULT en un [si](../../cpp/if-else-statement-cpp.md) instrucción, el valor HRESULT se convertirá en un [bool](../../cpp/bool-cpp.md) a menos que se pruebe explícitamente la variable como un valor HRESULT. De forma predeterminada, esta advertencia está desactivada.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4165

```cpp
// C4165.cpp
// compile with: /W1
#include <windows.h>
#pragma warning(1:4165)

extern HRESULT hr;
int main() {
   if (hr) {
   // try either of the following ...
   // if (FAILED(hr)) { // C4165 expected
   // if (hr != S_OK) {
   }
}
```