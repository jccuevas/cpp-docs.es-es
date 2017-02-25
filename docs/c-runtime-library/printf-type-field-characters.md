---
title: "printf (Caracteres de campo de tipo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "printf (función), especificación de formato (campos)"
  - "printf (función), caracteres de campo de tipo"
ms.assetid: 699cb438-cd14-402e-9f81-c7a32acc3317
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# printf (Caracteres de campo de tipo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En una especificación de formato, el carácter de `type` es un especificador de conversión que especifica si el argumento correspondiente debe interpretarse como un carácter, una cadena, un puntero, un entero o un número de punto flotante.  El carácter de `type` es el único campo necesario en la especificación de formato y aparece después de los campos opcionales.  
  
 Los argumentos que siguen a la cadena de formato se interpretan según el carácter de `type` correspondiente y el prefijo opcional [size](../c-runtime-library/size-specification.md).  Las conversiones de tipos de caracteres `char` y `wchar_t` se especifican mediante `c` o `C`, y las cadenas de caracteres de byte único y multibyte o de carácter ancho se especifican mediante `s` o `S`, según la función de formato que se esté usando.  Los argumentos de caracteres y cadenas que se especifican mediante el uso de `c` y `s` se interpretan como `char` y `char*` en la familia de funciones `printf` o como `wchar_t` y `wchar_t*` en la familia de funciones `wprintf`.  Los argumentos de caracteres y cadenas que se especifican mediante el uso de `C` y `S` se interpretan como `wchar_t` y `wchar_t*` en la familia de funciones `printf` o como `char` y `char*` en la familia de funciones `wprintf`.  
  
 Los tipos de enteros como `short`, `int`, `long`, `long long` y sus variantes `unsigned` se especifican mediante `d`, `i`, `o`, `u`, `x` y `X`.  Los tipos de punto flotante tipos como `float`, `double` y `long double`, se especifican mediante `a`, `A`, `e`, `E`, `f`, `g` y `G`.  De forma predeterminada, y a menos que los modifique un prefijo de longitud de campo `size`, los argumentos de entero se convierten en el tipo `int` y los argumentos de punto flotante se convierten en `double`.  En sistemas de 64 bits, un `int` es un valor de 32 bits; por consiguiente, los enteros de 64 bits se truncan cuando se les aplica formato para la salida, a menos que se use un prefijo `size` de `ll` o `I64`.  Los tipos de puntero que se especifican mediante `p` usan la longitud predeterminada de la plataforma.  
  
> [!NOTE]
>  Los caracteres de tipo `C`, `S` y `Z`, así como el comportamiento de los caracteres de tipo `c` y `s` cuando se usan con las funciones `printf` y `wprintf`, son extensiones de Microsoft y no son compatibles con ANSI.  [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] no admite el carácter de tipo `F`.  
  
### printf \(Caracteres de campo de tipo\)  
  
