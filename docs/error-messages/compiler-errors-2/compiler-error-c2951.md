---
title: Error del compilador C2951 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2951
dev_langs:
- C++
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6757256f08c5c1ed0a35fbf1c2a70776a4f2936
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074674"
---
# <a name="compiler-error-c2951"></a>Error del compilador C2951

solo se permiten en el espacio de nombres global, las declaraciones de tipo o ámbito de clase

No se puede declarar una clase genérica o clase de plantilla fuera global o ámbito de espacio de nombres. Si hace que las declaraciones de plantilla o genérico en un archivo de inclusión, asegúrese de que el archivo de inclusión está en el ámbito global.

El ejemplo siguiente genera C2951:

```
// C2951.cpp
template <class T>
class A {};

int main() {
   template <class T>   // C2951
   class B {};
}
```

C2951 también puede producirse al usar genéricos:

```
// C2951b.cpp
// compile with: /clr /c

// OK
generic <class T>
ref class GC { };

int main() {
   generic <class T> ref class GC2 {};   // C2951
}
```