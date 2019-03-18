---
title: Comentarios en un archivo MAKE
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, comments
ms.assetid: 76fd9e3d-5966-47f4-a091-c9e80b232b49
ms.openlocfilehash: c66819210d2112f9a68243ed4d3b34f491caae9d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827514"
---
# <a name="comments-in-a-makefile"></a>Comentarios en un archivo MAKE

Preceder a un comentario con un signo de número (#). NMAKE omite el texto en el signo de número para el siguiente carácter de nueva línea. Ejemplos:

```
# Comment on line by itself
OPTIONS = /MAP  # Comment on macro definition line

all.exe : one.obj two.obj  # Comment on dependency line
    link one.obj two.obj
# Comment in commands block
#   copy *.obj \objects  # Command turned into comment
    copy one.exe \release

.obj.exe:  # Comment on inference rule line
    link $<

my.exe : my.obj ; link my.obj  # Err: cannot comment this
# Error: # must be the first character
.obj.exe: ; link $<  # Error: cannot comment this
```

Para especificar un signo de número literal, precedidos por un símbolo de intercalación (**^**), como sigue:

```
DEF = ^#define  #Macro for a C preprocessing directive
```

## <a name="see-also"></a>Vea también

[Contenido de un archivo MAKE](contents-of-a-makefile.md)
