---
title: Error del compilador C3099 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3099
dev_langs:
- C++
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5f11e049965fb7374a2294e813502d1279f9f26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067420"
---
# <a name="compiler-error-c3099"></a>Error del compilador C3099

'keyword': use [System::AttributeUsageAttribute] para atributos administrados; use [Windows::Foundation::Metadata::AttributeUsageAttribute] para atributos WinRT

Use <xref:System.AttributeUsageAttribute> para declarar **/CLR** atributos. Use `Windows::Foundation::Metadata::AttributeUsageAttribute` para declarar atributos de Windows Runtime.

Para obtener más información sobre atributos/CLR, vea [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md). Para atributos admitidos en tiempo de ejecución de Windows, consulte [espacio de nombres Windows.Foundation.Metadata](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.aspx)

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