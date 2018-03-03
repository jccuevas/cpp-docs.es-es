---
title: Error irrecuperable C1002 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1002
dev_langs:
- C++
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d299c6793e106ce516a81a9a81312ef0a09c25bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1002"></a>Error irrecuperable C1002
el compilador no tiene espacio en el montón en el paso 2  
  
 El compilador se quedó sin espacio de memoria dinámica durante su segundo paso, probablemente debido a un programa con demasiados símbolos o expresiones complejas.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo  
  
1.  Divida el archivo de código fuente en varios archivos más pequeños.  
  
2.  Dividir expresiones en subexpresiones más pequeñas.  
  
3.  Quite otros programas o controladores que consumen memoria.