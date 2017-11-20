---
title: "Tipos enteros de C con tamaño | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 101c8facb8871d814d1a1ea05c2856d3105a8bfc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="c-sized-integer-types"></a>Tipos enteros de C con tamaño
**Específicos de Microsoft**  
  
 Microsoft C incluye compatibilidad para los tipos enteros con tamaño. Puede declarar variables de enteros de 8, 16, 32 o 64 bits mediante el especificador de tipo __int*n*, donde *n* es el tamaño, en bits, de la variable de entero. El valor de *n* puede ser 8, 16, 32 o 64. En el ejemplo siguiente se declara una variable de cada uno de los cuatro tipos de enteros con tamaño:  
  
```  
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 Los tres primeros tipos de enteros con tamaño son sinónimos de los tipos ANSI que tienen el mismo tamaño, y son útiles para escribir código portable que se comporta de forma idéntica en varias plataformas. Observe que el tipo de datos __int8 es sinónimo del tipo char, \__int16 es sinónimo del tipo short e \__int32 es sinónimo del tipo int. El tipo \__int64 no tiene ningún homólogo ANSI equivalente.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md)