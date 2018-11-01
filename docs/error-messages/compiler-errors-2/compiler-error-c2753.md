---
title: Error del compilador C2753
ms.date: 11/04/2016
f1_keywords:
- C2753
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
ms.openlocfilehash: e13c45cec99e60d8aec7dcc3db8e5a4813ea7de9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509414"
---
# <a name="compiler-error-c2753"></a>Error del compilador C2753

'*plantilla*': la especialización parcial no puede coincidir con la lista de argumentos de plantilla principal

Si la lista de argumentos de plantilla coincide con la lista de parámetros, el compilador trata como la misma plantilla. No se permite definir dos veces la misma plantilla.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2753 y muestra cómo corregirlo:

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