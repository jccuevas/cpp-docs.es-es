---
title: Error del compilador C3418
ms.date: 11/04/2016
f1_keywords:
- C3418
helpviewer_keywords:
- C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
ms.openlocfilehash: 8456e9b17b72cd4ac98349d2f2871a1c59f56911
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482777"
---
# <a name="compiler-error-c3418"></a>Error del compilador C3418

el especificador de acceso 'especificador' no se admite

Un especificador de acceso CLR se especificó incorrectamente.  Para obtener más información, vea la visibilidad de tipos y la visibilidad de miembros en [Cómo: definir y utilizar clases y Structs (C++ / c++ / CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3418.

```cpp
// C3418.cpp
// compile with: /clr /c
ref struct m {
internal public:   // C3418
   void test(){}
};

ref struct n {
internal:   // OK
   void test(){}
};
```