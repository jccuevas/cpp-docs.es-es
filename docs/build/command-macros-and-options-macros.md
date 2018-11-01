---
title: Macros de comando y macros de opciones
ms.date: 11/04/2016
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
ms.openlocfilehash: f18cfd6ada235485a5fe47bdc94b49631b9abbbe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601310"
---
# <a name="command-macros-and-options-macros"></a>Macros de comando y macros de opciones

Macros de comandos están predefinidas para productos de Microsoft. Macros de opciones representan las opciones para estos productos y no están definidas de forma predeterminada. Ambos se usan en las reglas de inferencia predefinidas y se pueden usar en bloques de descripción o las reglas de inferencia definido por el usuario. Macros de comandos se pueden redefinir para representar la totalidad o parte de una línea de comandos, incluidas las opciones. Macros de opciones generan una cadena nula si ha dejado sin definir.

|Producto de Microsoft|Macros de comando|Definido como|Macros de opciones|
|-----------------------|-------------------|----------------|-------------------|
|Macro Assembler|**IGUAL QUE**|ml|**AFLAGS**|
|Compilador básica|**CONTINUIDAD DEL NEGOCIO**|continuidad del negocio|**BFLAGS**|
|Compilador de C|**CC**|CL|**CFLAGS**|
|Compilador C++|**CPP**|CL|**CPPFLAGS**|
|Compilador C++|**CXX**|CL|**CXXFLAGS**|
|compilador de recursos|**RC**|rc|**RFLAGS**|

## <a name="see-also"></a>Vea también

[Macros NMAKE especiales](../build/special-nmake-macros.md)