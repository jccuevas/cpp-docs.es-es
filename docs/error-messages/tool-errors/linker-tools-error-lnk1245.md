---
title: Las herramientas del vinculador LNK1245 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1245
dev_langs:
- C++
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 142d88489748f30308395d64f3db78178a9b856f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1245"></a>Error de las herramientas del vinculador LNK1245
subsistema 'subsistema' especificado; /SUBSYSTEM debe ser WINDOWS, WINDOWSCE o CONSOLE  
  
 [/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) se utiliza para compilar el objeto y una de las siguientes condiciones era true:  
  
-   Se definió un punto de entrada personalizado ([/Entry](../../build/reference/entry-entry-point-symbol.md)), que el vinculador no pudo inferir un subsistema.  
  
-   Se pasó un valor a la [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) opción del vinculador que no es válido para los objetos / CLR.  
  
 En ambos casos, la solución es especificar un valor válido para la opción de vinculador/SUBSYSTEM.