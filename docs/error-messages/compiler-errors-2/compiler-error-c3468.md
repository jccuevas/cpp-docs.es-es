---
title: Error del compilador C3468
ms.date: 11/04/2016
f1_keywords:
- C3468
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
ms.openlocfilehash: 185bd35bb732f592c75912fe69d4491252fe9d0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476120"
---
# <a name="compiler-error-c3468"></a>Error del compilador C3468

'type': solamente puede reenviar un tipo a un ensamblado:

'`file`' no es un ensamblado

Solo se pueden reenviar tipos de un ensamblado.

Para obtener más información, consulte [reenvío de tipos (C++ / c++ / CLI)](../../windows/type-forwarding-cpp-cli.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un módulo.

```
// C3468.cpp
// compile with: /LN /clr
public ref class R {};
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3468.

```
// C3468_b.cpp
// compile with: /clr /c
#using "C3468.netmodule"
[ assembly:TypeForwardedTo(R::typeid) ];   // C3468
```