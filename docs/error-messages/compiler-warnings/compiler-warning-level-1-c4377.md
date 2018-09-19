---
title: Compilador advertencia (nivel 1) C4377 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4377
dev_langs:
- C++
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 613ebe183b61c6b9894ed3b726f90061e2b24ef6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047179"
---
# <a name="compiler-warning-level-1-c4377"></a>Advertencia del compilador (nivel 1) C4377

tipos nativos son privados de forma predeterminada; -d1PrivateNativeTypes está en desuso

En versiones anteriores, los tipos nativos en ensamblados eran públicos de forma predeterminada y una opción de compilador interno y no documentada (**/d1PrivateNativeTypes**) se usó para que sean privados.

Todos los tipos, nativos y CLR, ahora son privados de forma predeterminada en un ensamblado, por lo que **/d1PrivateNativeTypes** ya no es necesario.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4377.

```
// C4377.cpp
// compile with: /clr /d1PrivateNativeTypes /W1
// C4377 warning expected
int main() {}
```