---
title: Conversiones de tipos enteros sin signo
ms.date: 10/02/2019
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
ms.openlocfilehash: 3099f0113103223e392dc20560899b4a6e3ebf20
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998790"
---
# <a name="conversions-from-unsigned-integral-types"></a>Conversiones de tipos enteros sin signo

Cuando un entero sin signo se convierte a un entero o a un tipo de punto flotante, si el valor original se puede representar en el tipo del resultado, el valor no cambia.

Cuando un entero sin signo se convierte a un entero de mayor tamaño, el valor se completa con ceros. Cuando se convierte a un entero de menor tamaño, los bits de orden superior se truncan. El resultado se interpreta con el tipo del resultado, como se muestra en este ejemplo.

```C
unsigned k = 65533;
short j;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

Al convertir un entero sin signo a un tipo de punto flotante, si el valor original no se puede representar exactamente en el tipo del resultado, el resultado será el siguiente valor más alto o más bajo que se puede representar.

Consulte [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md) para obtener información sobre los tamaños de tipos enteros y de punto flotante.

**Específicos de Microsoft**

En el compilador de Microsoft, **unsigned** (o **unsigned int**) y **unsigned long** son tipos distintos, pero equivalentes. La conversión de un valor **unsigned int** se realiza de la misma forma que la de un **unsigned long**.

**FIN de Específicos de Microsoft**

En la tabla siguiente se resumen las conversiones de tipos enteros sin signo.

## <a name="table-of-conversions-from-unsigned-integral-types"></a>Tabla de conversiones de tipos enteros sin signo

|De|En|Método|
|----------|--------|------------|
|**unsigned char**|**char**|Se conserva el patrón de bits; el bit de orden superior se convierte en el bit de signo|
|**unsigned char**|**short**|Extensión de cero|
|**unsigned char**|**long**|Extensión de cero|
|**unsigned char**|**long long**|Extensión de cero|
|**unsigned char**|**unsigned short**|Extensión de cero|
|**unsigned char**|**unsigned long**|Extensión de cero|
|**unsigned char**|**unsigned long long**|Extensión de cero|
|**unsigned char**|**float**|Conversión a **long**; conversión de **long** a **float**|
|**unsigned char**|**double**|Conversión a **long**; conversión de **long** a **double**|
|**unsigned char**|**long double**|Conversión a **long**; conversión de **long** a **double**|
|**unsigned short**|**char**|Se mantiene el byte de orden inferior|
|**unsigned short**|**short**|Se conserva el patrón de bits; el bit de orden superior se convierte en el bit de signo|
|**unsigned short**|**long**|Extensión de cero|
|**unsigned short**|**long long**|Extensión de cero|
|**unsigned short**|**unsigned char**|Se mantiene el byte de orden inferior|
|**unsigned short**|**unsigned long**|Extensión de cero|
|**unsigned short**|**unsigned long long**|Extensión de cero|
|**unsigned short**|**float**|Conversión a **long**; conversión de **long** a **float**|
|**unsigned short**|**double**|Conversión a **long**; conversión de **long** a **double**|
|**unsigned short**|**long double**|Conversión a **long**; conversión de **long** a **double**|
|**unsigned long**|**char**|Se mantiene el byte de orden inferior|
|**unsigned long**|**short**|Se mantiene la palabra de orden inferior|
|**unsigned long**|**long**|Se conserva el patrón de bits; el bit de orden superior se convierte en el bit de signo|
|**unsigned long**|**long long**|Extensión de cero|
|**unsigned long**|**unsigned char**|Se mantiene el byte de orden inferior|
|**unsigned long**|**unsigned short**|Se mantiene la palabra de orden inferior|
|**unsigned long**|**unsigned long long**|Extensión de cero|
|**unsigned long**|**float**|Conversión a **long**; conversión de **long** a **float**|
|**unsigned long**|**double**|Conversión directa a **double**|
|**unsigned long**|**long double**|Conversión a **long**; conversión de **long** a **double**|
|**unsigned long long**|**char**|Se mantiene el byte de orden inferior|
|**unsigned long long**|**short**|Se mantiene la palabra de orden inferior|
|**unsigned long long**|**long**|Se mantiene el valor dword de orden inferior|
|**unsigned long long**|**long long**|Se conserva el patrón de bits; el bit de orden superior se convierte en el bit de signo|
|**unsigned long long**|**unsigned char**|Se mantiene el byte de orden inferior|
|**unsigned long long**|**unsigned short**|Se mantiene la palabra de orden inferior|
|**unsigned long long**|**unsigned long**|Se mantiene el valor dword de orden inferior|
|**unsigned long long**|**float**|Conversión a **long**; conversión de **long** a **float**|
|**unsigned long long**|**double**|Conversión directa a **double**|
|**unsigned long long**|**long double**|Conversión a **long**; conversión de **long** a **double**|

## <a name="see-also"></a>Vea también

[Conversiones de asignación](../c-language/assignment-conversions.md)
