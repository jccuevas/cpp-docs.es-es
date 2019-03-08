---
title: Error del compilador C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: beaa34bb9bed4824383cdad32c6bfd0aea19f6b7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418586"
---
# <a name="compiler-error-c3099"></a>Error del compilador C3099

'keyword': use [System::AttributeUsageAttribute] para atributos administrados; use [Windows::Foundation::Metadata::AttributeUsageAttribute] para atributos WinRT

Use <xref:System.AttributeUsageAttribute> para declarar **/CLR** atributos. Use `Windows::Foundation::Metadata::AttributeUsageAttribute` para declarar atributos de Windows Runtime.

Para obtener más información sobre atributos/CLR, vea [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md). Para atributos admitidos en tiempo de ejecución de Windows, consulte [espacio de nombres Windows.Foundation.Metadata](/uwp/api/windows.foundation.metadata)

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3099 y muestra cómo corregirlo:

```
// C3099.cpp
// compile with: /clr /c
using namespace System;
[usage(10)]   // C3099
// try the following line instead
// [AttributeUsageAttribute(AttributeTargets::All)]
ref class A : Attribute {};
```