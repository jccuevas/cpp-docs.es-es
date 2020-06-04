---
title: Error del compilador C3320
ms.date: 11/04/2016
f1_keywords:
- C3320
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
ms.openlocfilehash: 0289d49ebbb0e30153beb6b0b2bc758bff5ef118
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201310"
---
# <a name="compiler-error-c3320"></a>Error del compilador C3320

'tipo': el tipo no puede tener el mismo nombre que la propiedad de módulo 'nombre'

Un tipo definido por el usuario (UDT) exportado, que podría ser una estructura, una clase, una enumeración o una Unión, no puede tener el mismo nombre que el parámetro pasado a la propiedad Name del atributo [Module](../../windows/module-cpp.md) .

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3320:

```cpp
// C3320.cpp
#include "unknwn.h"
[module(name="xx")];

[export] struct xx {   // C3320
// Try the following line instead
// [export] struct yy {
   int i;
};
```
