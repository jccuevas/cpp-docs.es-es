---
title: Relleno y alineación de miembros de estructura
ms.date: 10/18/2018
helpviewer_keywords:
- structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
ms.openlocfilehash: 0f9c70ed074a11800b707aa48ec8e0e2f8b4f999
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148119"
---
# <a name="padding-and-alignment-of-structure-members"></a>Relleno y alineación de miembros de estructura

**ANSI 3.5.2.1** El relleno y la alineación de miembros de estructuras y si un campo de bits puede superponerse a un límite de unidad de almacenamiento

Los miembros de estructura se almacenan secuencialmente en el orden en que se declaran: el primer miembro tiene la dirección de memoria menor y el último miembro, la dirección de memoria mayor.

Cada objeto de datos tiene un elemento alignment-requirement. El requisito de alineación para todos los datos excepto las estructuras, uniones y matrices es el tamaño del objeto o el tamaño actual de empaquetado (especificado con /Zp o la directiva pragma `pack`, lo que sea menor). Para estructuras, uniones y matrices, el requisito de alineación es el mayor requisito de alineación de sus miembros. A cada objeto se le asigna un offset de forma que

*offset* **%** *alignment-requirement* **== 0**

Los campos de bits adyacentes se empaquetan en la misma unidad de asignación de 1, 2 o 4 bytes si los tipos enteros tienen el mismo tamaño y si el siguiente campo de bits cabe en la unidad de asignación actual sin traspasar el límite impuesto por los requisitos comunes de alineación de los campos de bits.

## <a name="see-also"></a>Vea también

[Estructuras, uniones, enumeraciones y campos de bits](../c-language/structures-unions-enumerations-and-bit-fields.md)
