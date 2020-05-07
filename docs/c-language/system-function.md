---
title: system (Función)
ms.date: 11/04/2016
helpviewer_keywords:
- system function
ms.assetid: 0786ccdc-20cd-4d96-b3d8-3230507c3066
ms.openlocfilehash: e37de4e084de6727cf2858117945fd162f6b0d63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345128"
---
# <a name="system-function"></a>system (Función)

**ANSI 4.10.4.5** Contenido y modo de ejecución de la cadena por la función **system**

La función **system** ejecuta un comando interno del sistema operativo, o un archivo .EXE, .COM (.CMD en Windows NT) o .BAT dentro de un programa de C, en lugar de la línea de comandos.

La función system encuentra el intérprete de comandos, que es normalmente CMD.EXE en el sistema operativo Windows NT o COMMAND.COM en Windows. Después, la función system pasa la cadena del argumento al intérprete de comandos.

Para más información, vea [system, _wsystem](../c-runtime-library/reference/system-wsystem.md).

## <a name="see-also"></a>Vea también

[Funciones de la biblioteca](../c-language/library-functions.md)
