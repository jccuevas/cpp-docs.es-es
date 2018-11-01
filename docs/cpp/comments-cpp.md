---
title: Comentarios (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
ms.openlocfilehash: a90d9d37e69cb2e8be4ab18f77026fdce1221307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506111"
---
# <a name="comments-c"></a>Comentarios (C++)

Un comentario es texto que el compilador omite pero que es útil para los programadores. Los comentarios se usan normalmente para anotar código para su referencia futura. El compilador los trata como si fueran espacios en blanco. Puede utilizar comentarios en las pruebas para desactivar algunas líneas de código inactivos; Sin embargo, `#if` / `#endif` las directivas de preprocesador funcionan mejor para esto porque se puede encerrar el código que contiene los comentarios, pero no se pueden anidar comentarios.

Los comentarios de C++ se escriben de una de las maneras siguientes:

- Los caracteres `/*` (barra diagonal, asterisco), seguidos de cualquier secuencia de caracteres (incluidas nuevas líneas), seguidos de los caracteres `*/`. Esta sintaxis es la misma que para ANSI C.

- Los caracteres `//` (dos barras diagonales), seguidos de cualquier secuencia de caracteres. Una nueva línea que no va precedida inmediatamente de una barra diagonal inversa finaliza esta forma de comentario. Por tanto, normalmente se denomina "comentario de una sola línea".

Los caracteres de comentario (`/*`, `*/` y `//`) no tienen ningún significado especial dentro de una constante de caracteres, un literal de cadena o un comentario. Por tanto, los comentarios que usan la primera sintaxis no se pueden anidar.

## <a name="see-also"></a>Vea también

[Convenciones léxicas](../cpp/lexical-conventions.md)