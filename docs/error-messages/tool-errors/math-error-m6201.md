---
title: "Error matemático M6201 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- M6201
dev_langs:
- C++
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17de7fab7b41a5a8acc2fed2f3c8185f66aadd9c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-m6201"></a>Error matemático M6201
'función': error _DOMAIN  
  
 Argumento pasado a la función especificada se realizó fuera del dominio de valores de entrada válidos para esa función.  
  
## <a name="example"></a>Ejemplo  
  
```  
result = sqrt(-1.0)   // C statement  
result = SQRT(-1.0)   !  FORTRAN statement  
```  
  
 Este error invoca la `_matherr` función con el nombre de función, sus argumentos y el tipo de error. Puede volver a escribir el `_matherr` función para personalizar el control de algunos errores matemáticos de punto flotante de tiempo de ejecución.