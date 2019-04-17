---
title: Error del compilador C2979
ms.date: 11/04/2016
f1_keywords:
- C2979
helpviewer_keywords:
- C2979
ms.assetid: 98bd9043-ec44-451e-a482-3a8e35fc7464
ms.openlocfilehash: e9b0af0d17ef57f19e051165b16632e3180159cd
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767065"
---
# <a name="compiler-error-c2979"></a>Error del compilador C2979

no se admite especializaciones explícitas en genéricos

Se declaró una clase genérica incorrectamente.  Consulte [genéricos](../../extensions/generics-cpp-component-extensions.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C2979.

```
// C2979.cpp
// compile with: /clr /c
generic <>
ref class Utils {};   // C2979 error

generic <class T>
ref class Utils2 {};   // OK
```