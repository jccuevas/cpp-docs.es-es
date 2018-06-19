---
title: Relleno y alineación de miembros de estructura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb090fc283da0a8aa86dac524272d308127059ba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385382"
---
# <a name="padding-and-alignment-of-structure-members"></a>Relleno y alineación de miembros de estructura
**ANSI 3.5.2.1** El relleno y la alineación de miembros de estructuras y si un campo de bits puede superponerse a un límite de unidad de almacenamiento  
  
 Los miembros de estructura se almacenan secuencialmente en el orden en que se declaran: el primer miembro tiene la dirección de memoria menor y el último miembro, la dirección de memoria mayor.  
  
 Cada objeto de datos tiene un elemento alignment-requirement. El requisito de alineación para todos los datos excepto las estructuras, uniones y matrices es el tamaño del objeto o el tamaño actual de empaquetado (especificado con /Zp o la directiva pragma `pack`, lo que sea menor). Para estructuras, uniones y matrices, el requisito de alineación es el mayor requisito de alineación de sus miembros. A cada objeto se le asigna un offset de forma que  
  
 *offset*  `%` *alignment-requirement* `==` 0  
  
 Los campos de bits adyacentes se empaquetan en la misma unidad de asignación de 1, 2 o 4 bytes si los tipos enteros tienen el mismo tamaño y si el siguiente campo de bits cabe en la unidad de asignación actual sin traspasar el límite impuesto por los requisitos comunes de alineación de los campos de bits.  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, uniones, enumeraciones y campos de bits](../c-language/structures-unions-enumerations-and-bit-fields.md)