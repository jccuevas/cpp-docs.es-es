---
title: Error irrecuperable C1055 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1055
dev_langs:
- C++
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 68b9dc5ac8a574111a678086a03e2760941e766f
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1055"></a>Error irrecuperable C1055
límite del compilador: no hay claves  
  
 El archivo de origen contiene demasiados símbolos. El compilador se quedó sin claves hash para la tabla de símbolos.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones  
  
1.  Divida el archivo de origen en archivos más pequeños.  
  
2.  Eliminar archivos de encabezado innecesarios.  
  
3.  Volver a usar las variables temporales y globales en lugar de crear otros nuevos.
