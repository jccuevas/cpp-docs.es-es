---
title: Macros Null y no definidas
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
ms.openlocfilehash: cf2dce2132cc1e7065cb0b93f1debd403f7a8342
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417234"
---
# <a name="null-and-undefined-macros"></a>Macros Null y no definidas

Macros null y no definidas se amplían a cadenas nulas, pero una macro definida como una cadena null se considera definidos en las expresiones de preprocesamiento. Para definir una macro como una cadena nula, especificar ningún carácter excepto los espacios o tabulaciones después del signo igual (=) en una línea de comandos o el archivo de comandos e incluya la cadena null o una definición de las comillas dobles (""). Para definir una macro, utilice **! UNDEF.** Para obtener más información, consulte [directivas de preprocesamiento de archivos MAKE](../build/makefile-preprocessing-directives.md).

## <a name="see-also"></a>Vea también

[Definición de una macro NMAKE](../build/defining-an-nmake-macro.md)
