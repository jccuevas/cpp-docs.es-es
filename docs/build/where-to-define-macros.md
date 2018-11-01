---
title: Dónde definir macros
ms.date: 11/04/2016
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
ms.openlocfilehash: 130863f8c5640a0c4915734732d93fc00d3d6479
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656253"
---
# <a name="where-to-define-macros"></a>Dónde definir macros

Definir macros en el archivo Tools.ini, archivos MAKE, archivo de comandos o una línea de comandos.

En un archivo MAKE o el archivo Tools.ini, cada definición de macro debe aparecer en una línea independiente y no puede comenzar con un espacio o tabulación. Se omiten los espacios o tabulaciones después del signo igual. Todos los [cadena de caracteres](../build/defining-an-nmake-macro.md) son literales, incluidas las comillas y espacios incrustados.

En una línea de comandos o el archivo de comandos, espacios y tabulaciones delimitan los argumentos y no se pueden delimitar el signo igual. Si `string` ha incorporado espacios o tabulaciones, encierre la propia cadena o la macro completa entre comillas dobles ("").

## <a name="see-also"></a>Vea también

[Definición de una macro NMAKE](../build/defining-an-nmake-macro.md)