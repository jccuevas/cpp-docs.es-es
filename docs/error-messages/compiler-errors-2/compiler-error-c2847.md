---
title: Error del compilador C2847 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2847
dev_langs:
- C++
helpviewer_keywords:
- C2847
ms.assetid: 9ad9a0e0-8b16-49d9-a5be-f8eda2372aa9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41e3b49c509240fd0d782aacaa9fae836b62702a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054446"
---
# <a name="compiler-error-c2847"></a>Error del compilador C2847

no se puede aplicar sizeof al tipo administrado o WinRT 'class'

El [sizeof](../../cpp/sizeof-operator.md) operador obtiene el valor de un objeto en tiempo de compilación. El tamaño de un tipo de valor, una interfaz o una clase administrada o WinRT es dinámico y no puede conocerse en tiempo de compilación.

El ejemplo siguiente genera el error C2847:

```
// C2847.cpp
// compile with: /clr
ref class A {};

int main() {
   A ^ xA = gcnew A;
   sizeof(*xA);   // C2847 cannot use sizeof on managed object
}
```
