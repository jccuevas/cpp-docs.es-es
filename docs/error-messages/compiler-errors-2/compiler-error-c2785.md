---
title: Error del compilador C2785
ms.date: 11/04/2016
f1_keywords:
- C2785
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
ms.openlocfilehash: 6aff2e5c96e3c79fc748d8a95779d6a08647ab03
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739628"
---
# <a name="compiler-error-c2785"></a>Error del compilador C2785

' declaration1 ' y ' declaration2 ' tienen distintos tipos de valor devueltos

El tipo de valor devuelto de la especialización de la plantilla de función difiere del tipo de valor devuelto de la plantilla de función principal.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Compruebe si todas las especializaciones de la plantilla de función son coherentes.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2785:

```cpp
// C2785.cpp
// compile with: /c
template<class T> void f(T);

template<> int f(int); // C2785
template<> void f(int); // OK
```
