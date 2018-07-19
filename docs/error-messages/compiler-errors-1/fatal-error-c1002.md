---
title: Error irrecuperable C1002 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1002
dev_langs:
- C++
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c63a8d399b3e8c781694d89825e7898fd1db4639
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225056"
---
# <a name="fatal-error-c1002"></a>Error irrecuperable C1002
el compilador no tiene espacio en el montón en el paso 2  
  
 El compilador se quedó sin espacio de memoria dinámica durante su segundo paso, probablemente debido a un programa con demasiados símbolos o expresiones complejas.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo  
  
1.  Divida el archivo de código fuente en varios archivos más pequeños.  
  
2.  Dividir expresiones en subexpresiones más pequeñas.  
  
3.  Quite otros programas o controladores que consumen memoria.