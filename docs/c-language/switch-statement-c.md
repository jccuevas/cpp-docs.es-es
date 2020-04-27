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
ms.openlocfilehash: 12163e85110092e3e372fa496cf42efd7574ea8d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167681"
---
# <a name="opno-locswitch-statement-c"></a>switchInstrucción (C)

Las **switch** instrucciones **case** y ayudan a controlar las operaciones condicionales y de bifurcación complejas. La **switch** instrucción transfiere el control a una instrucción dentro de su cuerpo.

## <a name="syntax"></a>Sintaxis

*Selection-Statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`switch (`***Expression* **`)`** ( *instrucción* )

*etiquetad-Statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`case`**  *Constant-Expression***`:`**(*instrucción* )    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`default :`**  *privacidad*

El control pasa a la instrucción cuya **case** *Constant-Expression* coincide con el valor de ** switch (** *Expression* **)**. La **switch** instrucción puede incluir cualquier número de **case** instancias. Sin embargo, dos case constantes de la misma **switch** instrucción no pueden tener el mismo valor. La ejecución del cuerpo de la instrucción comienza en la instrucción seleccionada. Continúa hasta el final del cuerpo o hasta que una **break** instrucción transfiere el control fuera del cuerpo.

El uso de **switch** la instrucción normalmente tiene un aspecto similar al siguiente:

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

Puede usar la instrucción **break** para finalizar el procesamiento de una instrucción determinada con etiqueta dentro de **switch** la instrucción. Se ramifica hasta el final de la **switch** instrucción. Sin **break**, el programa continúa con la siguiente instrucción etiquetada y ejecuta las instrucciones hasta que se **break** alcanza un o el final de la instrucción. Esta continuación puede ser deseable en algunas situaciones.

La **default** instrucción se ejecuta si ninguna **case** *expresión constante* es igual al valor de ** switch (** *expresión* **)**. Si no hay ninguna **default** instrucción y no se **case** encuentra ninguna coincidencia, no se ejecuta ninguna de las **switch** instrucciones del cuerpo. Puede haber como máximo una **default** instrucción. La **default** instrucción no tiene que estar al final. Puede aparecer en cualquier parte del cuerpo de la **switch** instrucción. Una **case** etiqueta **default** o solo puede aparecer dentro de **switch** una instrucción.

El tipo de **switch** *Expression* y **case** *Constant-Expression* deben ser enteros. El valor de cada **case** *expresión constante* debe ser único dentro del cuerpo de la instrucción.

Las **case** etiquetas **default** y del cuerpo **switch** de la instrucción solo son significativas en la prueba inicial que determina dónde se inicia la ejecución en el cuerpo de la instrucción. **switch** las instrucciones se pueden anidar. Las variables estáticas se inicializan antes de ejecutarse **switch** en cualquier instrucción.

> [!NOTE]
> Las declaraciones pueden aparecer en el encabezado de la instrucción compuesta que forma **switch** el cuerpo, pero las inicializaciones incluidas en las declaraciones no se realizan. La **switch** instrucción transfiere el control directamente a una instrucción ejecutable dentro del cuerpo y omite las líneas que contienen inicializaciones.

En los siguientes ejemplos **switch** se muestran instrucciones:

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

**switch** Las tres instrucciones del cuerpo de este ejemplo se ejecutan si `c` es igual a `'A'`, ya que **break** no aparece ninguna instrucción antes casede lo siguiente. El control de la ejecución se transfiere a la primera instrucción (`capital_a++;`) y continúa en orden con el resto del cuerpo. Si `c` es igual a `'a'`, se incrementan `letter_a` y `total`. Solo `total` se incrementa cuando `c` no es igual `'A'` a `'a'`o.

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

En este ejemplo, una **break** instrucción sigue cada instrucción del **switch** cuerpo. La **break** instrucción fuerza una salida del cuerpo de la instrucción después de ejecutar una instrucción. Si `i` es igual a -1, solo se incrementa `n`. La **break** siguiente instrucción `n++;` hace que el control de ejecución pase fuera del cuerpo de la instrucción, omitiendo las instrucciones restantes. De igual forma, si `i` es igual a 0, solo se incrementa `z`; si `i` es igual a 1, solo se incrementa `p`. La instrucción **break** final no es estrictamente necesaria, ya que el control sale del cuerpo al final de la instrucción compuesta. Se incluye por coherencia.

Una sola instrucción puede contener varias **case** etiquetas, como se muestra en el ejemplo siguiente:

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

Microsoft C no limita el número de case valores en una **switch** instrucción. El número solo está limitado por la memoria disponible. ANSI C requiere que se permitan al menos 257 case etiquetas **switch** en una instrucción.

default Para Microsoft C es que las extensiones de Microsoft están habilitadas. Use la opción del compilador [/za](../build/reference/za-ze-disable-language-extensions.md) para deshabilitar estas extensiones.

## <a name="see-also"></a>Consulte también

[switchStatement (C++)](../cpp/switch-statement-cpp.md)
