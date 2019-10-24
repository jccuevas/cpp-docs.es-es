---
title: Tipo int
ms.date: 11/04/2016
helpviewer_keywords:
- int data type
- type int
- portability [C++], type int
- signed integers
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
ms.openlocfilehash: c69d2308abe2ee3d7e6b392f5a9e78a004791501
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778360"
---
# <a name="type-int"></a>Tipo int

El tamaño de un elemento `int` con o sin signo es el tamaño estándar de un entero en un equipo determinado. Por ejemplo, en los sistemas operativos de 16 bits, el tipo `int` suele ser de 16 bits o 2 bytes. En los sistemas operativos de 32 bits, el tipo `int` suele ser de 32 bits o 4 bytes. Así, el tipo `int` es equivalente al tipo `short int` o **long int**, y el tipo `unsigned int` es equivalente al tipo **unsigned short** o `unsigned long`, dependiendo del entorno de destino. Todos los tipos `int` representan valores con signo, a menos que se especifique lo contrario.

Los especificadores de tipo `int` y `unsigned int` (o simplemente `unsigned`) definen ciertas características del lenguaje C (por ejemplo, el tipo `enum`). En estos casos, las definiciones de `int` y unsigned int para una implementación determinada determinan el almacenamiento real.

**Específicos de Microsoft**

Los enteros con signo se representan en forma de complemento de dos. El bit más significativo contiene el signo: 1 si es negativo y 0 si es positivo o cero. El intervalo de valores se proporciona en los [límites C++ de C y enteros](../c-language/cpp-integer-limits.md), que se toman de los límites. Archivo de encabezado H.

**FIN de Específicos de Microsoft**

> [!NOTE]
>  Los especificadores de tipo int y unsigned int se usan con bastante frecuencia en los programas de C, porque permiten que un equipo determinado administre los valores enteros del modo más eficaz para ese equipo. Sin embargo, puesto que los tamaños de los tipos int y unsigned int varían, es posible que los programas que dependan de un tamaño de int concreto no sean portables a otros equipos. Para que los programas sean más portables, puede usar expresiones con el operador sizeof (como se describe en [El operador sizeof](../c-language/sizeof-operator-c.md)), en lugar de tamaños de datos codificados de forma rígida.

## <a name="see-also"></a>Vea también

[Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md)
