---
title: Nombres de archivo largos en un archivo MAKE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, long filenames
- long filenames
ms.assetid: 626d56fc-8879-46ba-9c2d-dd386c78cccc
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f808faff82e9fcd29040f8d15e6cbaa9e037733
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="long-filenames-in-a-makefile"></a>Nombres de archivo largos en un archivo MAKE
Incluya nombres de archivo largos en comillas dobles, como se indica a continuación:  
  
```  
all : "VeryLongFileName.exe"  
```  
  
## <a name="see-also"></a>Vea también  
 [Contenido de un archivo MAKE](../build/contents-of-a-makefile.md)