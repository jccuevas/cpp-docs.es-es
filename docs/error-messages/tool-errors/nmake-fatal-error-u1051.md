---
title: Error grave de NMAKE U1051 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1051
dev_langs: C++
helpviewer_keywords: U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 93c109bf723b3c4cf08e998a715fe8f6f33be466
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1051"></a>Error grave de NMAKE U1051
No hay memoria suficiente  
  
 NMAKE se quedó sin memoria, incluida la memoria virtual, porque el archivo MAKE es demasiado grande o compleja.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo  
  
1.  Libere espacio en disco.  
  
2.  Aumentar el tamaño del archivo de paginación de Windows NT o el archivo de intercambio de Windows.  
  
3.  Si sólo se utiliza parte del archivo MAKE, divida el archivo MAKE en archivos independientes o bien **! IF** preprocesar directivas para limitar la cantidad que debe procesar NMAKE. El **! IF** directivas incluyen **! IF**, `!IFDEF`, **! IFNDEF**, **! ELSE IF**, **! ELSE** `IFDEF`, y **! ELSE** `IFNDEF`.