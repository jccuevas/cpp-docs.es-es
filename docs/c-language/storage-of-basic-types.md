---
title: Almacenamiento de tipos básicos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- specifiers [C++], type
- integral types, storage
- storage [C++], types
- floating-point numbers, storage
- type specifiers [C++], sizes
- arithmetic operations [C++], types
- int data type
- short data type
- signed types [C++], storage
- long double keyword [C], storage
- long keyword [C]
- double data type, storage
- types [C], arithmetic
- integral types
- data types [C], specifiers
- storing types [C++]
- unsigned types [C++], storage
- data types [C], storage
ms.assetid: bd1f33c1-c6b9-4558-8a72-afb21aef3318
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eafe81dc684300cb7fdf65137c2f7e45010285b0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388120"
---
# <a name="storage-of-basic-types"></a>Almacenamiento de tipos básicos
En la tabla siguiente se resume el almacenamiento asociado a cada tipo básico.  
  
### <a name="sizes-of-fundamental-types"></a>Tamaños de los tipos fundamentales  
  
|Tipo|Almacenamiento|  
|----------|-------------|  
|`char`, `unsigned char`, **signed char**|1 byte|  
|**short**, **unsigned short**|2 bytes|  
|`int`, `unsigned int`|4 bytes|  
|**long**, `unsigned long`|4 bytes|  
|**float**|4 bytes|  
|**double**|8 bytes|  
|`long double`|8 bytes|  
  
 Los tipos de datos de C entran en categorías generales. Los "tipos enteros" incluyen `char`, `int`, **short**, **long**, **signed**, `unsigned` y `enum`. Los "tipos de punto flotante" incluyen **float**, **double** y `long double`. Los “tipos aritméticos” incluyen todos los tipos de punto flotante y enteros.  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones y tipos](../c-language/declarations-and-types.md)