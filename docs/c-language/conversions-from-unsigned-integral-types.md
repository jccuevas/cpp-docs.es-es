---
title: Conversiones de tipos enteros sin signo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 15e1bc61e9b15293290098b9414642d8edf46707
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="conversions-from-unsigned-integral-types"></a>Conversiones de tipos enteros sin signo
Un entero sin signo se convierte en un entero con o sin signo menor truncando los bits de orden superior, o en un entero con o sin signo mayor mediante la extensión de cero (vea la tabla [Conversiones de tipos enteros sin signo](#_clang_table_4..3)).  
  
 Cuando el valor con el tipo entero se reduce a un entero con signo de menor tamaño, o cuando un entero sin signo se convierte en su entero con signo correspondiente, el valor no cambia si se puede representar en el nuevo tipo. Sin embargo, el valor que representa cambia si se establece el bit de signo, como en el ejemplo siguiente.  
  
```  
int j;  
unsigned short k = 65533;  
  
j = k;  
printf_s( "%hd\n", j );   // Prints -3  
```  
  
 Si no se puede representar, el resultado lo define la implementación. Vea [Conversiones de tipos](../c-language/type-cast-conversions.md) para obtener información sobre cómo controla el compilador de C de Microsoft la reducción de enteros. Se produce el mismo comportamiento en la conversión de enteros o en las conversión de tipos de enteros.  
  
 Los valores sin signo se convierten de manera que se conserve su valor y esta conversión no se puede representar directamente en C. La única excepción es una conversión de `unsigned long` a **float**, que pierde como mucho los bits de orden inferior. De lo contrario, el valor se conserva, con signo o sin signo. Cuando un valor de tipo entero se convierte en flotante y el valor está fuera del intervalo representable, el resultado es indefinido. (Vea [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md) para obtener información sobre el intervalo de tipos enteros y de punto flotante).  
  
 En la tabla siguiente se resumen las conversiones de tipos enteros sin signo.  
  
### <a name="conversions-from-unsigned-integral-types"></a>Conversiones de tipos enteros sin signo  
  
|De|Para|Método|  
|----------|--------|------------|  
|`unsigned char`|`char`|Se conserva el patrón de bits; el bit de orden superior se convierte en el bit de signo|  
|`unsigned char`|**short**|Extensión de cero|  
|`unsigned char`|**long**|Extensión de cero|  
|`unsigned char`|**unsigned short**|Extensión de cero|  
|`unsigned char`|`unsigned long`|Extensión de cero|  
|`unsigned char`|**float**|Conversión a **long**; conversión de **long** a **float**|  
|`unsigned char`|**double**|Conversión a **long**; conversión de **long** a **double**|  
|`unsigned char`|`long double`|Conversión a **long**; conversión de **long** a **double**|  
|**unsigned short**|`char`|Se mantiene el byte de orden inferior|  
|**unsigned short**|**short**|Se conserva el patrón de bits; el bit de orden superior se convierte en el bit de signo|  
|**unsigned short**|**long**|Extensión de cero|  
|**unsigned short**|`unsigned char`|Se mantiene el byte de orden inferior|  
|**unsigned short**|`unsigned long`|Extensión de cero|  
|**unsigned short**|**float**|Conversión a **long**; conversión de **long** a **float**|  
|**unsigned short**|**double**|Conversión a **long**; conversión de **long** a **double**|  
|**unsigned short**|`long double`|Conversión a **long**; conversión de **long** a **double**|  
|`unsigned long`|`char`|Se mantiene el byte de orden inferior|  
|`unsigned long`|**short**|Se mantiene la palabra de orden inferior|  
|`unsigned long`|**long**|Se conserva el patrón de bits; el bit de orden superior se convierte en el bit de signo|  
|`unsigned long`|`unsigned char`|Se mantiene el byte de orden inferior|  
|`unsigned long`|**unsigned short**|Se mantiene la palabra de orden inferior|  
|`unsigned long`|**float**|Conversión a **long**; conversión de **long** a **float**|  
|`unsigned long`|**double**|Conversión directa a **double**|  
|`unsigned long`|`long double`|Conversión a **long**; conversión de **long** a **double**|  
  
 **Específicos de Microsoft**  
  
 Para el compilador de C de 32 bits de Microsoft, el tipo `unsigned int` es equivalente al tipo `unsigned long`. La conversión de un valor `unsigned int` se realiza de la misma forma que la conversión de un `unsigned long`. Las conversiones de valores `unsigned long` a **float** no son exactas si el valor que se está convirtiendo es mayor que el valor **long** positivo máximo.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Conversiones de asignación](../c-language/assignment-conversions.md)