---
title: Error del compilador C2739 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2739
dev_langs:
- C++
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4e6c757823caa25bd9df890dce35035642e5212
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046672"
---
# <a name="compiler-error-c2739"></a>Error del compilador C2739

’number': las dimensiones de la matriz administrada o de WinRT explícita deben estar comprendidas entre 1 y 32

Una dimensión de matriz no estaba comprendida entre 1 y 32.

El ejemplo siguiente genera el error C2739 y muestra cómo corregirlo:

```
// C2739.cpp
// compile with: /clr
int main() {
   array<int, -1>^a;   // C2739
   // try the following line instead
   // array<int, 2>^a;
}
```