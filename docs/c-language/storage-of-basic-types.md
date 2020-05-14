---
title: Almacenamiento de tipos básicos
ms.date: 10/02/2019
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
ms.openlocfilehash: 64c642df4dd85e4aa09f90a143b8aa67c28b7dc2
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998764"
---
# <a name="storage-of-basic-types"></a>Almacenamiento de tipos básicos

En la tabla siguiente se resume el almacenamiento asociado a cada tipo básico.

## <a name="sizes-of-fundamental-types"></a>Tamaños de los tipos fundamentales

|Tipo|Almacenamiento|
|----------|-------------|
|**char**, **unsigned char**, **signed char**|1 byte|
|**short**, **unsigned short**|2 bytes|
|**int**, **unsigned int**|4 bytes|
|**long**, **unsigned long**|4 bytes|
|**long long**, **unsigned long long**|8 bytes|
|**float**|4 bytes|
|**double**|8 bytes|
|**long double**|8 bytes|

Los tipos de datos de C entran en categorías generales. Los *tipos enteros* incluyen **int**, **char**, **short**, **long** y **long long**. Estos tipos se pueden calificar con **signed** o **unsigned**, y se puede usar **unsigned** por sí solo como abreviatura para **unsigned int**. Los tipos de enumeración (**enum**) también se tratan como tipos enteros para la mayoría de los propósitos. Los *tipos flotantes* incluyen **float**, **double** y **long double**. Los *tipos aritméticos* incluyen todos los tipos flotantes y enteros.

## <a name="see-also"></a>Vea también

[Declaraciones y tipos](../c-language/declarations-and-types.md)
