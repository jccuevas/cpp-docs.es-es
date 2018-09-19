---
title: Error del compilador C2395 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2395
dev_langs:
- C++
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99d9a1be42a36baac2037e4289cb24db2f45b563
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050546"
---
# <a name="compiler-error-c2395"></a>Error del compilador C2395

'your_type::operator'op'': el operador CLR o WinRT no es válido. Al menos un parámetro debe ser de los tipos siguientes: 'T', 'T%', 'T&', 'T^', 'T^%', 'T^&', donde T = 'su_tipo'

Un operador en un tipo administrado o en Windows Runtime no tenía al menos un parámetro con un tipo igual al del valor devuelto del operador.

El ejemplo siguiente genera C2395 y muestra cómo corregirlo:

```
// C2395.cpp
// compile with: /clr /c
value struct V {
   static V operator *(int i, char c);   // C2395

   // OK
   static V operator *(V v, char c);
   // or
   static V operator *(int i, V& rv);
};
```