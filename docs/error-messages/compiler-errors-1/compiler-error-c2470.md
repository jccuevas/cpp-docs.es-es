---
title: Error del compilador C2470
ms.date: 11/04/2016
f1_keywords:
- C2470
helpviewer_keywords:
- C2470
ms.assetid: e17d2cb8-b84c-447c-976a-625f0c96f3fe
ms.openlocfilehash: 2a4f8c8052081fe90801dfeb30d942fbb9a91a01
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517161"
---
# <a name="compiler-error-c2470"></a>Error del compilador C2470

'function': parece una definición de función, pero no hay ninguna lista de parámetros; omitiendo el cuerpo aparente

Una definición de función falta su lista de argumentos.

El ejemplo siguiente genera C2470:

```
// C2470.cpp
int MyFunc {};  // C2470
void MyFunc2() {};  //OK

int main(){
   MyFunc();
   MyFunc2();
}
```