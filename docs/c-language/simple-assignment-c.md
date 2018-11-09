---
title: Asignación simple (C)
ms.date: 11/04/2016
helpviewer_keywords:
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
ms.openlocfilehash: 76c48fc6774f97bab69f916ad7e5176e91d004ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574920"
---
# <a name="simple-assignment-c"></a>Asignación simple (C)

El operador de asignación simple asigna el operando derecho al operando izquierdo. El valor del operando derecho se convierte al tipo de la expresión de asignación y reemplaza el valor almacenado en el objeto designado por el operando izquierdo. Se aplican las reglas de conversión para asignación (vea [Conversiones de asignación](../c-language/assignment-conversions.md)).

```
double x;
int y;

x = y;
```

En este ejemplo, el valor de `y` se convierte al tipo **double** y se asigna a `x`.

## <a name="see-also"></a>Vea también

[Operadores de asignación de C](../c-language/c-assignment-operators.md)