---
title: "Especificación de tamaño | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr120.dll
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- size
dev_langs:
- C++
helpviewer_keywords:
- printf function, format specification fields
ms.assetid: 525dc5d8-e70a-4797-a6a0-ec504a27355c
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 9041b6c8cc2789b275bf7a62c73102812e5c9c48
ms.lasthandoff: 02/24/2017

---
# <a name="size-specification"></a>Especificación de tamaño
En una especificación de formato, el cuarto campo es un modificador de longitud del argumento del especificador de conversión. Los prefijos del campo `size` para el campo `type` (`h`, `l`, `w`, `I`, `I32`, `I64` y `ll`) especifican el “tamaño” del argumento correspondiente (largo o corto, de 32 o de 64 bits, carácter de un solo byte o carácter ancho) en función del especificador de conversión que modifican. Estos prefijos de tamaño se usan con los caracteres de `type` de los grupos de funciones `printf` y `wprintf` para especificar la interpretación de la longitud de los argumentos, como se muestra en la tabla siguiente. El campo `size` es opcional en algunos tipos de argumento. Cuando no se especifica ningún prefijo de tamaño, el formateador usa argumentos de entero, por ejemplo, con signo o sin signo `char`, `short`, `int`, `long`, y los tipos de enumeración, como tipos `int` de 32 bits. Los argumentos de punto flotante se usan como de tipos `double` de 64 bits. Esto coincide con las reglas de promoción de argumentos predeterminadas de las listas de argumentos variables. Para obtener más información acerca de la promoción de argumentos, consulte Ellipses and Default Arguments (Elipses y argumentos predeterminados) en [Postfix expressions](../cpp/postfix-expressions.md) (Expresiones Postfix). En los sistemas de 32 y 64 bits, la especificación de formato de un argumento de entero de 64 bits debe incluir un prefijo de tamaño de `ll` o `I64`. De lo contrario, el comportamiento del formateador no queda definido.  
  
 Algunos tipos tienen tamaños diferentes en código de 32 bits y de 64 bits. Por ejemplo, `size_t` es de 32 bits en el código compilado para x86 y de 64 bits en el código compilado para x64. Para crear código de formato independiente de la plataforma para los tipos de ancho variable, puede usar un modificador de longitud de argumentos de ancho variable. Como alternativa, puede usar un modificador de longitud de argumentos de 64 bits y promover explícitamente el tipo de argumentos de ancho variable a 64 bits. El modificador de longitud de argumentos `I` específico de Microsoft usa argumentos de entero de ancho variable.  
  
> [!NOTE]
>  Los prefijos de modificador de longitud `I`, `I32` y `I64` son extensiones de Microsoft y no son compatibles con ANSI. El prefijo `h`, cuando se usa con datos de tipo `char`, el prefijo `w`, cuando se usa con datos de tipo `wchar_t`, y el prefijo `l`, cuando se usa con datos de tipo `double`, son extensiones de Microsoft. Los prefijos de longitud `hh`, `j`, `z` y `t` no se admiten.  
  
### <a name="size-prefixes-for-printf-and-wprintf-format-type-specifiers"></a>Prefijos de tamaño de los especificadores de tipo de formato printf y wprintf  
  
|Para especificar|Usar prefijo|Con especificador de tipo|  
|----------------|----------------|-------------------------|  
|`long int`|`l` (L minúscula)|`d`, `i`, `o`, `x` o `X`|  
|`long unsigned int`|`l`|`o`, `u`, `x` o `X`|  
|`long long`|`ll`|`d`, `i`, `o`, `x` o `X`|  
|`short int`|`h`|`d`, `i`, `o`, `x` o `X`|  
|`short unsigned int`|`h`|`o`, `u`, `x` o `X`|  
|`__int32`|`I32`|`d`, `i`, `o`, `x` o `X`|  
|`unsigned __int32`|`I32`|`o`, `u`, `x` o `X`|  
|`__int64`|`I64`|`d`, `i`, `o`, `x` o `X`|  
|`unsigned __int64`|`I64`|`o`, `u`, `x` o `X`|  
|`ptrdiff_t` (es decir, `__int32` en plataformas de 32 bits, `__int64` en plataformas de 64 bits)|`I`|`d`, `i`, `o`, `x` o `X`|  
|`size_t` (es decir, `unsigned __int32` en plataformas de 32 bits, `unsigned __int64` en plataformas de 64 bits)|`I`|`o`, `u`, `x` o `X`|  
|`long double` (en [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)], aunque `long double` es un tipo distinto, tiene la misma representación interna que `double`.)|`l` o `L`|`a`, `A`, `e`, `E`, `f`, `g` o `G`|  
|Carácter de un solo byte con las funciones `printf` y `wprintf`. (Un especificador de tipo `hc` o `hC` es sinónimo de `c` en las funciones `printf` y de `C` en las funciones `wprintf`).|`h`|`c` o `C`|  
|Carácter ancho con las funciones `printf` y `wprintf`. (Un especificador de tipo `lc`, `lC`, `wc` o `wC` es sinónimo de `C` en las funciones `printf` y de `c` en las funciones `wprintf`.)|`l` o `w`|`c` o `C`|  
|Cadena de caracteres de un solo byte con las funciones `printf` y `wprintf`. (Un especificador de tipo `hs` o `hS` es sinónimo de `s` en las funciones `printf` y de `S` en las funciones `wprintf`).|`h`|`s`, `S` o `Z`|  
|Cadena de caracteres anchos con las funciones `printf` y `wprintf`. (Un especificador de tipo `ls`, `lS`, `ws` o `wS` es sinónimo de `S` en las funciones `printf` y de `s` en las funciones `wprintf`.)|`l` o `w`|`s`, `S` o `Z`|  
  
## <a name="see-also"></a>Vea también  
 [printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [Sintaxis de especificación de formato: printf y wprintf (Funciones)](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [Directivas de marca](../c-runtime-library/flag-directives.md)   
 [printf (Especificación de ancho)](../c-runtime-library/printf-width-specification.md)   
 [Especificación de precisión](../c-runtime-library/precision-specification.md)   
 [printf (Caracteres de campo de tipo)](../c-runtime-library/printf-type-field-characters.md)
