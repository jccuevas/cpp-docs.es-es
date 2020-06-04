---
title: Error del compilador C3836
ms.date: 11/04/2016
f1_keywords:
- C3836
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
ms.openlocfilehash: 9c8a7e761f2ece046d5de5c0e74ee911e5ee550d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741409"
---
# <a name="compiler-error-c3836"></a>Error del compilador C3836

no se permite que el constructor estático tenga una lista de inicializadores de miembro

Una clase administrada no puede tener un constructor estático que también tenga una lista de inicialización de miembros. El Common Language Runtime llama a los constructores de clase estáticos para realizar la inicialización de la clase, inicializando los miembros de datos estáticos.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3836:

```cpp
// C3836a.cpp
// compile with: /clr
ref class M
{
   static int s_i;

public:
   static M() :  s_i(1234)   // C3836, delete initializer to resolve
   {
   }
};

int main()
{
}
```
