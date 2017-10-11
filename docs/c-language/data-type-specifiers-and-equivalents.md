---
title: Especificadores de tipo de datos y equivalentes | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 0fbc76f70eba6fab46e709978bbadcd10312af6e
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

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
