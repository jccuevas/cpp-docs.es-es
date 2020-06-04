---
title: Error del compilador C3104
ms.date: 11/04/2016
f1_keywords:
- C3104
helpviewer_keywords:
- C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
ms.openlocfilehash: b92a6eade137a1d319ec286afa08f8477ff029d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755879"
---
# <a name="compiler-error-c3104"></a>Error del compilador C3104

argumento de atributo no válido

Especificó un argumento no válido para un atributo.

Para obtener más información, vea [tipos de parámetro de atributo](../../extensions/attribute-parameter-types-cpp-component-extensions.md) .

Este error se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio 2005: al pasar matrices administradas a atributos personalizados, el tipo de la matriz ya no se deduce de la lista de inicialización agregada. Ahora, el compilador requiere que se especifique el tipo de la matriz, así como la lista de inicializadores.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3104.

```cpp
// C3104a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104
// try the following line instead
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3104.

```cpp
// C3104b.cpp
// compile with: /clr /c
// C3104 expected
using namespace System;

int func() {
   return 0;
}

[attribute(All)]
ref class A {
public:
   A(int) {}
};

// Delete the following 2 lines to resolve.
[A(func())]
ref class B {};

// OK
[A(0)]
ref class B {};
```
