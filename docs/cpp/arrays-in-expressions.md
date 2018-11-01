---
title: Matrices en expresiones
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
ms.openlocfilehash: 0f2ef43c2a5bc4f8a44378c21d6d53b14f07ea07
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478174"
---
# <a name="arrays-in-expressions"></a>Matrices en expresiones

Cuando un identificador de un tipo de matriz aparece en una expresión distinta `sizeof`, dirección de (**&**), o la inicialización de una referencia, se convierte a un puntero al primer elemento de matriz. Por ejemplo:

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

El puntero `psz` apunta al primer elemento de la matriz `szError1`. Tenga en cuenta que las matrices, a diferencia de los punteros, no son valores l modificables. Por consiguiente, la siguiente asignación no es válida:

```cpp
szError1 = psz;
```

## <a name="see-also"></a>Vea también

[Matrices](../cpp/arrays-cpp.md)