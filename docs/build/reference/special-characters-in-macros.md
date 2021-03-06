---
title: Caracteres especiales en las macros
ms.date: 11/04/2016
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
ms.openlocfilehash: aac7b07500d2a129194e7234210a590cb5d0f19a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318373"
---
# <a name="special-characters-in-macros"></a>Caracteres especiales en las macros

Un signo de número (#) después de una definición especifica un comentario. Para especificar un signo de número literal en una macro, utilice un símbolo de intercalación (^), como en ^ #.

Un signo de dólar ($) especifica una llamada de macro. Para especificar un signo $ literal, utilice $$.

Para ampliar una definición de una nueva línea, al final de la línea con una barra diagonal inversa (\\). Cuando se invoca la macro, el carácter de barra diagonal inversa además de nueva línea se reemplaza por un espacio. Para especificar una barra diagonal inversa literal al final de la línea, precedidos por un símbolo de intercalación (^) o, seguido de un especificador de comentario (#).

Para especificar un carácter de nueva línea literal final de la línea con un símbolo de intercalación (^), como en:

```
CMDS = cls^
dir
```

## <a name="see-also"></a>Vea también

[Definición de una macro NMAKE](defining-an-nmake-macro.md)
