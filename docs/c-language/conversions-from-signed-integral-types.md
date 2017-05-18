---
title: Conversiones de tipos enteros con signo | Microsoft Docs
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
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: d7ed58066cecc42492f3b163b130ff8a4ef53ed0
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="conversions-from-signed-integral-types"></a>Conversiones de tipos enteros con signo
Cuando un entero con signo se convierte en un entero sin signo de igual o mayor tamaño y el valor del entero con signo no es negativo, el valor no cambia. La conversión se realiza extendiendo el signo al entero con signo. Un entero con signo se convierte en un entero con signo menor truncando los bits de orden superior. El resultado se interpreta como un valor sin signo, como se muestra en este ejemplo.  
  
```  
int i = -3;  
unsigned short u;  
  
u = i;   
printf_s( "%hu\n", u );  // Prints 65533  
  
```  
  
 Cuando un entero con signo se convierte en un valor flotante no se pierde información, aunque sí puede perderse precisión cuando un valor **long int** o **unsigned long int** se convierte en un valor **float**.  
  
 En la tabla siguiente se resumen las conversiones de tipos enteros con signo. En esta tabla se presupone que el tipo **char** tiene signo de manera predeterminada. Si usa una opción de tiempo de compilación para cambiar el valor predeterminado del tipo **char** a un tipo sin signo, se aplican las conversiones especificadas en la tabla [Conversiones de tipos enteros sin signo](../c-language/conversions-from-unsigned-integral-types.md) para el tipo **unsigned char** en lugar de las conversiones de la tabla siguiente, Conversiones de tipos enteros con signo.  
  
### <a name="conversions-from-signed-integral-types"></a>Conversiones de tipos enteros con signo  
  
|De|Para|Método|  
|----------|--------|------------|  
|**char**1|**short**|Extensión de signo|  
|**char**|**long**|Extensión de signo|  
|**char**|**unsigned char**|Se mantiene el patrón; el bit de orden superior pierde la función de bit con signo|  
|**char**|**unsigned short**|Extensión de signo a **short**; conversión de **short** a **unsigned short**|  
|**char**|**unsigned long**|Extensión de signo a **long**; conversión de **long** a **unsigned long**|  
|**char**|**float**|Extensión de signo a **long**; conversión de **long** a **float**|  
|**char**|**double**|Extensión de signo a **long**; conversión de **long** a **double**|  
|**char**|**long double**|Extensión de signo a **long**; conversión de **long** a **double**|  
|**short**|**char**|Se mantiene el byte de orden inferior|  
|**short**|**long**|Extensión de signo|  
|**short**|**unsigned char**|Se mantiene el byte de orden inferior|  
|**short**|**unsigned short**|Se mantiene el patrón de bits; el bit de orden superior pierde la función de bit con signo|  
|**short**|**unsigned long**|Extensión de signo a **long**; conversión de **long** a **unsigned long**|  
|**short**|**float**|Extensión de signo a **long**; conversión de **long** a **float**|  
|**short**|**double**|Extensión de signo a **long**; conversión de **long** a **double**|  
|**short**|**long double**|Extensión de signo a **long**; conversión de **long** a **double**|  
|**long**|**char**|Se mantiene el byte de orden inferior|  
|**long**|**short**|Se mantiene la palabra de orden inferior|  
|**long**|**unsigned char**|Se mantiene el byte de orden inferior|  
|**long**|**unsigned short**|Se mantiene la palabra de orden inferior|  
|**long**|**unsigned long**|Se mantiene el patrón de bits; el bit de orden superior pierde la función de bit con signo|  
|**long**|**float**|Se representa como **float**. Si **long** no se puede representar exactamente, se pierde precisión.|  
|**long**|**double**|Se representa como **double**. Si **long** no se puede representar exactamente como **double**, se pierde precisión.|  
|**long**|**long double**|Se representa como **double**. Si **long** no se puede representar exactamente como **double**, se pierde precisión.|  
  
 1. Todas las entradas de **char** presuponen que el tipo **char** tiene signo de manera predeterminada.  
  
 **Específicos de Microsoft**  
  
 Para el compilador de C de 32 bits de Microsoft, un entero es equivalente a **long**. La conversión de un valor **int** se realiza de la misma forma que para un valor **long**.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Conversiones de asignación](../c-language/assignment-conversions.md)
