---
title: Macros null y no definidas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eee6e713715e4709af990878224261a41f5470e3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702642"
---
# <a name="null-and-undefined-macros"></a>Macros Null y no definidas

Macros null y no definidas se amplían a cadenas nulas, pero una macro definida como una cadena null se considera definidos en las expresiones de preprocesamiento. Para definir una macro como una cadena nula, especificar ningún carácter excepto los espacios o tabulaciones después del signo igual (=) en una línea de comandos o el archivo de comandos e incluya la cadena null o una definición de las comillas dobles (""). Para definir una macro, utilice **! UNDEF.** Para obtener más información, consulte [directivas de preprocesamiento de archivos MAKE](../build/makefile-preprocessing-directives.md).

## <a name="see-also"></a>Vea también

[Definición de una macro NMAKE](../build/defining-an-nmake-macro.md)