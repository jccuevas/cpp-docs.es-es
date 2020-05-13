---
title: switchInstrucción (C)
ms.date: 04/25/2020
f1_keywords:
- switch
helpviewer_keywords:
- switch keyword [C]
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
no-loc:
- switch
- case
- default
- break
ms.openlocfilehash: 5858447602a28dcc5573aa3138e869d106b5aa23
ms.sourcegitcommit: 2f9ff2041d70c406df76c5053151192aad3937ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "82587366"
---
# <a name="switch-statement-c"></a>`switch`Instrucción (C)

Las __`switch`__ instrucciones __`case`__ y ayudan a controlar las operaciones condicionales y de bifurcación complejas. La __`switch`__ instrucción transfiere el control a una instrucción dentro de su cuerpo.

## <a name="syntax"></a>Sintaxis

> *`selection-statement`*:<br/>
> &nbsp;&nbsp;&nbsp;&nbsp; __`switch (`__&nbsp;*`expression`* &nbsp;__`)`__&nbsp;*`statement`*

> *`labeled-statement`*:<br/>
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__&nbsp;*`constant-expression`*&nbsp;__`:`__&nbsp;*`statement`*<br/>
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__&nbsp;__`:`__&nbsp;*`statement`*

## <a name="remarks"></a>Observaciones

Una __`switch`__ instrucción hace que el control se transfiera *`labeled-statement`* a uno en su cuerpo de instrucción, dependiendo del valor *`expression`* de.

Los valores de *`expression`* y cada *`constant-expression`* deben tener un tipo entero. Un *`constant-expression`* debe tener un valor entero constante no ambiguo en tiempo de compilación.

El control pasa a **`case`** la instrucción *`constant-expression`* cuyo valor coincide con el *`expression`* valor de. La __`switch`__ instrucción puede incluir cualquier número de __`case`__ instancias. Sin embargo, dos *`constant-expression`* valores de la misma __`switch`__ instrucción no pueden tener el mismo valor. La ejecución del __`switch`__ cuerpo de la instrucción comienza en la primera instrucción de o después *`labeled-statement`* de la coincidencia. La ejecución continúa hasta el final del cuerpo o hasta que una __`break`__ instrucción transfiere el control fuera del cuerpo.

El uso de __`switch`__ la instrucción normalmente tiene un aspecto similar al siguiente:

```C
switch ( expression )
{
    // declarations
    // . . .
    case constant_expression:
        // statements executed if the expression equals the
        // value of this constant_expression
        break;
    default:
        // statements executed if expression does not equal
        // any case constant_expression
}
```

Puede usar la instrucción __`break`__ para finalizar el procesamiento de una instrucción determinada con etiqueta dentro de __`switch`__ la instrucción. Se ramifica hasta el final de la __`switch`__ instrucción. Sin __`break`__, el programa continúa con la siguiente instrucción etiquetada y ejecuta las instrucciones hasta que se __`break`__ alcanza un o el final de la instrucción. Esta continuación puede ser deseable en algunas situaciones.

La __`default`__ instrucción se ejecuta si ningún __`case`__ *`constant-expression`* valor es igual al valor de *`expression`*. Si no hay ninguna __`default`__ instrucción y no se __`case`__ encuentra ninguna coincidencia, no se ejecuta ninguna de las __`switch`__ instrucciones del cuerpo. Puede haber como máximo una __`default`__ instrucción. La __`default`__ instrucción no tiene que estar al final. Puede aparecer en cualquier parte del cuerpo de la __`switch`__ instrucción. Una __`case`__ etiqueta __`default`__ o solo puede aparecer dentro de __`switch`__ una instrucción.

El tipo de __`switch`__ *`expression`* y __`case`__ *`constant-expression`* debe ser entero. El valor de cada __`case`__ *`constant-expression`* debe ser único dentro del cuerpo de la instrucción.

Las __`case`__ etiquetas __`default`__ y del cuerpo __`switch`__ de la instrucción solo son significativas en la prueba inicial que determina dónde se inicia la ejecución en el cuerpo de la instrucción. __`switch`__ las instrucciones se pueden anidar. Las variables estáticas se inicializan antes de ejecutarse __`switch`__ en cualquier instrucción.

> [!NOTE]
> Las declaraciones pueden aparecer en el encabezado de la instrucción compuesta que forma __`switch`__ el cuerpo, pero las inicializaciones incluidas en las declaraciones no se realizan. La __`switch`__ instrucción transfiere el control directamente a una instrucción ejecutable dentro del cuerpo y omite las líneas que contienen inicializaciones.

En los siguientes ejemplos __`switch`__ se muestran instrucciones:

```C
switch( c )
{
    case 'A':
        capital_a++;
    case 'a':
        letter_a++;
    default :
        total++;
}
```

__`switch`__ Las tres instrucciones del cuerpo de este ejemplo se ejecutan si `c` es igual a `'A'`, ya que __`break`__ no aparece ninguna instrucción antes __`case`__ de lo siguiente. El control de la ejecución se transfiere a la primera instrucción (`capital_a++;`) y continúa en orden con el resto del cuerpo. Si `c` es igual a `'a'`, se incrementan `letter_a` y `total`. Solo `total` se incrementa cuando `c` no es igual `'A'` a `'a'`o.

```C
switch( i )
{
    case -1:
        n++;
        break;
    case 0 :
        z++;
        break;
    case 1 :
        p++;
        break;
}
```

En este ejemplo, una __`break`__ instrucción sigue cada instrucción del __`switch`__ cuerpo. La __`break`__ instrucción fuerza una salida del cuerpo de la instrucción después de ejecutar una instrucción. Si `i` es igual a -1, solo se incrementa `n`. La __`break`__ siguiente instrucción `n++;` hace que el control de ejecución pase fuera del cuerpo de la instrucción, omitiendo las instrucciones restantes. De igual forma, si `i` es igual a 0, solo se incrementa `z`; si `i` es igual a 1, solo se incrementa `p`. La instrucción __`break`__ final no es estrictamente necesaria, ya que el control sale del cuerpo al final de la instrucción compuesta. Se incluye por coherencia.

Una sola instrucción puede contener varias __`case`__ etiquetas, como se muestra en el ejemplo siguiente:

```C
switch( c )
{
    case 'a' :
    case 'b' :
    case 'c' :
    case 'd' :
    case 'e' :
    case 'f' :  convert_hex(c);
}
```

En este ejemplo, si *constant-expression* es cualquier letra entre `'a'` y `'f'`, se llama a la función `convert_hex`.

### <a name="microsoft-specific"></a>Específico de Microsoft

Microsoft C no limita el número de __`case`__ valores en una __`switch`__ instrucción. El número solo está limitado por la memoria disponible. ANSI C requiere que se permitan al menos 257 __`case`__ etiquetas __`switch`__ en una instrucción.

default Para Microsoft C es que las extensiones de Microsoft están habilitadas. Use la opción del compilador [/za](../build/reference/za-ze-disable-language-extensions.md) para deshabilitar estas extensiones.

## <a name="see-also"></a>Consulte también

[switchStatement (C++)](../cpp/switch-statement-cpp.md)
