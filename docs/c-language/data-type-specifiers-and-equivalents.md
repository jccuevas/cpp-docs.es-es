---
title: Especificadores de tipo de datos y equivalentes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type specifiers [C++], list
- widening integers
- data types [C++], equivalents
- sign-extending integral types
- zero-extending
- identifiers, data type
- data types [C++], specifiers
- simple types, names
- type names [C++], simple
ms.assetid: 0d4b515a-4f68-4786-83cf-a5d43c7cb6f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7380fa654ba7e886800d784966b77cb8c9d1dab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386155"
---
# <a name="data-type-specifiers-and-equivalents"></a>Especificadores de tipo de datos y equivalentes
En este documento se utilizan normalmente las formas de especificadores de tipos que se incluyen en la tabla siguiente, en lugar de formas largas, y se supone que el tipo `char` es un tipo con signo de forma predeterminada. Por consiguiente, en este documento, `char` es equivalente a **signed char**.  
  
### <a name="type-specifiers-and-equivalents"></a>Especificadores de tipo y sus equivalentes  
  
|Especificador de tipo|Equivalentes|  
|--------------------|---------------------|  
|**signed char**1|**char**|  
|**signed int**|**signed**, **int**|  
|**signed short int**|**short**, **signed short**|  
|**signed long int**|**long**, **signed long**|  
|**unsigned char**|—|  
|**unsigned int**|**unsigned**|  
|**unsigned short int**|**unsigned short**|  
|**unsigned long int**|**unsigned long**|  
|**float**|—|  
|**long double**2|—|  
  
 1 Cuando hace que **char** sea un tipo sin signo de manera predeterminada (mediante la opción del compilador /J), no puede abreviar **signed char** como **char**.  
  
 2 En los sistemas operativos de 32 y 64 bits, el compilador de Microsoft C asigna **long double** al tipo **double**.  
  
 **Específicos de Microsoft**  
  
 Puede especificar la opción del compilador /J para cambiar el tipo predeterminado de **char** de signed a unsigned. Cuando esta opción está activada, **char** tiene el mismo significado que **unsigned char**, y será preciso usar la palabra clave **signed** para declarar un valor de carácter con signo. Si un valor **char** se declara explícitamente como con signo, la opción /J no le afecta; el valor se completa con un signo cuando se amplía a un tipo **int**. El tipo **char** se completa con ceros cuando se amplía al tipo **int**.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Especificadores de tipos de C](../c-language/c-type-specifiers.md)