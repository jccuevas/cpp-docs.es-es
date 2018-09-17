---
title: Macros de comando y Macros de opciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c66295a42fff6a2e6dde5205fb5d9139e6eceb6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705541"
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