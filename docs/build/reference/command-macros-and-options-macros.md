---
title: Macros de comando y macros de opciones
description: Describe las macros NMAKE predefinidas para las herramientas de compilación y sus opciones.
ms.date: 11/20/2019
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
no-loc:
- AS
- AFLAGS
- CC
- CFLAGS
- CPP
- CPPFLAGS
- CXX
- CXXFLAGS
- RC
- RFLAGS
- ias
- ml
- ml64
- cl
- rc
ms.openlocfilehash: d5c4477fd97e2a6c48dbac4d0ce83f7fd5f12ad6
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303171"
---
# <a name="command-macros-and-options-macros"></a>Macros de comando y macros de opciones

Las macros de comandos están predefinidas para productos de Microsoft. Las macros de opciones representan opciones para estos productos y no están definidas de forma predeterminada. Ambos se usan en reglas de inferencia predefinidas y se pueden usar en bloques de descripción o reglas de inferencia definidas por el usuario. Las macros de comandos se pueden redefinir para representar parte o toda la línea de comandos, incluidas las opciones. Las macros de opciones generan una cadena nula si se deja sin definir.

|Producto de Microsoft|Macro de comando|Definido como|Macro Options|
|-----------------------|-------------------|----------------|-------------------|
|Ensamblador de macros|**AS**|ml, ias o ml64|**AFLAGS**|
|Compilador de C|**CC**|cl|**CFLAGS**|
|Compilador C++|**CPP**|cl|**CPPFLAGS**|
|Compilador C++|**CXX**|cl|**CXXFLAGS**|
|compilador de recursos|**RC**|rc|**RFLAGS**|

## <a name="see-also"></a>Vea también

[Macros NMAKE especiales](special-nmake-macros.md)
