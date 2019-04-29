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
ms.openlocfilehash: 0f4905473dd6914547ad6ac129d34e438992c2af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320505"
---
# <a name="null-and-undefined-macros"></a>Macros Null y no definidas

Macros null y no definidas se amplían a cadenas nulas, pero una macro definida como una cadena null se considera definidos en las expresiones de preprocesamiento. Para definir una macro como una cadena nula, especificar ningún carácter excepto los espacios o tabulaciones después del signo igual (=) en una línea de comandos o el archivo de comandos e incluya la cadena null o una definición de las comillas dobles (""). Para definir una macro, utilice **! UNDEF.** Para obtener más información, consulte [directivas de preprocesamiento de archivos MAKE](makefile-preprocessing-directives.md).

## <a name="see-also"></a>Vea también

[Definición de una macro NMAKE](defining-an-nmake-macro.md)
