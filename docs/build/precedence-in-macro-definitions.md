---
title: Prioridad en definiciones de Macro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21a3d8873fd1fee61afec865181bab27305bebfd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722220"
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