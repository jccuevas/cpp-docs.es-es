---
title: Error del compilador C2951
ms.date: 11/04/2016
f1_keywords:
- C2951
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
ms.openlocfilehash: dbc7186edfce6cc12a38fb2fc1dda08ac4a181c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300731"
---
# <a name="compiler-error-c2951"></a>Error del compilador C2951

solo se permiten en el espacio de nombres global, las declaraciones de tipo o ámbito de clase

No se puede declarar una clase genérica o clase de plantilla fuera global o ámbito de espacio de nombres. Si hace que las declaraciones de plantilla o genérico en un archivo de inclusión, asegúrese de que el archivo de inclusión está en el ámbito global.

El ejemplo siguiente genera C2951:

```
// C2951.cpp
template <class T>
class A {};

int main() {
   template <class T>   // C2951
   class B {};
}
```

C2951 también puede producirse al usar genéricos:

```
// C2951b.cpp
// compile with: /clr /c

// OK
generic <class T>
ref class GC { };

int main() {
   generic <class T> ref class GC2 {};   // C2951
}
```