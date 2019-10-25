---
title: scanf (Especificación de ancho)
ms.date: 10/22/2019
api_location:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- scanf
helpviewer_keywords:
- scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
ms.openlocfilehash: 54331f4150c50b084b59ac51b3f34ffe15c5b1c8
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811120"
---
# <a name="scanf-width-specification"></a>scanf (Especificación de ancho)

Esta información se aplica a la interpretación de cadenas de formato en la familia de funciones `scanf`, incluidas las versiones seguras, como `scanf_s`. Por lo general, estas funciones asumen que la secuencia de entrada se divide en una secuencia de tokens. Los tokens se separan mediante espacios en blanco (espacio, tabulación o nueva línea), o para los tipos numéricos, mediante el final natural de un tipo de datos numérico, tal como se indica en el primer carácter que no se puede convertir en texto numérico. Sin embargo, la especificación de ancho puede utilizarse para hacer que se detenga el análisis de la entrada antes del fin natural de un token.

La especificación del *ancho* consta de caracteres entre el `%` y el especificador de campo de tipo, que puede incluir un entero positivo denominado el campo *ancho* y uno o varios caracteres que indican el tamaño del campo, que también pueden considerarse como modificadores del tipo del campo, como una indicación de si el tipo de entero es **corto** o **largo**. Dichos caracteres se conocen como el prefijo de tamaño.

## <a name="the-width-field"></a>El campo ancho

El campo *ancho* es un entero decimal positivo que controla el número máximo de caracteres que se van a leer para ese campo. No se convierten más de caracteres de *ancho* en el `argument`correspondiente. Es posible que se lean menos caracteres de *ancho* si se produce un carácter de espacio en blanco o un carácter que no se puede convertir según el formato especificado antes de que se alcance el *ancho* .

La especificación de ancho es independiente y diferente del argumento de tamaño de búfer requerido por las versiones seguras de estas funciones (por ejemplo, `scanf_s`, `wscanf_s`, etc.). En el siguiente ejemplo, la especificación de ancho es de 20, que indica que se leerá un máximo de 20 caracteres del flujo de entrada. La longitud del búfer es de 21, que incluye espacio para los 20 posibles caracteres más el terminador nulo:

```C
char str[21];
scanf_s("%20s", str, 21);
```

Si no se usa el campo *ancho* , `scanf_s` intenta leer el token completo en la cadena. Si el tamaño especificado no es lo suficientemente grande como para contener el token completo, no se escribirá nada en la cadena de destino. Si se especifica el campo *ancho* , los primeros caracteres de *ancho* del token se escriben en la cadena de destino, junto con el terminador null.

## <a name="the-size-prefix"></a>El prefijo de tamaño

