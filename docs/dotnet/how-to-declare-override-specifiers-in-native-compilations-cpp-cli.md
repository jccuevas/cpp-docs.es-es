---
title: 'Cómo: Declarar especificadores de invalidación (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
ms.openlocfilehash: 9f3f6855f257d0af250b9bbdd2c0360b308ce775
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374452"
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Cómo: Declarar especificadores de invalidación en las compilaciones nativas (C++/CLI)

[sealed](../extensions/sealed-cpp-component-extensions.md), [abstract](../extensions/abstract-cpp-component-extensions.md)e [override](../extensions/override-cpp-component-extensions.md) están disponibles en compilaciones que no utilizan **/ZW** o [/clr](../build/reference/clr-common-language-runtime-compilation.md).

> [!NOTE]
> El lenguaje ISO C++11 Standard tiene el identificador de [invalidación](../cpp/override-specifier.md) `final` y `sealed` el identificador [final,](../cpp/final-specifier.md) y ambos se admiten en Visual Studio Use en lugar de en el código que está destinado a compilarse como solo nativo.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el ejemplo `sealed` siguiente se muestra que es válido en compilaciones nativas.

### <a name="code"></a>Código

```cpp
// sealed_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
   virtual void g();
};

class X : public I1 {
public:
   virtual void g() sealed {}
};

class Y : public X {
public:

   // the following override generates a compiler error
   virtual void g() {}   // C3248 X::g is sealed!
};
```

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el ejemplo `override` siguiente se muestra que es válido en compilaciones nativas.

### <a name="code"></a>Código

```cpp
// override_native_keyword.cpp
#include <stdio.h>
__interface I1 {
   virtual void f();
};

class X : public I1 {
public:
   virtual void f() override {}   // OK
   virtual void g() override {}   // C3668 I1::g does not exist
};
```

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

Este ejemplo `abstract` muestra que es válido en compilaciones nativas.

### <a name="code"></a>Código

```cpp
// abstract_native_keyword.cpp
class X abstract {};

int main() {
   X * MyX = new X;   // C3622 cannot instantiate abstract class
}
```

## <a name="see-also"></a>Consulte también

[Especificadores de invalidación](../extensions/override-specifiers-cpp-component-extensions.md)
