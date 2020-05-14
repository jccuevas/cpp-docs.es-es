---
title: Instrucción switch (C)
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
ms.openlocfilehash: eb18b6244318b595e67cc45f99dfcde314866f55
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825683"
---
# <a name="switch-statement-c"></a>Instrucción `switch` (C)

Las instrucciones __`switch`__ y __`case`__ ayudan a controlar las operaciones condicionales y de bifurcación complejas. La instrucción __`switch`__ transfiere el control a una instrucción dentro del cuerpo.

## <a name="syntax"></a>Sintaxis

> *`selection-statement`* :\
> &nbsp;&nbsp;&nbsp;&nbsp; __`switch (`__ &nbsp; *`expression`* &nbsp; __`)`__ &nbsp; *`statement`*

> *`labeled-statement`* :\
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__ &nbsp; *`constant-expression`* &nbsp; __`:`__ &nbsp; *`statement`* \
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__ &nbsp; __`:`__ &nbsp; *`statement`*

## <a name="remarks"></a>Comentarios

Una instrucción __`switch`__ hace que el control se transfiera a una instrucción *`labeled-statement`* en el cuerpo de la instrucción, en función del valor de *`expression`* .

Los valores de *`expression`* y cada *`constant-expression`* deben tener un tipo entero. Una *`constant-expression`* debe tener un valor entero constante no ambiguo en tiempo de compilación.

El control pasa a la instrucción **`case`** cuyo valor *`constant-expression`* coincide con el valor de *`expression`* . La instrucción __`switch`__ puede incluir cualquier número de instancias de __`case`__ . Aun así, dos valores *`constant-expression`* dentro de la misma instrucción __`switch`__ no pueden tener el mismo valor. La ejecución del cuerpo de la instrucción __`switch`__ comienza en la primera instrucción dentro o después de la instrucción *`labeled-statement`* correspondiente. La ejecución continúa hasta el final del cuerpo o hasta que una instrucción __`break`__ transfiere el control fuera del cuerpo.

El uso de la instrucción __`switch`__ suele tener una apariencia similar a lo siguiente:

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

Puede usar la instrucción __`break`__ para finalizar el procesamiento de una instrucción con etiqueta concreta dentro de la instrucción __`switch`__ . Se bifurca al final de la instrucción __`switch`__ . Sin __`break`__ , el programa continúa a la siguiente expresión con etiqueta y ejecuta las instrucciones hasta una instrucción __`break`__ o hasta que se alcance el final de la instrucción. Esta continuación puede ser deseable en algunas situaciones.

La instrucción __`default`__ se ejecuta si ningún valor *`constant-expression`* __`case`__ es igual al valor de *`expression`* . Si no hay ninguna instrucción __`default`__ y no se encuentra ninguna instrucción __`case`__ coincidente, no se ejecuta ninguna de las instrucciones del cuerpo __`switch`__ . Puede haber a lo sumo una instrucción __`default`__ . No es necesario que la instrucción __`default`__ aparezca al final. Puede aparecer en cualquier parte del cuerpo de la instrucción __`switch`__ . Una etiqueta __`case`__ o __`default`__ solo puede aparecer en una instrucción __`switch`__ .

El tipo de *`expression`* __`switch`__ y *`constant-expression`* __`case`__ debe ser entero. El valor de cada *`constant-expression`* __`case`__ debe ser único dentro del cuerpo de instrucción.

Las etiquetas __`case`__ y __`default`__ del cuerpo de instrucción __`switch`__ solo tienen sentido en la prueba inicial que determina dónde se inicia la ejecución en el cuerpo de instrucción. Las instrucciones __`switch`__ se pueden anidar. Cualquier variable estática se inicializa antes de ejecutar cualquier instrucción __`switch`__ .

> [!NOTE]
> Las declaraciones pueden aparecer en el encabezado de la instrucción compuesta que constituye el cuerpo de __`switch`__ , pero las inicializaciones incluidas en las declaraciones no se realizan. La instrucción __`switch`__ transfiere el control directamente a una instrucción ejecutable dentro del cuerpo y omite las líneas que contienen inicializaciones.

En los siguientes ejemplos se muestran instrucciones __`switch`__ :

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

En este ejemplo, las tres instrucciones del cuerpo de __`switch`__ se ejecutan si `c` es igual a `'A'`, ya que no aparece una instrucción __`break`__ antes de la siguiente instrucción __`case`__ . El control de la ejecución se transfiere a la primera instrucción (`capital_a++;`) y continúa en orden con el resto del cuerpo. Si `c` es igual a `'a'`, se incrementan `letter_a` y `total`. Solo se incrementa `total` cuando `c` no es igual a `'A'` o `'a'`.

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

En este ejemplo, una instrucción __`break`__ sigue a cada instrucción del cuerpo de __`switch`__ . La instrucción __`break`__ fuerza una salida del cuerpo de instrucción tras ejecutar una instrucción. Si `i` es igual a -1, solo se incrementa `n`. La instrucción __`break`__ que sigue a la instrucción `n++;` hace que el control de la ejecución salga del cuerpo de instrucción y omita las instrucciones restantes. De igual forma, si `i` es igual a 0, solo se incrementa `z`; si `i` es igual a 1, solo se incrementa `p`. La instrucción __`break`__ final no es estrictamente necesaria, puesto que el control sale del cuerpo al final de la instrucción compuesta. Se incluye por coherencia.

Una sola instrucción puede contener varias etiquetas __`case`__ , como se muestra en el ejemplo siguiente:

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

Microsoft C no limita el número de valores __`case`__ en una instrucción __`switch`__ . El número solo está limitado por la memoria disponible. ANSI C requiere que se permitan al menos 257 etiquetas __`case`__ en una instrucción __`switch`__ .

El valor predeterminado default para Microsoft C es que las extensiones de Microsoft estén habilitadas. Use la opción de compilador [/Za](../build/reference/za-ze-disable-language-extensions.md) para deshabilitar estas extensiones.

## <a name="see-also"></a>Vea también

[Instrucción switch (C++)](../cpp/switch-statement-cpp.md)