Los prefijos opcionales **h**, **HH**, **l**, **ll**, **I64**y **l** indican el tamaño del `argument` (carácter largo o corto, carácter de un solo byte o carácter ancho, según el carácter de tipo que modifiquen). Estos caracteres de  especificación de formato se utilizan con caracteres de tipo en las funciones `scanf` o `wscanf` para especificar la interpretación de los argumentos tal como se muestra en la siguiente tabla. El prefijo de tipo **I64** es una extensión de Microsoft y no es compatible con C estándar. Los caracteres de tipo y sus significados se describen en la tabla "caracteres de tipo para las funciones scanf" en los [caracteres de campo de tipo scanf](../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Los prefijos **h**, **l**y **l** son extensiones de Microsoft cuando se usan con datos de tipo **Char**.

### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>Prefijos de tamaño para especificadores de tipo de formato scanf y wscanf

|Para especificar|Usar prefijo|Con especificador de tipo|
|----------------|----------------|-------------------------|
|**double**|**l**|**e**, **E**, **f**, **g** o **G**|
|**long double** (igual que double)|**L**|**e**, **E**, **f**, **g** o **G**|
|**long int**|**l**|**d**, **i**, **o**, **x** o **X**|
|**long unsigned int**|**l**|**u**|
|**long long**|**ll**|**d**, **i**, **o**, **x** o **X**|
|**Short int**|**h**|**d**, **i**, **o**, **x** o **X**|
|**short unsigned int**|**h**|**u**|
|**char**|**hh**|**d**, **i**, **o**, **x** o **X**|
|**unsigned char**|**hh**|**u**|
|**int64**|**I64**|**d**, **i**, **o**, **u**, **x** o **X**|
|Carácter de un solo byte con `scanf`|**h**|**c** o **C**|
|Carácter de un solo byte con `wscanf`|**h**|**c** o **C**|
|Carácter ancho con `scanf`|**l**|**c** o **C**|
|Carácter ancho con `wscanf`|**l**|**c** o **C**|
|Cadena de caracteres de un solo byte con `scanf`|**h**|**s** o **S**|
|Cadena de caracteres de un solo byte con `wscanf`|**h**|**s** o **S**|
|Cadena de caracteres anchos con `scanf`|**l**|**s** o **S**|
|Cadena de caracteres anchos con `wscanf`|**l**|**s** o **S**|

Los siguientes ejemplos usan **h** y **l** con funciones `scanf_s` y `wscanf_s`:

```C
scanf_s("%ls", &x, 2);     // Read a wide-character string
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character
```

Si utiliza una función no segura de la familia `scanf`, omita el parámetro de tamaño que indica la longitud del búfer del argumento anterior.

## <a name="reading-undelimited-strings"></a>Leer cadenas no delimitadas

Para leer cadenas que no son delimitadas por caracteres de espacio en blanco, se puede sustituir un conjunto de caracteres entre corchetes ( **[ ]** ) por el carácter de tipo **s** (cadena). El conjunto de caracteres entre corchetes se conoce como una *cadena de control*. El campo de entrada correspondiente se lee hasta el primer carácter que no aparece en la cadena de control. Si el primer carácter del conjunto es un símbolo de intercalación ( **^** ), se invierte el efecto: el campo de entrada se lee hasta el primer carácter que aparece en el resto del conjunto de caracteres.

Tanto **% [a-z]** como **% [z-a]** se interpretan como equivalentes a **% [ABCDE... z]** . Es una extensión de función de `scanf` común, pero no es necesaria para el estándar de C.

## <a name="reading-unterminated-strings"></a>Leer cadenas no terminadas

Para almacenar una cadena sin almacenar un carácter nulo de terminación (' \ 0 '), use la especificación `%Nc`, donde *N* es un entero decimal. En este caso, el carácter de tipo **c** indica que el argumento es un puntero a una matriz de caracteres. Los siguientes caracteres *N* se leen desde el flujo de entrada en la ubicación especificada y no se anexa ningún carácter nulo (' \ 0 '). Si no se especifica *N* , su valor predeterminado es 1.

## <a name="when-scanf-stops-reading-a-field"></a>Si scanf deja de leer un campo

La función `scanf` examina cada campo de entrada, carácter a carácter. Puede dejar de leer un campo de entrada concreto antes de llegar a un carácter de espacio por una de varias razones:

- Se ha alcanzado el ancho especificado.

- No se puede convertir el siguiente carácter según lo especificado.

- El siguiente carácter entra en conflicto con un carácter de la cadena de control que se supone que debe coincidir.

- El siguiente carácter no aparece en un juego de caracteres determinado.

Por algún motivo, cuando la función `scanf` deja de leer un campo de entrada, se considera que el siguiente campo de entrada comienza en el primer carácter no leído. El carácter conflictivo, si existe, se considera no leído. Es el primer carácter del siguiente campo de entrada o el primer carácter de las operaciones de lectura posteriores en el flujo de entrada.

## <a name="see-also"></a>Vea también

[scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[Campos de especificación de formato: scanf y wscanf (funciones)](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)<br/>
[scanf (caracteres de campo de tipo)](../c-runtime-library/scanf-type-field-characters.md)<br/>
