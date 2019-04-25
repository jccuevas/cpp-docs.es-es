---
title: Error del compilador C3100
ms.date: 11/04/2016
f1_keywords:
- C3100
helpviewer_keywords:
- C3100
ms.assetid: 7a9c9eaf-08ef-442d-94a0-e457beee8549
ms.openlocfilehash: 98fa90d184db596458ec7b943e3c35ddc5b7bce9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324810"
---
# <a name="compiler-error-c3100"></a>Error del compilador C3100

'target': calificador de atributo desconocido

Se especificó un destino de atributo no válido.

Para obtener más información, consulte [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3100.

```
// C3100.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::All)]
public ref class Attr : public Attribute {
public:
   Attr(int t) : m_t(t) {}
   int m_t;
};

[invalid_target:Attr(10)];   // C3100
[assembly:Attr(10)];   // OK
```