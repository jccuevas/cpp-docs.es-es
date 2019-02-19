---
title: Comentarios en C
ms.date: 06/25/2018
helpviewer_keywords:
- code comments, C code
- comments, documenting code
- comments, C code
- /* */ comment delimiters
- comments
ms.assetid: 0f5f2825-e673-49e7-8669-94e2f5294989
ms.openlocfilehash: fd2c08855bcc3ef3b4068f3841ce177d8162ff5b
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152734"
---
# <a name="c-comments"></a>Comentarios en C

Un “comentario” es una secuencia de caracteres que comienza con una combinación de barra diagonal/asterisco (<strong>/\*</strong>) que el compilador trata como un único carácter de espacio en blanco y se pasa por alto de cualquier otra manera. Un comentario puede incluir cualquier combinación de caracteres del juego de caracteres representable, incluidos los caracteres de nueva línea, salvo el delimitador de "final de comentario" (<strong>\*/</strong>). Los comentarios pueden ocupar más de una línea, pero no se pueden anidar.

Los comentarios pueden aparecer en cualquier lugar en el que se permita un carácter de espacio en blanco. Dado que el compilador trata un comentario como si fuese un único carácter de espacio en blanco, no se pueden incluir comentarios dentro de tokens. El compilador omite los caracteres del comentario.

Use comentarios para documentar el código. Este ejemplo es un comentario admitido por el compilador:

```C
/* Comments can contain keywords such as
   for and while without generating errors. */
```

Los comentarios pueden aparecer en la misma línea que una instrucción de código:

```C
printf( "Hello\n" );  /* Comments can go here */
```

Puede anteponer un bloque de comentario descriptivo a funciones o módulos de programa:

```C
/* MATHERR.C illustrates writing an error routine
* for math functions.
*/
```

Puesto que los comentarios no pueden contener comentarios anidados, este ejemplo produce un error:

```C
/* Comment out this routine for testing

   /* Open file */
    fh = _open( "myfile.c", _O_RDONLY );
    .
    .
    .
*/
```

El error se produce porque el compilador reconoce el primer `*/`, después de las palabras `Open file`, como el final del comentario. Intenta procesar el texto restante y genera un error cuando encuentra `*/` fuera de un comentario.

Aunque se pueden utilizar comentarios para inhabilitar algunas líneas de código a modo de prueba, las directivas de preprocesador `#if` y `#endif` y la compilación condicional son una alternativa útil para esta tarea. Para obtener más información, vea [Directivas de preprocesador](../preprocessor/preprocessor-directives.md) en la *Referencia del preprocesador*.

**Específicos de Microsoft**

El compilador de Microsoft también admite los comentarios de una línea precedidos por dos barras diagonales (__//__). Si compila con /Za (estándar ANSI), estos comentarios generan errores. Estos comentarios no pueden extenderse a una segunda línea.

```C
// This is a valid comment
```

Los comentarios que comienzan con dos barras diagonales (__//__) se finalizan con el siguiente carácter de nueva línea que no vaya precedido por un carácter de escape. En el ejemplo siguiente, el carácter de nueva línea va precedido de una barra diagonal inversa (**\\**), por lo que crea una "secuencia de escape". Esta secuencia de escape hace que el compilador trate la línea siguiente como parte de la línea anterior. (Para obtener más información, vea [Secuencias de escape](../c-language/escape-sequences.md)).

```C
// my comment \
    i++;
```

Por consiguiente, la instrucción `i++;` está marcada como comentario.

El valor predeterminado para Microsoft C es que las extensiones de Microsoft estén habilitadas. Utilice /Za para deshabilitar estas extensiones.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Tokens de C](../c-language/c-tokens.md)
