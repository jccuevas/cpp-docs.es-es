---
title: Error del compilador C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: 81f508c47c678d86f8f95303861b42f8a70daa57
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750057"
---
# <a name="compiler-error-c3099"></a>Error del compilador C3099

'keyword': use [System::AttributeUsageAttribute] para atributos administrados; use [Windows::Foundation::Metadata::AttributeUsageAttribute] para atributos WinRT

Use <xref:System.AttributeUsageAttribute> para declarar atributos **/CLR** . Use `Windows::Foundation::Metadata::AttributeUsageAttribute` para declarar atributos de Windows Runtime.

Para obtener más información sobre los atributos/CLR, vea [atributos definidos por el usuario](../../extensions/user-defined-attributes-cpp-component-extensions.md). Para los atributos admitidos en Windows Runtime, consulte [espacio de nombres Windows. Foundation. Metadata.](/uwp/api/windows.foundation.metadata)

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3099 y muestra cómo corregirlo:

```cpp
// C3099.cpp
// compile with: /clr /c
using namespace System;
[usage(10)]   // C3099
// try the following line instead
// [AttributeUsageAttribute(AttributeTargets::All)]
ref class A : Attribute {};
```
