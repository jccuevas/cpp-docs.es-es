---
title: Error del compilador C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 5f39510ee9ec0e717d675aa8b396405bc33b4ea1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445011"
---
# <a name="compiler-error-c3279"></a>Error del compilador C3279

no se permiten especializaciones parciales o explícitas ni creaciones de instancias explícitas de plantillas de clase declaradas en el espacio de nombres cli

El espacio de nombres `cli` está definido por Microsoft y contiene pseudoplantillas. El compilador de Visual C++ no permite las especializaciones definidas por el usuario, parciales, explícitas ni creaciones de instancias explícitas de plantillas de clase en este espacio de nombres.

El ejemplo siguiente genera la advertencia C3279:

```
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```