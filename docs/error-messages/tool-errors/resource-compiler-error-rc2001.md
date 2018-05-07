---
title: Error del compilador de recursos RC2001 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2001
dev_langs:
- C++
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ef1fd5d29fc5784ee418a8456cacec37e943b73
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-error-rc2001"></a>Error del compilador de recursos RC2001
nueva línea en constante  
  
 Una constante de cadena continuó en una segunda línea sin una barra diagonal inversa (**\\**) o de apertura y cierre entre comillas dobles (**"**).  
  
 Para interrumpir una constante de cadena que se encuentra en dos líneas en el archivo de origen, realice una de las siguientes acciones:  
  
-   Finalizar la primera línea con el carácter de continuación de línea, una barra diagonal inversa.  
  
-   La cadena en la primera línea con un signo de comillas dobles de cierre y abra la cadena en la línea siguiente con otra comilla.  
  
 No es suficiente finalizar la primera línea con \n, la secuencia de escape para incrustar un carácter de nueva línea en una constante de cadena.