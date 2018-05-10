---
title: Advertencia de línea de comandos D9027 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9027
dev_langs:
- C++
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfe2493290c4e4cc5b744136b8e7036c6559220a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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