---
title: Error del compilador C3465
ms.date: 11/04/2016
f1_keywords:
- C3465
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
ms.openlocfilehash: 1d82d367c5b77f54548403b7b142aa740919b6c2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756570"
---
# <a name="compiler-error-c3465"></a>Error del compilador C3465

para usar el tipo 'type' debe hacer referencia al ensamblado 'assembly'

El reenvío de tipos funcionará para una aplicación cliente hasta que recompile el cliente. Cuando recompile, necesitará una referencia para cada ensamblado que contenga la definición de un tipo utilizado en la aplicación cliente.

Para obtener más información, consulte [reenvío deC++tipos (/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera un ensamblado que contiene la nueva ubicación de un tipo.

```cpp
// C3465.cpp
// compile with: /clr /LD
public ref class R {
public:
   ref class N {};
};
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera un ensamblado que se usa para contener la definición del tipo, pero ahora contiene sintaxis de reenvío para el tipo.

```cpp
// C3465_b.cpp
// compile with: /clr /LD
#using "C3465.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3465.

```cpp
// C3465_c.cpp
// compile with: /clr
// C3465 expected
#using "C3465_b.dll"
// Uncomment the following line to resolve.
// #using "C3465.dll"

int main() {
   R^ r = gcnew R();
}
```
