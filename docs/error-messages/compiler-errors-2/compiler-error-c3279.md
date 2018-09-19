---
title: Error del compilador C3279 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3279
dev_langs:
- C++
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89c537da9bcf91e7774353cc1516a4c44e28649c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056773"
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