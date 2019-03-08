---
title: Dónde definir macros
ms.date: 11/04/2016
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
ms.openlocfilehash: 5a5e853627f5d337e3f0587cb41fdc77e7eeb4f5
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417923"
---
# <a name="where-to-define-macros"></a>Dónde definir macros

Definir macros en el archivo Tools.ini, archivos MAKE, archivo de comandos o una línea de comandos.

En un archivo MAKE o el archivo Tools.ini, cada definición de macro debe aparecer en una línea independiente y no puede comenzar con un espacio o tabulación. Se omiten los espacios o tabulaciones después del signo igual. Todos los [cadena de caracteres](../build/defining-an-nmake-macro.md) son literales, incluidas las comillas y espacios incrustados.

En una línea de comandos o el archivo de comandos, espacios y tabulaciones delimitan los argumentos y no se pueden delimitar el signo igual. Si `string` ha incorporado espacios o tabulaciones, encierre la propia cadena o la macro completa entre comillas dobles ("").

## <a name="see-also"></a>Vea también

[Definición de una macro NMAKE](../build/defining-an-nmake-macro.md)
