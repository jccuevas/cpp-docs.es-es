---
title: Error del compilador C2390 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2390
dev_langs:
- C++
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5de5a9af8f8aa04219f0a7d61162336745fd4bfa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098220"
---
# <a name="compiler-error-c2390"></a>Error del compilador C2390

'identifier': clase de almacenamiento incorrecta 'especificador'

La clase de almacenamiento no es válida para el identificador de ámbito global. La clase de almacenamiento predeterminada se utiliza en lugar de la clase no válida.

Soluciones posibles:

- Si el identificador es una función, declárelo con `extern` almacenamiento.

- Si el identificador es un parámetro formal o una variable local, declárelo con almacenamiento automático.

- Si el identificador es una variable global, declárelo con ninguna clase de almacenamiento (almacenamiento automático).

## <a name="example"></a>Ejemplo

- El ejemplo siguiente genera C2390:

```
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```