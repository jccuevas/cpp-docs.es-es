---
title: Error del compilador C3450
ms.date: 11/04/2016
f1_keywords:
- C3450
helpviewer_keywords:
- C3450
ms.assetid: 78892cf7-0b82-4589-90d0-e06666247003
ms.openlocfilehash: 7b57b67e8f4542266818ad5b3d90d78a1a943d55
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756232"
---
# <a name="compiler-error-c3450"></a>Error del compilador C3450

'type': no es un atributo; no puede especificar [System::AttributeUsageAttribute] ni [Windows::Foundation::Metadata::AttributeUsageAttribute]

Un atributo administrado definido por el usuario debe heredar de <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>. Se debe definir un atributo de tiempo de ejecución de Windows en el espacio de nombres `Windows::Foundation::Metadata`.

Para obtener más información, consulta [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3450 y muestra cómo corregirlo.

```cpp
// C3450.cpp
// compile with: /clr
// C3450 expected
using namespace System;
using namespace System::Security;
using namespace System::Security::Permissions;

public ref class MyClass {};

class MyClass2 {};

[attribute(AttributeTargets::All)]
ref struct AtClass {
   AtClass(Type ^) {}
};

[attribute(AttributeTargets::All)]
ref struct AtClass2 {
   AtClass2() {}
};

// Apply the AtClass and AtClass2 attributes to class B
[AtClass(MyClass::typeid), AtClass2]
[AttributeUsage(AttributeTargets::All)]
// Delete the following line to resolve.
ref class B {};
// Uncomment the following line to resolve.
// ref class B : Attribute {};
```
