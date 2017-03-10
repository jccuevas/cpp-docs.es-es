---
title: Comentarios en C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- code comments, C code
- comments, documenting code
- comments, C code
- /* */ comment delimiters
- comments
ms.assetid: 0f5f2825-e673-49e7-8669-94e2f5294989
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
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
ms.openlocfilehash: f8281cce930a9f1b98536b65762bf8b940b0d973
ms.lasthandoff: 02/24/2017

---
# <a name="c-comments"></a>Comentarios en C
Un “comentario” es una secuencia de caracteres que comienza con una combinación de barra diagonal/asterisco (<b>/\*</b>) que el compilador trata como un único carácter de espacio en blanco y se pasa por alto de cualquier otra manera. Un comentario puede incluir cualquier combinación de caracteres del juego de caracteres representable, incluidos los caracteres de nueva línea, salvo el delimitador de "final de comentario" (<b>\*/</b>). Los comentarios pueden ocupar más de una línea, pero no se pueden anidar.  
  
 Los comentarios pueden aparecer en cualquier lugar en el que se permita un carácter de espacio en blanco. Dado que el compilador trata un comentario como si fuese un único carácter de espacio en blanco, no se pueden incluir comentarios dentro de tokens. El compilador omite los caracteres del comentario.  
  
 Use comentarios para documentar el código. Este ejemplo es un comentario admitido por el compilador:  
  
```  
/* Comments can contain keywords such as  
   for and while without generating errors. */  
```  
  
 Los comentarios pueden aparecer en la misma línea que una instrucción de código:  
  
```  
printf( "Hello\n" );  /* Comments can go here */  
```  
  
 Puede anteponer un bloque de comentario descriptivo a funciones o módulos de programa:  
  
```  
/* MATHERR.C illustrates writing an error routine   
 * for math functions.   
 */   
```  
  
 Puesto que los comentarios no pueden contener comentarios anidados, este ejemplo produce un error:  
  
```  
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
  
 El compilador de Microsoft también admite los comentarios de una línea precedidos por dos barras diagonales (**//**). Si compila con /Za (estándar ANSI), estos comentarios generan errores. Estos comentarios no pueden extenderse a una segunda línea.  
  
```  
// This is a valid comment  
```  
  
 Los comentarios que comienzan con dos barras diagonales (**//**) se finalizan con el siguiente carácter de nueva línea que no vaya precedido por un carácter de escape. En el ejemplo siguiente, el carácter de nueva línea va precedido de una barra diagonal inversa (**\\**), por lo que crea una "secuencia de escape". Esta secuencia de escape hace que el compilador trate la línea siguiente como parte de la línea anterior. (Para obtener más información, vea [Secuencias de escape](../c-language/escape-sequences.md)).  
  
```  
// my comment \  
    i++;   
```  
  
 Por consiguiente, la instrucción `i++;` está marcada como comentario.  
  
 El valor predeterminado para Microsoft C es que las extensiones de Microsoft estén habilitadas. Utilice /Za para deshabilitar estas extensiones.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Tokens de C](../c-language/c-tokens.md)

