---
title: Error grave de NMAKE U1051 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1051
dev_langs:
- C++
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 570c7e5d8e6e8250a67e4f032ac26b04388cfd00
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1051"></a>Error grave de NMAKE U1051
No hay memoria suficiente  
  
 NMAKE se quedó sin memoria, incluida la memoria virtual, porque el archivo MAKE es demasiado grande o compleja.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo  
  
1.  Libere espacio en disco.  
  
2.  Aumentar el tamaño del archivo de paginación de Windows NT o el archivo de intercambio de Windows.  
  
3.  Si sólo se utiliza parte del archivo MAKE, divida el archivo MAKE en archivos independientes o bien **! IF** preprocesar directivas para limitar la cantidad que debe procesar NMAKE. El **! IF** directivas incluyen **! IF**, `!IFDEF`, **! IFNDEF**, **! ELSE IF**, **! ELSE** `IFDEF`, y **! ELSE** `IFNDEF`.