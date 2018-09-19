---
title: Error del compilador C2833 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2833
dev_langs:
- C++
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53360c1eaf81ad407589fbdb125d9e6fe017708e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070176"
---
# <a name="compiler-error-c2833"></a>Error del compilador C2833

'operator operator' no es un operador o tipo reconocido

La palabra `operator` debe ir seguido por un operador que desea invalidar o un tipo que va a convertir.

Para obtener una lista de los operadores que se pueden definir en un tipo administrado, consulte [operadores definidos por el usuario](../../dotnet/user-defined-operators-cpp-cli.md).

El ejemplo siguiente genera C2833:

```
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```