---
title: Advertencia del compilador (nivel 1) C4674
ms.date: 11/04/2016
f1_keywords:
- C4674
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
ms.openlocfilehash: b9428a593ff59cbdfa6d8eb369413a560b4a5ad2
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052539"
---
# <a name="compiler-warning-level-1-c4674"></a>Advertencia del compilador (nivel 1) C4674

'method' se debe declarar como 'static' y tener exactamente un parámetro

La firma de un operador de conversión no es correcta. El método no se considera una conversión definida por el usuario. Para obtener más información sobre la definición de operadores, consulte [operadores definidosC++por el usuario (/CLI)](../../dotnet/user-defined-operators-cpp-cli.md) y [conversiones definidasC++por el usuario (/CLI)](../../dotnet/user-defined-conversions-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4674.

```cpp
// C4674.cpp
// compile with: /clr /WX /W1 /LD
ref class G {
   int op_Implicit(int i) {   // C4674
      return 0;
   }
};
```
