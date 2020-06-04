---
title: Prioridad en las definiciones de macro
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
ms.openlocfilehash: 38a653a9f460beae81f9f88ea457870d30f25339
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320167"
---
# <a name="precedence-in-macro-definitions"></a>Prioridad en las definiciones de macro

Si una macro tiene varias definiciones, NMAKE utiliza la definición de la prioridad más alta. En la lista siguiente se muestra el orden de prioridad, de mayor a menor:

1. Una macro definida en la línea de comandos

1. Una macro definida en un archivo MAKE o incluir archivo

1. Una macro de variables de entorno heredada

1. Una macro definida en el archivo Tools.ini

1. Una macro predefinida, como [CC](command-macros-and-options-macros.md) y [AS](command-macros-and-options-macros.md)

Use /E para hacer que las macros heredadas de variables de entorno para invalidar las macros de archivos MAKE con el mismo nombre. Use **! UNDEF** para invalidar una línea de comandos.

## <a name="see-also"></a>Vea también

[Definición de una macro NMAKE](defining-an-nmake-macro.md)
