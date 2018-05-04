---
title: Comentarios (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 919c40dce53dd5d1c8847287099c61c3e1b229cf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="comments-c"></a>Comentarios (C++)
Un comentario es texto que el compilador omite pero que es útil para los programadores. Los comentarios se usan normalmente para anotar código para su referencia futura. El compilador los trata como si fueran espacios en blanco. Puede utilizar comentarios en las pruebas para desactivar algunas líneas de código; Sin embargo, `#if` / `#endif` directivas de preprocesador funcionan mejor para esto porque se puede encerrar el código que contiene comentarios, pero no se pueden anidar comentarios.  
  
 Los comentarios de C++ se escriben de una de las maneras siguientes:  
  
-   Los caracteres `/*` (barra diagonal, asterisco), seguidos de cualquier secuencia de caracteres (incluidas nuevas líneas), seguidos de los caracteres `*/`. Esta sintaxis es la misma que para ANSI C.  
  
-   Los caracteres `//` (dos barras diagonales), seguidos de cualquier secuencia de caracteres. Una nueva línea que no va precedida inmediatamente de una barra diagonal inversa finaliza esta forma de comentario. Por tanto, normalmente se denomina "comentario de una sola línea".  
  
 Los caracteres de comentario (`/*`, `*/` y `//`) no tienen ningún significado especial dentro de una constante de caracteres, un literal de cadena o un comentario. Por tanto, los comentarios que usan la primera sintaxis no se pueden anidar.  
  
## <a name="see-also"></a>Vea también  
 [Convenciones léxicas](../cpp/lexical-conventions.md)