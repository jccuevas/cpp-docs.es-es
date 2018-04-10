---
title: 'Sintaxis de especificación de formato: funciones printf y wprintf | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- format specification fields for printf function
- printf function format specification fields
- flag directives, printf function
- type fields, printf function
- width fields, printf function
- precision fields, printf function
ms.assetid: 664b1717-2760-4c61-bd9c-22eee618d825
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 437657857b87f2f7df140576d09467d6276549f6
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2018
---
# <a name="format-specification-syntax-printf-and-wprintf-functions"></a>Sintaxis de especificación de formato: funciones printf y wprintf

Las distintas funciones `printf` y `wprintf` toman una cadena de formato y argumentos opcionales y generan una secuencia de caracteres con formato para la salida. La cadena de formato contiene cero o más *directivas*, que son caracteres literales para la salida o *especificaciones de conversión* codificadas que describen cómo dar formato a un argumento en la salida. En este tema se describe la sintaxis utilizada para codificar las especificaciones de conversión en la cadena de formato. Para obtener una lista de estas funciones, vea [E/S de secuencia](../c-runtime-library/stream-i-o.md).

Una especificación de conversión consta de campos opcionales y obligatorios con este formato:

**%**[[*marcas*](#flags)][[*ancho*](#width)][.[*precisión*](#precision)][[*tamaño*](#size)][*tipo*](#type)

Cada campo de la especificación de conversión es un carácter o un número que indica una opción de formato o un especificador de conversión. El campo obligatorio *tipo* especifica el tipo de conversión que se aplicará a un argumento. Los campos opcionales *marcas*, *ancho* y *precisión* controlan aspectos de formato adicionales, como espacios o ceros iniciales, justificación y precisión mostrada. El campo *tamaño* especifica el tamaño del argumento consumido y convertido.

La especificación de conversión básica solo contiene el signo de porcentaje y un carácter para *tipo*. Por ejemplo, `%s` especifica una conversión de cadena. Para imprimir un carácter de signo de porcentaje, use `%%`. Si un signo de porcentaje va seguido de un carácter que no tiene ningún significado como campo de formato, se invoca el controlador de parámetros no válidos. Para más información, consulte [Validación de parámetros](../c-runtime-library/parameter-validation.md).

> [!IMPORTANT]
> Por motivos de seguridad y estabilidad, asegúrese de que las cadenas de especificación de conversión no están definidas por el usuario. Por ejemplo, imagine un programa que solicita al usuario que escriba un nombre y almacena la entrada en una variable de cadena denominada `user_name`. Para imprimir `user_name`, no haga esto:
>
> `printf( user_name ); /* Danger!  If user_name contains "%s", program will crash */`
>
> En lugar de ello, haga esto:
>
> `printf( "%s", user_name );`

<a name="type"></a>

## <a name="type-conversion-specifier"></a>Especificador de conversión de tipo

El carácter del especificador de conversión *tipo* especifica si el argumento correspondiente debe interpretarse como un carácter, una cadena, un puntero, un entero o un número de punto flotante. El carácter de *tipo* es el único campo de especificación de conversión necesario y aparece después de los campos opcionales.

Los argumentos que siguen a la cadena de formato se interpretan según el carácter de *tipo* correspondiente y el prefijo opcional [tamaño](#size). Las conversiones de tipos de caracteres `char` y `wchar_t` se especifican mediante **c** o **C**, y las cadenas de caracteres de byte único y multibyte o de carácter ancho se especifican mediante **s** o **S**, según la función de formato que se esté usando. Los argumentos de caracteres y cadenas que se especifican mediante el uso de **c** y **s** se interpretan como `char` y `char*` en la familia de funciones `printf`, o como `wchar_t` y `wchar_t*` en la familia de funciones `wprintf`. Los argumentos de caracteres y cadenas que se especifican mediante el uso de **C** y **S** se interpretan como `wchar_t` y `wchar_t*` en la familia de funciones `printf`, o como `char` y `char*` en la familia de funciones `wprintf`. Este comportamiento es específico de Microsoft.

Los tipos de enteros como `short`, `int`, `long`, `long long` y sus variantes `unsigned` se especifican mediante **d**, **i**, **o**, **u**, **x** y **X**. Los tipos de punto flotante como `float`, `double` y `long double`, se especifican mediante **a**, **A**, **e**, **E**, **f**, **F**, **g** y **G**. De forma predeterminada, y a menos que los modifique un prefijo de *tamaño*, los argumentos de entero se convierten en el tipo `int` y los argumentos de punto flotante se convierten en `double`. En sistemas de 64 bits, `int` es un valor de 32 bits; por consiguiente, los enteros de 64 bits se truncan cuando se les aplica formato para la salida, a menos que se use un prefijo para *tamaño* de **ll** o **I64**. Los tipos de puntero que se especifican mediante **p** usan el tamaño de puntero predeterminado para la plataforma.

> [!NOTE]
> **Específicos de Microsoft**  
> El carácter de tipo **Z**, así como el comportamiento de los caracteres de tipo **c**, **C**, **s** y  **S** cuando se usan con las funciones `printf` y `wprintf`, son extensiones de Microsoft. El estándar ISO C usa **c** y **s** sistemáticamente para caracteres estrechos y cadenas, y **C** y **S** para caracteres anchos y cadenas, en todas las funciones de formato.

### <a name="type-field-characters"></a>Caracteres del campo de tipo

|Carácter de tipo|Argumento|Formato de salida|
|--------------------|--------------|-------------------|
|**c**|Carácter|Cuando se usa con funciones `printf`, especifica un carácter de byte único; cuando se usa con funciones `wprintf`, especifica un carácter ancho.|
|**C**|Carácter|Cuando se usa con funciones `printf`, especifica un carácter ancho; cuando se usa con funciones `wprintf`, especifica un carácter de byte único.|
|**d**|Integer|Entero decimal con signo.|
|**i**|Integer|Entero decimal con signo.|
|**o**|Integer|Entero octal sin signo.|
|**u**|Integer|Entero decimal sin signo.|
|**x**|Integer|Entero hexadecimal sin signo; usa “abcdef”.|
|**X**|Integer|Entero hexadecimal sin signo; usa “ABCDEF”.|
|**e**|Punto flotante|Valor con signo que tiene el formato [-]*d.dddd*__e±__*dd*[*d*], donde *d* es un dígito decimal, *dddd* es uno o varios dígitos decimales en función de la precisión especificada, o seis de manera predeterminada, y *dd*[*d*] son dos o tres dígitos decimales en función del [formato de salida](../c-runtime-library/set-output-format.md) y el tamaño del exponente.|
|**E**|Punto flotante|Es idéntico al formato de **e** salvo que el exponente se introduce mediante **E** en lugar de **e**.|
|**f**|Punto flotante|Valor con signo que tiene el formato [-]*dddd*__.__*dddd*, donde *dddd* es uno o varios dígitos decimales. El número de dígitos que hay delante del separador decimal depende de la magnitud del número y el número de dígitos que hay detrás del separador decimal depende de la precisión solicitada, seis de forma predeterminada.|
|**F**|Punto flotante|Idéntico al formato **f** salvo que la salida infinito y nan se ponen en mayúsculas.|
|**g**|Punto flotante|Los valores con signo se muestran en formato **f** o **e**, lo que sea más conciso para el valor y la precisión especificados. El formato **e** solo se usa cuando el exponente del valor es menor que -4 o mayor o igual que el argumento *precision*. Los ceros a la derecha se truncan y el separador decimal tan solo aparece si va seguido de uno o más dígitos.|
|**G**|Punto flotante|Es idéntico al formato de **g**, salvo que el exponente se introduce mediante **E** en lugar de **e** (cuando corresponda).|
|**a**|Punto flotante|Valor de punto flotante de precisión doble hexadecimal con signo que tiene el formato [-]0x*h.hhhh*__p±__*dd*, donde *h.hhhh* corresponde a los dígitos hexadecimales (con letras minúsculas) de la mantisa y *dd* corresponde al exponente, con uno o varios dígitos. La precisión especifica el número de dígitos que se muestran después del punto.|
|**A**|Punto flotante|Valor de punto flotante de precisión doble hexadecimal con signo que tiene el formato [-]0X*h.hhhh*__P±__*dd*, donde *h.hhhh* corresponde a los dígitos hexadecimales (con letras mayúsculas) de la mantisa y *dd* corresponde al exponente, con uno o varios dígitos. La precisión especifica el número de dígitos que se muestran después del punto.|
|**n**|Puntero para entero|Número de caracteres que se han escrito correctamente en el flujo o búfer. Este valor se almacena en el entero cuya dirección se indica como argumento. El tamaño del entero apuntado se puede controlar mediante un prefijo de especificación del tamaño de argumento. El especificador **n** está deshabilitado de forma predeterminada; para información, consulte la nota de seguridad importante.|
|**p**|Tipo de puntero|Muestra el argumento como una dirección de dígitos hexadecimales.|
|**s**|String|Cuando se usa con funciones `printf`, especifica una cadena de caracteres de byte único o multibyte; cuando se usa con funciones `wprintf`, especifica una cadena de carácter ancho. Los caracteres se muestran hasta el primer carácter nulo o hasta que se alcanza el valor de *precisión*.|
|**S**|String|Cuando se usa con funciones `printf`, especifica una cadena de carácter ancho; cuando se usa con funciones `wprintf`, especifica una cadena de caracteres de byte único o multibyte. Los caracteres se muestran hasta el primer carácter nulo o hasta que se alcanza el valor de *precisión*.|
|**Z**|Estructura `ANSI_STRING` o `UNICODE_STRING`|Cuando la dirección de una estructura [ANSI_STRING](http://msdn.microsoft.com/library/windows/hardware/ff540605.aspx) o [UNICODE_STRING](http://msdn.microsoft.com/library/windows/hardware/ff564879.aspx) se pasa como argumento, muestra la cadena contenida en el búfer al que apunta el campo `Buffer` de la estructura. Use un prefijo del modificador *tamaño* de **w** para especificar un argumento `UNICODE_STRING`, por ejemplo, `%wZ`. El campo `Length` de la estructura debe establecerse en la longitud de la cadena expresada en bytes. El campo `MaximumLength` de la estructura debe establecerse en la longitud del búfer expresada en bytes.<br /><br /> Normalmente, el carácter de tipo **Z** tan solo se usa en funciones de depuración de controladores que utilizan una especificación de formato, como `dbgPrint` y `kdPrint`.|

A partir de Visual Studio 2015, si el argumento correspondiente a un especificador de conversión de punto flotante (**a**, **A**, **e**, **E**, **f**, **F**, **g**, **G**) es infinito, indefinido o NaN, la salida con formato se ajusta al estándar C99. Esta tabla enumera la salida con formato:

|Valor|Salida|
|-----------|------------|
|infinity|`inf`|
|NaN reservado|`nan`|
|NaN de señalización|`nan(snan)`|
|NaN indefinido|`nan(ind)`|

Cualquiera de estos valores puede ir precedido por un signo. Si un carácter especificador de conversión de *tipo* de punto flotante es una letra mayúscula, la salida también adquiere el formato de letras mayúsculas. Por ejemplo, si el especificador de formato es `%F` en lugar de `%f`, se da formato a un infinito como `INF` en lugar de `inf`. Las funciones `scanf` también pueden analizar estas cadenas, por lo que estos valores pueden realizar una acción de ida y vuelta a través de funciones `printf` y `scanf`.

Antes de Visual Studio 2015, CRT utilizaba un formato diferente no estándar para la salida de los valores infinito, indefinido y NaN:

|Valor|Salida|
|-----------|------------|
|+ infinito|`1.#INF` *dígitos aleatorios*|
|- infinity|`-1.#INF` *dígitos aleatorios*|
|Indefinido (igual que un valor NaN simple)|*dígitos* `.#IND` *dígitos aleatorios*|
|NaN|*dígitos* `.#NAN` *dígitos aleatorios*|

Cualquiera de estas cadenas podía ir precedida de un signo y tener un formato ligeramente diferente según el ancho de campo y la precisión, a veces con efectos inusuales. Por ejemplo, `printf("%.2f\n", INFINITY)` imprimía `1.#J` porque #INF se “redondearía” a una precisión de 2 dígitos.

> [!NOTE]
> Si el argumento correspondiente a `%s` o `%S`, o el campo `Buffer` del argumento que corresponde a `%Z`, es un puntero nulo, se mostrará "(null)".

> [!NOTE]
> En todos los formatos exponenciales, dos es el número mínimo de dígitos del exponente que debe mostrarse y solo se deben usar tres si es necesario. Mediante el uso de la función [_set_output_format](../c-runtime-library/set-output-format.md), puede establecer el número de dígitos para mostrar en tres para mantener la compatibilidad con el código escrito para Visual Studio 2013 y versiones anteriores.

> [!IMPORTANT]
> Dado que el formato `%n` es intrínsecamente inseguro, se deshabilita de forma predeterminada. Si `%n` aparece en una cadena de formato, se invoca el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../c-runtime-library/parameter-validation.md). Para habilitar la compatibilidad con `%n`, vea [_set_printf_count_output](../c-runtime-library/reference/set-printf-count-output.md).

<a name="flags"></a>

## <a name="flag-directives"></a>Directivas de marca

El primer campo opcional en una especificación de conversión contiene *directivas de marca*, cero o más caracteres de marca que especifican la justificación de salida y la salida de control de signos, espacios en blanco, ceros iniciales, puntos decimales y prefijos octales y hexadecimales. Puede aparecer más de una directiva de marca en una especificación de conversión y los caracteres de marca pueden aparecer en cualquier orden.

### <a name="flag-characters"></a>Caracteres de marca

|Marcar|Significado|Default|
|----------|-------------|-------------|
|**-**|Alinear a la izquierda el resultado dentro del ancho de campo dado.|Alinear a la derecha.|
|**+**|Usar un signo (+ o -) como prefijo del valor de salida si es de un tipo con signo.|El signo solo aparece para valores con signo negativo (-).|
|**0**|Si *ancho* tiene el prefijo **0**, se agregan ceros iniciales hasta que se alcanza el ancho mínimo. Si aparecen tanto **0** como **-**, **0** se omite. Si **0** se especifica para un formato de entero (**i**, **u**, **x**, **X**, **o**, **d**) y también existe una especificación de precisión (por ejemplo, `%04.d`), **0** se omite. Si **0** se especifica para la el formato de punto flotante **a** o **A**, se anteponen ceros iniciales a la mantisa, después de `0x` o el prefijo `0X`.|Ningún relleno.|
|**blank** (' ')|Utilice un espacio en blanco como prefijo del valor de salida si tiene signo y es positivo. El espacio en blanco se omite si aparecen las marcas blank y +.|No aparecen espacios en blanco.|
|**#**|Cuando se usa con el formato **o**, **x** o **X**, la marca **#** utiliza 0, 0x o 0X, respectivamente, para utilizar como prefijo cualquier valor de salida distinto de cero.|No aparecen espacios en blanco.|
||Cuando se usa con el formato **e**, **E**, **f**, **F**, **a** o **A**, la marca **#** exige al valor de salida que contenga un punto decimal.|El punto decimal solo aparece si hay dígitos detrás.|
||Cuando se usa con el formato **g** o **G**, la marca **#** exige al valor de salida que contenga un punto decimal y evita el truncamiento de los ceros finales.<br /><br /> Se omite cuando se usa con **c**, **d**, **i**, **u** o **s**.|El punto decimal solo aparece si hay dígitos detrás. Los ceros finales se truncan.|

<a name="width"></a>

## <a name="width-specification"></a>Especificación del ancho

En una especificación de conversión, el campo de especificación de ancho opcional aparece después de cualquier carácter de *marcas* . El argumento *ancho* es un entero decimal no negativo que controla el número mínimo de caracteres que aparecerán en la salida. Si el número de caracteres en el valor de salida es menor que el ancho especificado, se agregan espacios en blanco a la izquierda o a la derecha de los valores, dependiendo de si se especifica la marca de alineación a la izquierda (**-**), hasta que se alcanza el ancho mínimo. Si *ancho* tiene como prefijo 0, se agregan ceros iniciales a las conversiones de entero y punto flotante hasta que se alcanza el ancho mínimo, excepto cuando la conversión sea a un infinito o NaN.

La especificación de ancho nunca provoca el truncamiento de un valor. Si el número de caracteres del valor de salida es mayor que el ancho especificado, o si el argumento *ancho* no se proporciona, todos los caracteres del valor aparecen en la salida, sujeto a la especificación del argumento *precisión*.

Si la especificación de ancho es un asterisco (`*`), un argumento `int` de la lista de argumentos proporciona el valor. El argumento *ancho* debe preceder al valor al que se asigna formato en la lista de argumentos, tal y como se muestra en este ejemplo:

`printf("%0*f", 5, 3);  /* 00003 is output */`

Una valor de *ancho* ausente o pequeño en una especificación de conversión no provoca el truncamiento de un valor de salida. Si el resultado de una conversión es más ancho que el valor de *ancho*, el campo se expande para incluir el resultado de la conversión.

<a name="precision"></a>

## <a name="precision-specification"></a>Especificación de la precisión

En una especificación de conversión, el tercer campo opcional es la especificación de precisión. Consta de un separador (,) seguido de un entero decimal no negativo que, según el tipo de conversión, especifica el número de caracteres de cadena, el número de posiciones decimales o el número de dígitos significativos que se van a generar.

A diferencia de la especificación de ancho, la especificación de precisión puede provocar el truncamiento del valor de salida o el redondeo del valor de punto flotante. Si *precisión* se especifica como 0 y el valor que se va a convertir es 0, el resultado no es ninguna salida de caracteres, tal y como se muestra en este ejemplo:

`printf( "%.0d", 0 );      /* No characters output */`

Si la especificación de la precisión es un asterisco (\*), un argumento `int` de la lista de argumentos proporciona el valor. En la lista de argumentos, el argumento *precisión* debe preceder al valor al que se asigna formato, tal y como se muestra en este ejemplo:

`printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`

El carácter de *tipo* determina la interpretación de *precisión* o la precisión predeterminada cuando *precisión* se omite, tal y como se muestra en la tabla siguiente.

### <a name="how-precision-values-affect-type"></a>Cómo afectan los valores de precisión al tipo

|Tipo|Significado|Default|
|----------|-------------|-------------|
|**a**, **A**|La precisión especifica el número de dígitos que se muestran después del punto.|La precisión predeterminada es 13. Si la precisión es 0, no se imprime ningún punto decimal a menos que se use la marca **#**.|
|**c**, **C**|La precisión no tiene ningún efecto.|El carácter se imprime.|
|**d**, **i**, **o**, **u**, **x**, **X**|La precisión especifica el número mínimo de dígitos que se imprimen. Si el número de dígitos del argumento es menor que *precisión*, el valor de salida se rellena con ceros a la izquierda. El valor no se trunca cuando el número de dígitos supera al argumento *precisión*.|La precisión predeterminada es 1.|
|**e**, **E**|La precisión especifica el número de dígitos que se almacenarán después del separador decimal. El último dígito impreso se redondea.|La precisión predeterminada es 6. Si *precisión* es 0 o no aparece un número detrás del punto (.), el punto decimal no se imprime.|
|**f**, **F**|El valor de precisión especifica el número de dígitos que siguen al separador decimal. Si aparece un separador decimal, aparece al menos un dígito antes. El valor se redondea al número adecuado de dígitos.|La precisión predeterminada es 6. Si *precisión* es 0 o si no aparece un número detrás del punto (.), el punto decimal no se imprime.|
|**g**, **G**|La precisión especifica el número máximo de dígitos significativos que se imprimen.|Se imprimen seis dígitos significativos y se truncan los ceros finales.|
|**s**, **S**|La precisión especifica el número máximo de caracteres que se imprimen. Los caracteres que rebasen el valor de *precisión* no se imprimen.|Los caracteres se imprimen hasta que se encuentra un carácter nulo.|

<a name="size"></a>

## <a name="argument-size-specification"></a>Especificación del tamaño del argumento

En una especificación de conversión, el campo *tamaño* es un modificador de longitud del argumento del especificador de conversión *tipo*. Los prefijos del campo *tamaño* para el campo *tipo*, que pueden ser **hh**, **h**, **j**, **l** (L minúscula), **L**, **ll**, **t**, **w**, **z**, **I** (i mayúscula), **I32** e **I64**, especifican el "tamaño" del argumento correspondiente (largo o corto, de 32 o de 64 bits, carácter de un solo byte o carácter ancho) en función del especificador de conversión que modifican. Estos prefijos de tamaño se usan con los caracteres de *tipo* de los grupos de funciones `printf` y `wprintf` para especificar la interpretación del tamaño de los argumentos, como se muestra en la tabla siguiente. El campo *tamaño* es opcional en algunos tipos de argumento. Cuando no se especifica ningún prefijo de tamaño, el formateador consume argumentos de entero (por ejemplo, `char`, `short`, `int` y `long` con signo o sin signo, y tipos de enumeración) como tipos `int` de 32 bits y los argumentos de punto flotante `float`, `double` y `long double` se consumen como tipos `double` de 64 bits. Esto coincide con las reglas de promoción de argumentos predeterminadas de las listas de argumentos variables. Para obtener más información acerca de la promoción de argumentos, consulte Ellipses and Default Arguments (Elipses y argumentos predeterminados) en [Postfix expressions](../cpp/postfix-expressions.md) (Expresiones Postfix). En los sistemas de 32 y 64 bits, la especificación de conversión de un argumento de entero de 64 bits debe incluir un prefijo de tamaño de **ll** o **I64**. De lo contrario, el comportamiento del formateador no queda definido.

Algunos tipos tienen tamaños diferentes en código de 32 bits y de 64 bits. Por ejemplo, `size_t` es de 32 bits en el código compilado para x86 y de 64 bits en el código compilado para x64. Para crear código de formato independiente de la plataforma para los tipos de ancho variable, puede usar un modificador de tamaño de argumentos de ancho variable. Como alternativa, puede usar un modificador de tamaño de argumentos de 64 bits y promover explícitamente el tipo de argumentos de ancho variable a 64 bits. El modificador de tamaño de argumentos **I** (i mayúscula) específico de Microsoft controla los argumentos de entero de ancho variable, pero se recomiendan los modificadores **j**, **t** y **z** específicos del tipo para la portabilidad.

### <a name="size-prefixes-for-printf-and-wprintf-format-type-specifiers"></a>Prefijos de tamaño de los especificadores de tipo de formato printf y wprintf

|Para especificar|Usar prefijo|Con especificador de tipo|
|----------------|----------------|-------------------------|
|`char`<br />`unsigned char`|**hh**|**d**, **i**, **o**, **u**, **x** o **X**|
|`short int`<br />`short unsigned int`|**h**|**d**, **i**, **o**, **u**, **x** o **X**|
|`__int32`<br />`unsigned __int32`|**I32**|**d**, **i**, **o**, **u**, **x** o **X**|
|`__int64`<br />`unsigned __int64`|**I64**|**d**, **i**, **o**, **u**, **x** o **X**|
|`intmax_t`<br />`uintmax_t`|**j** o **I64**|**d**, **i**, **o**, **u**, **x** o **X**|
|`long double`|**l** (L minúscula) o **L**|**a**, **A**, **e**, **E**, **f**, **F**, **g** o **G**|
|`long int`<br />`long unsigned int`|**l** (L minúscula)|**d**, **i**, **o**, **u**, **x** o **X**|
|`long long int`<br />`unsigned long long int`|**ll**  (LL minúscula)|**d**, **i**, **o**, **u**, **x** o **X**|
|`ptrdiff_t`|**t** o **I** (i mayúscula)|**d**, **i**, **o**, **u**, **x** o **X**|
|`size_t`|**z** o **I** (i mayúscula)|**d**, **i**, **o**, **u**, **x** o **X**|
|Carácter de un solo byte|**h**|**c** o **C**|
|Carácter ancho|**l** (L minúscula) o **w**|**c** o **C**|
|Cadena de caracteres de un solo byte|**h**|**s**, **S** o **Z**|
|Cadena de caracteres anchos|**l** (L minúscula) o **w**|**s**, **S** o **Z**|

Los tipos `ptrdiff_t` y `size_t` son `__int32` o `unsigned __int32` en plataformas de 32 bits, y `__int64` o `unsigned __int64` en plataformas de 64 bits. Los prefijos de tamaño **I** (i mayúscula), **j**, **t** y **z** toman el ancho de argumento correcto para la plataforma.

En Visual C++, aunque `long double` es un tipo bien diferenciado, tiene la misma representación interna que `double`.

Un especificador de tipo **hc** o **hC** es sinónimo de **c** en las funciones `printf` y de **C** en las funciones `wprintf`. Un especificador de tipo **lc**, **lC**, **wc** or **wC** es sinónimo de **C** en las funciones `printf` y de **c** en las funciones `wprintf`. Un especificador de tipo **hs** o **hS** es sinónimo de **s** en las funciones `printf` y de **S** en las funciones `wprintf`. Un especificador de tipo **ls**, **lS**, **ws** o **wS** es sinónimo de **S** en las funciones `printf` y de **s** en las funciones `wprintf`.

> [!NOTE]
> **Específicos de Microsoft**  
> Los prefijos del modificador de tamaño de argumento **I** (i mayúsculas), **I32**, **I64** y **w** son extensiones de Microsoft y no son compatibles con ISO C. El prefijo **h**, cuando se usa con datos de tipo `char`, y el prefijo **l** (l minúscula), cuando se usa con datos de tipo `double`, son extensiones de Microsoft.

## <a name="see-also"></a>Vea también

[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)  
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)  
[printf_p (parámetros de posición)](../c-runtime-library/printf-p-positional-parameters.md)  