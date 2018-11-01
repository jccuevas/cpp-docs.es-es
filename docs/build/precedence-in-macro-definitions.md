---
title: Prioridad en las definiciones de macro
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
ms.openlocfilehash: 8829b3cdbc7b2324ef3d118f8ca45dd2a1621e7e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619090"
---
# <a name="precedence-in-macro-definitions"></a>Prioridad en las definiciones de macro

Si una macro tiene varias definiciones, NMAKE utiliza la definición de la prioridad más alta. En la lista siguiente se muestra el orden de prioridad, de mayor a menor:

1. Una macro definida en la línea de comandos

1. Una macro definida en un archivo MAKE o incluir archivo

1. Una macro de variables de entorno heredada

1. Una macro definida en el archivo Tools.ini

1. Una macro predefinida, como [CC](../build/command-macros-and-options-macros.md) y [AS](../build/command-macros-and-options-macros.md)

Use /E para hacer que las macros heredadas de variables de entorno para invalidar las macros de archivos MAKE con el mismo nombre. Use **! UNDEF** para invalidar una línea de comandos.

## <a name="see-also"></a>Vea también

[Definición de una macro NMAKE](../build/defining-an-nmake-macro.md)