|Carácter de tipo|Argumento|Formato de salida|  
|----------------------|---------------|-----------------------|  
|`c`|Carácter|Cuando se usa con funciones `printf`, especifica un carácter de byte único; cuando se usa con funciones `wprintf`, especifica un carácter ancho.|  
|`C`|Carácter|Cuando se usa con funciones `printf`, especifica un carácter ancho; cuando se usa con funciones `wprintf`, especifica un carácter de byte único.|  
|`d`|Entero|Entero decimal con signo.|  
|`i`|Entero|Entero decimal con signo.|  
|`o`|Entero|Entero octal sin signo.|  
|`u`|Entero|Entero decimal sin signo.|  
|`x`|Entero|Entero hexadecimal sin signo; usa “abcdef”.|  
|`X`|Entero|Entero hexadecimal sin signo; usa “ABCDEF”.|  
|`e`|Punto flotante|Valor con signo que tiene el formato \[ – \]`d`**.**`dddd` e \[*signo*\]`dd[d]` donde `d` es un dígito decimal, `dddd` es uno o varios dígitos decimales, `dd[d]` es dos o tres dígitos decimales en función del [formato de salida](../c-runtime-library/set-output-format.md) y el tamaño del exponente, y *signo* es \+ o –.|  
|`E`|Punto flotante|Es idéntico al formato de `e` salvo que el exponente se introduce mediante **E** en lugar de **e**.|  
|`f`|Punto flotante|Valor con signo que tiene el formato \[ – \]`dddd`**.**`dddd`, donde `dddd` es uno o varios dígitos decimales.  El número de dígitos que hay delante del separador decimal depende de la magnitud del número y el número de dígitos que hay detrás del separador decimal depende de la precisión solicitada.|  
|`g`|Punto flotante|Los valores con signo se muestran en formato `f` o `e`, lo que sea más conciso para el valor y la precisión especificados.  El formato `e` solo se usa cuando el exponente del valor es menor que –4 o mayor o igual que el argumento `precision`.  Los ceros a la derecha se truncan y el separador decimal tan solo aparece si va seguido de uno o más dígitos.|  
|`G`|Punto flotante|Es idéntico al formato de `g`, salvo que el exponente se introduce mediante **E** en lugar de **e** \(cuando corresponda\).|  
|`a`|Punto flotante|Valor con signo hexadecimal de punto flotante y precisión doble que tiene el formato \[−\]0x*h.hhhh* **p±**`dd`, donde *h.hhhh* son los dígitos hexadecimales \(con letras minúsculas\) de la mantisa y `dd` es uno o más dígitos del exponente.  La precisión especifica el número de dígitos que se muestran después del punto.|  
|`A`|Punto flotante|Valor con signo hexadecimal de punto flotante y precisión doble que tiene el formato \[−\]0X*h.hhhh* **P±**`dd`, donde *h.hhhh* son los dígitos hexadecimales \(con letras mayúsculas\) de la mantisa y `dd` es uno o más dígitos del exponente.  La precisión especifica el número de dígitos que se muestran después del punto.|  
|`n`|Puntero para entero|Número de caracteres que se han escrito correctamente en el flujo o búfer.  Este valor se almacena en el entero cuya dirección se indica como argumento.  Vea la nota sobre seguridad más adelante en este artículo.|  
|`p`|Tipo de puntero|Muestra el argumento como una dirección de dígitos hexadecimales.|  
|`s`|Cadena|Cuando se usa con funciones `printf`, especifica una cadena de caracteres de byte único o multibyte; cuando se usa con funciones `wprintf`, especifica una cadena de carácter ancho.  Los caracteres se muestran hasta el primer carácter nulo o hasta que se alcanza el valor de `precision`.|  
|`S`|Cadena|Cuando se usa con funciones `printf`, especifica una cadena de carácter ancho; cuando se usa con funciones `wprintf`, especifica una cadena de caracteres de byte único o multibyte.  Los caracteres se muestran hasta el primer carácter nulo o hasta que se alcanza el valor de `precision`.|  
|`Z`|Estructura `ANSI_STRING` o `UNICODE_STRING`|Cuando la dirección de una estructura [ANSI\_STRING](http://msdn.microsoft.com/library/windows/hardware/ff540605.aspx) o [UNICODE\_STRING](http://msdn.microsoft.com/library/windows/hardware/ff564879.aspx) se pasa como argumento, muestra la cadena incluida en el búfer al que apunta el campo `Buffer` de la estructura.  Use un prefijo de modificador de longitud de `w` para especificar un argumento `UNICODE_STRING`, por ejemplo, `%wZ`.  El campo `Length` de la estructura debe establecerse en la longitud de la cadena expresada en bytes.  El campo `MaximumLength` de la estructura debe establecerse en la longitud del búfer expresada en bytes.<br /><br /> Normalmente, el carácter de tipo `Z` tan solo se usa en funciones de depuración de controladores que utilizan una especificación de formato, como `dbgPrint` y `kdPrint`.|  
  
 Si el argumento correspondiente a un especificador de conversión de punto flotante es infinito, indefinido o NAN, en la tabla siguiente muestra la salida con formato.  
  
|Valor|Resultado|  
|-----------|---------------|  
|\+ infinito|`1.#INF` *dígitos aleatorios*|  
|– infinito|`–1.#INF` *dígitos aleatorios*|  
|Indefinido \(igual que un valor NaN simple\)|*dígito* `.#IND` *dígitos aleatorios*|  
|NAN|*dígito* `.#NAN` *dígitos aleatorios*|  
  
> [!NOTE]
>  Si el campo de `Buffer` del argumento correspondiente a `%Z` o del argumento correspondiente a `%s` o `%S`, es un puntero nulo, se mostrará "\(null\)".  
  
> [!NOTE]
>  En todos los formatos exponenciales, tres es el número predeterminado de dígitos del exponente que debe mostrarse.  La función [\_set\_output\_format](../c-runtime-library/set-output-format.md) permite establecer en dos el número de dígitos que se muestran, pero este valor debe ampliarse a tres si así lo exige el tamaño del exponente.  
  
> [!IMPORTANT]
>  Dado que el formato `%n` es intrínsecamente inseguro, se deshabilita de forma predeterminada.  Si `%n` aparece en una cadena de formato, se invoca el controlador de parámetros no válidos, tal como se describe en [Validación de parámetros](../c-runtime-library/parameter-validation.md).  Para habilitar la compatibilidad con `%n`, vea [\_set\_printf\_count\_output](../c-runtime-library/reference/set-printf-count-output.md).  
  
## Vea también  
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [Sintaxis de especificación de formato: Funciones printf y wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [Directivas de marca](../c-runtime-library/flag-directives.md)   
 [printf \(Especificación de ancho\)](../c-runtime-library/printf-width-specification.md)   
 [Especificación de precisión](../c-runtime-library/precision-specification.md)   
 [Especificación de tamaño](../c-runtime-library/size-specification.md)   
 [\_set\_output\_format](../c-runtime-library/set-output-format.md)