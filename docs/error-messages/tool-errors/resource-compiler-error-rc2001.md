---
title: Error del compilador de recursos RC2001 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC2001
dev_langs: C++
helpviewer_keywords: RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7c04110898780495f918c1e37c0068daead340a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rc2001"></a>Error del compilador de recursos RC2001
nueva línea en constante  
  
 Una constante de cadena continuó en una segunda línea sin una barra diagonal inversa (**\\**) o de apertura y cierre entre comillas dobles (**"**).  
  
 Para interrumpir una constante de cadena que se encuentra en dos líneas en el archivo de origen, realice una de las siguientes acciones:  
  
-   Finalizar la primera línea con el carácter de continuación de línea, una barra diagonal inversa.  
  
-   La cadena en la primera línea con un signo de comillas dobles de cierre y abra la cadena en la línea siguiente con otra comilla.  
  
 No es suficiente finalizar la primera línea con \n, la secuencia de escape para incrustar un carácter de nueva línea en una constante de cadena.