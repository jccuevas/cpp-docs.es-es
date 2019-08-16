---
title: Macros de comando y macros de opciones
ms.date: 11/04/2016
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
ms.openlocfilehash: c6dad7b50d265a1460a98747665d48051078163a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272443"
---
# <a name="command-macros-and-options-macros"></a>Macros de comando y macros de opciones

Macros de comandos están predefinidas para productos de Microsoft. Macros de opciones representan las opciones para estos productos y no están definidas de forma predeterminada. Ambos se usan en las reglas de inferencia predefinidas y se pueden usar en bloques de descripción o las reglas de inferencia definido por el usuario. Macros de comandos se pueden redefinir para representar la totalidad o parte de una línea de comandos, incluidas las opciones. Macros de opciones generan una cadena nula si ha dejado sin definir.

|Producto de Microsoft|Macros de comando|Definido como|Macros de opciones|
|-----------------------|-------------------|----------------|-------------------|
|Macro Assembler|**AS**|ml|**AFLAGS**|
|Compilador básica|**BC**|bc|**BFLAGS**|
|Compilador de C|**CC**|cl|**CFLAGS**|
|Compilador C++|**CPP**|cl|**CPPFLAGS**|
|Compilador C++|**CXX**|cl|**CXXFLAGS**|
|compilador de recursos|**RC**|rc|**RFLAGS**|

## <a name="see-also"></a>Vea también

[Macros NMAKE especiales](special-nmake-macros.md)
