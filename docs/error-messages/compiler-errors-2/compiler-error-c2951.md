---
title: Error del compilador C2951
ms.date: 11/04/2016
f1_keywords:
- C2951
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
ms.openlocfilehash: fdb837f8e9a9b769d470b70b962ce63d144161e1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755985"
---
# <a name="compiler-error-c2951"></a>Error del compilador C2951

las declaraciones de tipos solo se permiten en el ámbito global, de espacio de nombres o de clase

No se puede declarar una clase genérica o de plantilla fuera del ámbito global o de espacio de nombres. Si realiza las declaraciones genéricas o de plantilla en un archivo de inclusión, asegúrese de que el archivo de inclusión está en el ámbito global.

En el ejemplo siguiente se genera C2951:

```cpp
// C2951.cpp
template <class T>
class A {};

int main() {
   template <class T>   // C2951
   class B {};
}
```

C2951 también puede producirse cuando se usan genéricos:

```cpp
// C2951b.cpp
// compile with: /clr /c

// OK
generic <class T>
ref class GC { };

int main() {
   generic <class T> ref class GC2 {};   // C2951
}
```
