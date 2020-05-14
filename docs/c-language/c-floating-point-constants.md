---
title: Constantes de punto flotante de C
ms.date: 11/04/2016
helpviewer_keywords:
- types [C], constants
- floating-point numbers, floating-point constants
- constants, floating-point
- floating-point constants
- floating-point constants, about floating-point constants
- double data type, floating-point constants
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
ms.openlocfilehash: 5e17490926ee328c3a4ca03b1de9cb6e752959a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325686"
---
# <a name="c-floating-point-constants"></a>Constantes de punto flotante de C

Una "constante de punto flotante" es un número decimal que representa un número real con signo. La representación de un número real con signo incluye una parte entera, una parte fraccionaria y un exponente. Utilice constantes de punto flotante para representar valores de punto flotante que no se pueden modificar.

## <a name="syntax"></a>Sintaxis

*floating-point-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*fractional-constant* *exponent-part*<sub>opt</sub> *floating-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *exponent-part* *floating-suffix*<sub>opt</sub>

*fractional-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence*<sub>opt</sub> **.** *digit-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence*  **.**

*exponent-part*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**e** *sign*<sub>opt</sub> *digit-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**E** *sign*<sub>opt</sub> *digit-sequence*

*sign*: uno de<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **+ -**

*digit-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *digit*

*floating-suffix*: uno de<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**f l F L**

Se pueden omitir los dígitos que hay delante del separador decimal (la parte entera del valor) o los dígitos que hay detrás del separador decimal (la parte fraccionaria), pero no ambos. Solo se puede omitir el separador decimal si se incluye un exponente. No se pueden utilizar caracteres de espacio en blanco para separar los dígitos o los caracteres de la constante.

En los ejemplos siguientes se muestran algunas formas de constantes y expresiones de punto flotante:

```C
15.75
1.575E1   /* = 15.75   */
1575e-2   /* = 15.75   */
-2.5e-3   /* = -0.0025 */
25E-4     /* =  0.0025 */
```

Las constantes de punto flotante son positivas a menos que vayan precedidas de un signo menos ( **-** ). En este caso, el signo menos se trata como un operador unario de negación aritmética. Las constantes de punto flotante tienen el tipo `float`, `double` o `long double`.

Una constante de punto flotante sin un sufijo **f**, **F**, **l** o **L** tiene el tipo `double`. Si el sufijo es la letra **f** o **F**, la constante tiene el tipo `float`. Si el sufijo es la letra **l** o **L**, tiene el tipo `long double`. Por ejemplo:

```C
10.0L  /* Has type long double  */
10.0F  /* Has type float        */
```

Tenga en cuenta que el compilador deMicrosoft C representa internamente `long double` igual que el tipo `double`. Vea [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md) para obtener información sobre los tipos `double`, `float` y `long double`.

Se puede omitir la parte entera de la constante de punto flotante, como se muestra en los ejemplos siguientes. El número .75 se puede expresar de muchas maneras, incluidas las siguientes:

```C
.0075e2
0.075e1
.075e1
75e-2
```

## <a name="see-also"></a>Vea también

[Constantes de C](../c-language/c-constants.md)
