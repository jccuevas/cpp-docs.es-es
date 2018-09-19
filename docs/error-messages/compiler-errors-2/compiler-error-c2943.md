---
title: Error del compilador C2943 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2943
dev_langs:
- C++
helpviewer_keywords:
- C2943
ms.assetid: ede6565e-d892-44c0-8eee-c69545f3be2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4849e138cdbef97595d4aa1bbb45c277e7feb96a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047335"
---
# <a name="compiler-error-c2943"></a>Error del compilador C2943

'class': el identificador de clase de tipo se volvió a definir como argumento de tipo de una plantilla

No puede usar una clase genérica o de plantilla, en lugar de un símbolo, como argumento de tipo genérico o de plantilla.

El ejemplo siguiente genera la advertencia C2943:

```
// C2943.cpp
// compile with: /c
template<class T>
class List {};

template<class List<int> > class MyList;   // C2943
template<class T >  class MyList;
```