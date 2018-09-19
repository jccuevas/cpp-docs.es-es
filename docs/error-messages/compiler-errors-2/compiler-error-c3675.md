---
title: Error del compilador C3675 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3675
dev_langs:
- C++
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4b6656753ab4a611dcb80d1473e0b44bf47a270
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094785"
---
# <a name="compiler-error-c3675"></a>Error del compilador C3675

'function': se ha reservado porque 'property' está definido

Cuando se declara una propiedad simple, el compilador genera get y métodos de descriptor de acceso set y los nombres están presentes en el ámbito del programa.  Los nombres generados por el compilador se forman anteponiendo get_ y set_ al nombre de propiedad.  Por lo tanto, no puede declarar funciones con el mismo nombre que los descriptores de acceso generados por el compilador.

Vea [property](../../windows/property-cpp-component-extensions.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3675.

```
// C3675.cpp
// compile with: /clr /c
ref struct C {
public:
   property int Size;
   int get_Size() { return 0; }   // C3675
};
```