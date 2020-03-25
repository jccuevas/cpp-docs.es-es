---
title: Error del compilador C2753
ms.date: 11/04/2016
f1_keywords:
- C2753
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
ms.openlocfilehash: ea2901c998ac1a44ad142779e7ce48bfffff66c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202165"
---
# <a name="compiler-error-c2753"></a>Error del compilador C2753

'*plantilla*': la especialización parcial no puede coincidir con la lista de argumentos de la plantilla principal

Si la lista de argumentos de plantilla coincide con la lista de parámetros, el compilador la trata como la misma plantilla. No se permite definir la misma plantilla dos veces.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se genera C2753 y se muestra una manera de corregirlo:

```cpp
// C2753.cpp
// compile with: cl /c C2753.cpp
template<class T>
struct A {};

template<class T>
struct A<T> {};   // C2753
// try the following line instead
// struct A<int> {};

template<class T, class U, class V, class W, class X>
struct B {};
```
