---
title: Error del compilador C3675
ms.date: 11/04/2016
f1_keywords:
- C3675
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
ms.openlocfilehash: c154a0fe1989c92bb5e07c0710d3846883d1a113
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546332"
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