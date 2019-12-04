---
title: Error del compilador C3707
ms.date: 11/04/2016
f1_keywords:
- C3707
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
ms.openlocfilehash: 6faf035c0f4f68b10b187c56bea4cafc776998cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757961"
---
# <a name="compiler-error-c3707"></a>Error del compilador C3707

' función ': el método dispinterface debe tener un DISPID

Si utiliza un método `dispinterface`, debe asignarle un `dispid`. Para corregir este error, asigne un `dispid` al método `dispinterface`, por ejemplo, quitando los comentarios del atributo `id` en el método en el ejemplo siguiente. Para obtener más información, vea los atributos [dispinterface](../../windows/dispinterface.md) e [ID](../../windows/id.md).

En el ejemplo siguiente se genera C3707:

```cpp
// C3707.cpp
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(name="xx")];
[dispinterface]
__interface IEvents : IDispatch
{
   HRESULT event1([in] int i);   // C3707
   // try the following line instead
   // [id(1)] HRESULT event1([in] int i);
};

int main() {
}
```
