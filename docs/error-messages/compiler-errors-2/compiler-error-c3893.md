---
title: Error del compilador C3893 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3893
dev_langs:
- C++
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 857d13de61f03bf0784d8cd10ad092d16f7acdaa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087052"
---
# <a name="compiler-error-c3893"></a>Error del compilador C3893

'var': uso del valor l del miembro de datos initonly solamente se permite en un constructor de instancia de clase 'type_name'

Estática [initonly](../../dotnet/initonly-cpp-cli.md) los miembros de datos solo pueden obtener la dirección en un constructor estático.

Los miembros de datos de instancia (no estáticos) initonly solo pueden obtener la dirección en constructores de instancia (no estáticos).

El ejemplo siguiente genera C3893:

```
// C3893.cpp
// compile with: /clr
ref struct Y1 {
   Y1() : data_var(0) {
      int% i = data_var;   // OK
   }
   initonly int data_var;
};

int main(){
   Y1^ y= gcnew Y1;
   int% i = y->data_var;   // C3893
}
```