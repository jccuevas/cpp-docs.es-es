---
title: "Advertencia de línea de comandos D9027 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- D9027
dev_langs:
- C++
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2769eb5f78cb1d5bdd6749e65429d83b69a2807b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="command-line-warning-d9027"></a>Advertencia de la línea de comandos D9027
archivo de código fuente '\<filename >' omite  
  
 CL.exe ha omitido el archivo de origen de entrada.  
  
 Esta advertencia puede deberse a un espacio entre la opción /Fo y un nombre de archivo de salida en una línea de comandos con la opción/c. Por ejemplo:  
  
```  
cl /c /Fo output.obj input.c   
```  
  
 Dado que hay un espacio entre /Fo y `output.obj`, CL.exe toma `output.obj` como el nombre del archivo de entrada. Para corregir el problema, quite el espacio:  
  
```  
cl /c /Fooutput.obj input.c   
```