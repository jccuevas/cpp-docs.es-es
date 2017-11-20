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
ms.openlocfilehash: 43e34f3c4aba212f373a5c44535533f38f1bf216
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="long-filenames-in-a-makefile"></a>Nombres de archivo largos en un archivo MAKE
Incluya nombres de archivo largos en comillas dobles, como se indica a continuación:  
  
```  
all : "VeryLongFileName.exe"  
```  
  
## <a name="see-also"></a>Vea también  
 [Contenido de un archivo MAKE](../build/contents-of-a-makefile.md)