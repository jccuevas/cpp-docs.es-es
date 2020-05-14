---
title: Conversiones de tipos enteros con signo
ms.date: 10/02/2019
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
ms.openlocfilehash: 79608b5ca4335ee3c30bdab27e7efade5b7e2f54
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998725"
---
# <a name="conversions-from-signed-integral-types"></a>Conversiones de tipos enteros con signo

Cuando un entero con signo se convierte a un entero o a un tipo de punto flotante, si el valor original se puede representar en el tipo del resultado, el valor no cambia.

Cuando un entero con signo se convierte a un entero de mayor tamaño, se agrega al valor la extensión de signo. Cuando se convierte a un entero de menor tamaño, los bits de orden superior se truncan. El resultado se interpreta con el tipo del resultado, como se muestra en este ejemplo:

```C
int i = -3;
unsigned short u;

u = i;
printf_s( "%hu\n", u );  // Prints 65533
```

Al convertir un entero con signo a un tipo de punto flotante, si el valor original no se puede representar exactamente en el tipo del resultado, el resultado será el siguiente valor más alto o más bajo que se puede representar.

Para obtener información sobre los tamaños de tipos enteros y de punto flotante, consulte [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md).

En la tabla siguiente se resumen las conversiones de tipos enteros con signo. Se presupone que el tipo **char** tiene signo de manera predeterminada. Si usa una opción de tiempo de compilación para cambiar el valor predeterminado del tipo **char** a un tipo sin signo, se aplican las conversiones especificadas en la tabla [Conversiones de tipos enteros sin signo](../c-language/conversions-from-unsigned-integral-types.md) para el tipo **unsigned char**, en lugar de las conversiones de esta tabla.

**Específicos de Microsoft**

En el compilador de Microsoft, **int** y **long** son tipos distintos, pero equivalentes. La conversión de un valor **int** se realiza de la misma forma que la conversión de un valor **long**.

**FIN de Específicos de Microsoft**

## <a name="table-of-conversions-from-signed-integral-types"></a>Tabla de conversiones de tipos enteros con signo

|De|En|Método|
|----------|--------|------------|
|**char**<sup>1</sup>|**short**|Extensión de signo|
|**char**|**long**|Extensión de signo|
|**char**|**long long**|Extensión de signo|
|**char**|**unsigned char**|Se mantiene el patrón; el bit de orden superior pierde la función de bit con signo|
|**char**|**unsigned short**|Extensión de signo a **short**; conversión de **short** a **unsigned short**|
|**char**|**unsigned long**|Extensión de signo a **long**; conversión de **long** a **unsigned long**|
|**char**|**unsigned long long**|Extensión de signo a **long long**; conversión de **long long** a **unsigned long long**|
|**char**|**float**|Extensión de signo a **long**; conversión de **long** a **float**|
|**char**|**double**|Extensión de signo a **long**; conversión de **long** a **double**|
|**char**|**long double**|Extensión de signo a **long**; conversión de **long** a **double**|
|**short**|**char**|Se mantiene el byte de orden inferior|
|**short**|**long**|Extensión de signo|
|**short**|**long long**|Extensión de signo|
|**short**|**unsigned char**|Se mantiene el byte de orden inferior|
|**short**|**unsigned short**|Se mantiene el patrón de bits; el bit de orden superior pierde la función de bit con signo|
|**short**|**unsigned long**|Extensión de signo a **long**; conversión de **long** a **unsigned long**|
|**short**|**unsigned long long**|Extensión de signo a **long long**; conversión de **long long** a **unsigned long long**|
|**short**|**float**|Extensión de signo a **long**; conversión de **long** a **float**|
|**short**|**double**|Extensión de signo a **long**; conversión de **long** a **double**|
|**short**|**long double**|Extensión de signo a **long**; conversión de **long** a **double**|
|**long**|**char**|Se mantiene el byte de orden inferior|
|**long**|**short**|Se mantiene la palabra de orden inferior|
|**long**|**long long**|Extensión de signo|
|**long**|**unsigned char**|Se mantiene el byte de orden inferior|
|**long**|**unsigned short**|Se mantiene la palabra de orden inferior|
|**long**|**unsigned long**|Se mantiene el patrón de bits; el bit de orden superior pierde la función de bit con signo|
|**long**|**unsigned long long**|Extensión de signo a **long long**; conversión de **long long** a **unsigned long long**|
|**long**|**float**|Se representa como **float**. Si **long** no se puede representar exactamente, se pierde precisión.|
|**long**|**double**|Se representa como **double**. Si **long** no se puede representar exactamente como **double**, se pierde precisión.|
|**long**|**long double**|Se representa como **double**. Si **long** no se puede representar exactamente como **double**, se pierde precisión.|
|**long long**|**char**|Se mantiene el byte de orden inferior|
|**long long**|**short**|Se mantiene la palabra de orden inferior|
|**long long**|**long**|Se mantiene el valor dword de orden inferior|
|**long long**|**unsigned char**|Se mantiene el byte de orden inferior|
|**long long**|**unsigned short**|Se mantiene la palabra de orden inferior|
|**long long**|**unsigned long**|Se mantiene el valor dword de orden inferior|
|**long long**|**unsigned long long**|Se mantiene el patrón de bits; el bit de orden superior pierde la función de bit con signo|
|**long long**|**float**|Se representa como **float**. Si **long long** no se puede representar exactamente, se pierde precisión.|
|**long long**|**double**|Se representa como **double**. Si **long long** no se puede representar exactamente como **double**, se pierde precisión.|
|**long long**|**long double**|Se representa como **double**. Si **long long** no se puede representar exactamente como **double**, se pierde precisión.|

<sup>1</sup> Todas las entradas de **char** presuponen que el tipo **char** tiene signo de manera predeterminada.

## <a name="see-also"></a>Vea también

[Conversiones de asignación](../c-language/assignment-conversions.md)
