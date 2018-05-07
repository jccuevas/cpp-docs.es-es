---
title: Las herramientas del vinculador LNK1245 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1245
dev_langs:
- C++
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47a1c2e5f7bf66946dcc5816d7a20fd485b59b45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1245"></a>Error de las herramientas del vinculador LNK1245
subsistema 'subsistema' especificado; /SUBSYSTEM debe ser WINDOWS, WINDOWSCE o CONSOLE  
  
 [/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) se utiliza para compilar el objeto y una de las siguientes condiciones era true:  
  
-   Se definió un punto de entrada personalizado ([/Entry](../../build/reference/entry-entry-point-symbol.md)), que el vinculador no pudo inferir un subsistema.  
  
-   Se pasó un valor a la [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) opción del vinculador que no es válido para los objetos / CLR.  
  
 En ambos casos, la solución es especificar un valor válido para la opción de vinculador/SUBSYSTEM.