---
title: Último carácter en una cadena | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e207ec1d5489a629b765d398e26ac7c07771d0da
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384993"
---
# <a name="last-character-in-a-string"></a>Último carácter de una cadena

Use las sugerencias siguientes:

- Intervalos de bytes finales superponen el juego en muchos casos de caracteres ASCII. Puede utilizar análisis byte a byte para cualquier carácter de control (menor que 32).

- Tenga en cuenta la siguiente línea de código, lo que puede comprobar para ver si el último carácter de una cadena es un carácter de barra diagonal inversa:

    ```cpp
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?
        // . . .
    ```

   Dado que `strlen` no es compatible con MBCS, devuelve el número de bytes, no el número de caracteres, en una cadena multibyte. Además, tenga en cuenta que en algunas páginas de códigos (932, por ejemplo), '\\' (0x5c) es un byte final válido (`sz` es una cadena de C).

   Una posible solución es volver a escribir el código de este modo:

    ```cpp
    char *pLast;
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )
        // . . .
    ```

   Este código usa las funciones MBCS `_mbsrchr` y `_mbsinc`. Dado que estas funciones son compatibles con MBCS, puede distinguir un '\\'carácter y un byte final'\\'. El código realiza alguna acción si el último carácter en la cadena es un valor nulo ('\0').

## <a name="see-also"></a>Vea también

[Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)<br/>
[Asignación de caracteres](../text/character-assignment.md)