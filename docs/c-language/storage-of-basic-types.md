---
title: "Almacenamiento de tipos básicos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dff8df934a0c812ca798d5a1e87188e2468902ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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