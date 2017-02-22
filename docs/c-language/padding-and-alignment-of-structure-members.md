---
title: "Rellenar y alinear miembros de estructura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "miembros de estructura, relleno y alineación"
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Rellenar y alinear miembros de estructura
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.5.2.1** El relleno y la alineación de miembros de estructuras y si un campo de bits puede superponerse a un límite de unidad de almacenamiento  
  
 Los miembros de estructura se almacenan secuencialmente en el orden en que se declaran: el primer miembro tiene la dirección de memoria menor y el último miembro, la dirección de memoria mayor.  
  
 Cada objeto de datos tiene un elemento alignment\-requirement.  El requisito de alineación para todos los datos excepto las estructuras, uniones y matrices es el tamaño del objeto o el tamaño actual de empaquetado \(especificado con \/Zp o la directiva pragma `pack`, lo que sea menor\).  Para estructuras, uniones y matrices, el requisito de alineación es el mayor requisito de alineación de sus miembros.  A cada objeto se le asigna un offset de forma que  
  
 *offset*  `%` *alignment\-requirement* `==` 0  
  
 Los campos de bits adyacentes se empaquetan en la misma unidad de asignación de 1, 2 o 4 bytes si los tipos enteros tienen el mismo tamaño y si el siguiente campo de bits cabe en la unidad de asignación actual sin traspasar el límite impuesto por los requisitos comunes de alineación de los campos de bits.  
  
## Vea también  
 [Estructuras, uniones, enumeraciones y campos de bits](../c-language/structures-unions-enumerations-and-bit-fields.md)