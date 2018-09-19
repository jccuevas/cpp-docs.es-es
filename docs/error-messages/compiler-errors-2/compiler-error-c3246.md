---
title: Error del compilador C3246 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3246
dev_langs:
- C++
helpviewer_keywords:
- C3246
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a588067fa21e0aeee54516bcec28cdf3648ac9f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047816"
---
# <a name="compiler-error-c3246"></a>Error del compilador C3246

'class': no se puede heredar de 'type', ya que se ha declarado como 'sealed'

Una clase marcada como [sealed](../../windows/sealed-cpp-component-extensions.md) no puede ser la clase base de otras clases.

El ejemplo siguiente genera la advertencia C3246:

```
// C3246_2.cpp
// compile with: /clr /LD
ref class X sealed {};

ref class Y : public X {}; // C3246
```
