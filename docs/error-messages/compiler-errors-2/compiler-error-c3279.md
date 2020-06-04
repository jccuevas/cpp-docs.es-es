---
title: Error del compilador C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 3025dbf7c6bf4701218c2d9a956cae26d7180848
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757610"
---
# <a name="compiler-error-c3279"></a>Error del compilador C3279

no se permiten especializaciones parciales o explícitas ni creaciones de instancias explícitas de plantillas de clase declaradas en el espacio de nombres cli

El espacio de nombres `cli` está definido por Microsoft y contiene pseudoplantillas. El compilador de Microsoft C++ no permite especializaciones definidas por el usuario, parciales y explícitas ni creaciones de instancias explícitas de plantillas de clase en este espacio de nombres.

El ejemplo siguiente genera la advertencia C3279:

```cpp
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```
