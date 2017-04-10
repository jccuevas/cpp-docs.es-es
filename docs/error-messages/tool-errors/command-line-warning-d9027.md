---
title: "Advertencia de línea de comandos D9027 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- D9027
dev_langs:
- C++
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 7d569243a6d0d1669a8964ab9c419cb0e7428ba9
ms.lasthandoff: 04/04/2017

---
# <a name="command-line-warning-d9027"></a>Advertencia de la línea de comandos D9027
archivo de código fuente '\<filename >' omite  
  
 CL.exe ha omitido el archivo de origen de entrada.  
  
 Esta advertencia puede deberse a un espacio entre la opción /Fo y un nombre de archivo de salida en una línea de comandos con la opción/c.. Por ejemplo:  
  
```  
cl /c /Fo output.obj input.c   
```  
  
 Dado que hay un espacio entre /Fo y `output.obj`, CL.exe toma `output.obj` como el nombre del archivo de entrada. Para corregir el problema, quite el espacio:  
  
```  
cl /c /Fooutput.obj input.c   
```
