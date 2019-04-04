---
title: Error del compilador C3465
ms.date: 11/04/2016
f1_keywords:
- C3465
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
ms.openlocfilehash: 117c9b9918950fd2e95e206c5aea457dee183b0a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781580"
---
# <a name="compiler-error-c3465"></a>Error del compilador C3465

para usar el tipo 'type' debe hacer referencia al ensamblado 'assembly'

El reenvío de tipos funcionará para una aplicación cliente hasta que recompile el cliente. Cuando recompile, necesitará una referencia para cada ensamblado que contenga la definición de un tipo utilizado en la aplicación cliente.

Para obtener más información, consulte [reenvío de tipos (C++ / c++ / CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera un ensamblado que contiene la nueva ubicación de un tipo.

```
// C3465.cpp
// compile with: /clr /LD
public ref class R {
public:
   ref class N {};
};
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera un ensamblado que se usa para contener la definición del tipo, pero ahora contiene sintaxis de reenvío para el tipo.

```
// C3465_b.cpp
// compile with: /clr /LD
#using "C3465.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3465.

```
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