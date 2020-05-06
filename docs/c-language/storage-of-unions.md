---
title: Almacenamiento de uniones
ms.date: 11/04/2016
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
ms.openlocfilehash: 49b99dc17fd7bdddd8a47e3bfd5913a70a7631a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157934"
---
# <a name="storage-of-unions"></a>Almacenamiento de uniones

El almacenamiento asociado a una variable de unión es el almacenamiento necesario para el miembro mayor de la unión. Cuando se almacena un miembro menor, la variable de unión puede contener espacio de memoria sin usar. Todos los miembros se almacenan en el mismo espacio de memoria y comienzan en la misma dirección. El valor almacenado se sobrescribe cada vez que se asigna un valor a un miembro diferente. Por ejemplo:

```
union         /* Defines a union named x */
{
    char *a, b;
    float f[20];
} x;
```

Los miembros de la unión `x` son, en orden de declaración, un puntero a un valor `char`, un valor `char` y una matriz de valores **float**. El almacenamiento asignado para `x` es el almacenamiento necesario para la matriz `f` de 20 elementos, ya que `f` es el miembro más largo de la unión. Dado que no hay ninguna etiqueta asociada con la unión, su tipo es sin nombre o “anónimo”.

## <a name="see-also"></a>Vea también

[Declaraciones de unión](../c-language/union-declarations.md)
