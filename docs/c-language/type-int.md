---
title: Tipo int | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- int data type
- type int
- portability [C++], type int
- signed integers
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ed3fcd9b11a76f8ff211bf8be5cf50ee6664cda
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="type-int"></a>Tipo int
El tamaño de un elemento `int` con o sin signo es el tamaño estándar de un entero en un equipo determinado. Por ejemplo, en los sistemas operativos de 16 bits, el tipo `int` suele ser de 16 bits o 2 bytes. En los sistemas operativos de 32 bits, el tipo `int` suele ser de 32 bits o 4 bytes. Así, el tipo `int` es equivalente al tipo `short int` o **long int**, y el tipo `unsigned int` es equivalente al tipo **unsigned short** o `unsigned long`, dependiendo del entorno de destino. Todos los tipos `int` representan valores con signo, a menos que se especifique lo contrario.  
  
 Los especificadores de tipo `int` y `unsigned int` (o simplemente `unsigned`) definen ciertas características del lenguaje C (por ejemplo, el tipo `enum`). En estos casos, las definiciones de `int` y unsigned int para una implementación determinada determinan el almacenamiento real.  
  
 **Específicos de Microsoft**  
  
 Los enteros con signo se representan en forma de complemento de dos. El bit más significativo contiene el signo: 1 si es negativo y 0 si es positivo o cero. El intervalo de valores se proporciona en [Límites de enteros de C++](../c-language/cpp-integer-limits.md), que se toma del archivo de encabezado LIMITS.H.  
  
 **FIN de Específicos de Microsoft**  
  
> [!NOTE]
>  Los especificadores de tipo int y unsigned int se usan con bastante frecuencia en los programas de C, porque permiten que un equipo determinado administre los valores enteros del modo más eficaz para ese equipo. Sin embargo, puesto que los tamaños de los tipos int y unsigned int varían, es posible que los programas que dependan de un tamaño de int concreto no sean portables a otros equipos. Para que los programas sean más portables, puede usar expresiones con el operador sizeof (como se describe en [El operador sizeof](../c-language/sizeof-operator-c.md)), en lugar de tamaños de datos codificados de forma rígida.  
  
## <a name="see-also"></a>Vea también  
 [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md)