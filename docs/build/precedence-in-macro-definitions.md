---
title: Prioridad en definiciones de Macro | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7421ef51c37e3724bdb986321581e6736a62e18b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="precedence-in-macro-definitions"></a>Prioridad en las definiciones de macro
Si una macro tiene varias definiciones, NMAKE utiliza la definición de prioridad más alta. En la lista siguiente muestra el orden de prioridad, de mayor a menor:  
  
1.  Una macro definida en la línea de comandos  
  
2.  Una macro definida en un archivo MAKE o archivo de inclusión  
  
3.  Una macro de variables de entorno heredada  
  
4.  Una macro definida en el archivo Tools.ini  
  
5.  Una macro predefinida, como [CC](../build/command-macros-and-options-macros.md) y [AS](../build/command-macros-and-options-macros.md)  
  
 Use /E para hacer que las macros heredadas de variables de entorno para reemplazar macros de archivo MAKE con el mismo nombre. Utilice **! UNDEF** para reemplazar una línea de comandos.  
  
## <a name="see-also"></a>Vea también  
 [Definición de una macro NMAKE](../build/defining-an-nmake-macro.md)