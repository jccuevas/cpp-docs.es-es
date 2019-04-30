---
title: Error del compilador C3104
ms.date: 11/04/2016
f1_keywords:
- C3104
helpviewer_keywords:
- C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
ms.openlocfilehash: 3b2737bd67798fd467649be175d581ca551e1331
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404174"
---
# <a name="compiler-error-c3104"></a>Error del compilador C3104

argumento de atributo no válido

Ha especificado un argumento no válido a un atributo.

Consulte [tipos de parámetro de atributo](../../extensions/attribute-parameter-types-cpp-component-extensions.md) para obtener más información.

Este error puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: cuando se pasan las matrices administradas a los atributos personalizados, el tipo de la matriz ya no se deduce de la lista de inicialización de agregado. Ahora, el compilador requiere que especifique el tipo de la matriz, así como la lista de inicializadores.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3104.

```
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

El ejemplo siguiente genera C3104.

```
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
