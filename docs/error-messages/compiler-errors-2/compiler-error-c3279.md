---
title: Error del compilador C3279
ms.date: 11/04/2016
f1_keywords:
- C3279
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
ms.openlocfilehash: 72646d7611163748fe7e27ea6c78cd38426eb6ad
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447816"
---
# <a name="compiler-error-c3279"></a>Error del compilador C3279

no se permiten especializaciones parciales o explícitas ni creaciones de instancias explícitas de plantillas de clase declaradas en el espacio de nombres cli

El espacio de nombres `cli` está definido por Microsoft y contiene pseudoplantillas. Microsoft C++ compilador no permite definido por el usuario, especializaciones parciales o explícitas ni creaciones de instancias explícitas de plantillas de clase en este espacio de nombres.

El ejemplo siguiente genera la advertencia C3279:

```
// C3279.cpp
// compile with: /clr
namespace cli {
   template <> ref class array<int> {};   // C3279
   template <typename T> ref class array<T, 2> {};   // C3279
}
```