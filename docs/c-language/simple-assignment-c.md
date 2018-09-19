---
title: Asignación simple (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff4e032e205680da84369075514e3177fa5fb33e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051027"
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