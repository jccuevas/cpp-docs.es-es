---
title: Error del compilador C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: 0f3eac1c232ef159d220a347d6b6dc3aed2fdd9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324784"
---
# <a name="compiler-error-c3099"></a>Error del compilador C3099

'keyword': use [System::AttributeUsageAttribute] para atributos administrados; use [Windows::Foundation::Metadata::AttributeUsageAttribute] para atributos WinRT

Use <xref:System.AttributeUsageAttribute> para declarar **/CLR** atributos. Use `Windows::Foundation::Metadata::AttributeUsageAttribute` para declarar atributos de Windows Runtime.

Para obtener más información sobre atributos/CLR, vea [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md). Para atributos admitidos en tiempo de ejecución de Windows, consulte [espacio de nombres Windows.Foundation.Metadata](/uwp/api/windows.foundation.metadata)

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