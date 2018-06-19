---
title: Error irrecuperable C1071 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1071
dev_langs:
- C++
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9cef64c327c0fd3b668947de52f2776cca2833c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227200"
---
# <a name="fatal-error-c1071"></a>Error irrecuperable C1071
no se esperaba el final de archivo encontrado en el comentario  
  
 El compilador ha alcanzado el final del archivo mientras se analizaba un comentario.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Falta el terminador de comentario (* /).  
  
2.  Falta el carácter de nueva línea después de un comentario en la última línea de un archivo de origen.  
  
 El ejemplo siguiente genera C1071:  
  
```  
// C1071.cpp  
int main() {  
}  
  
/* this comment is fine */  
/* forgot the closing tag        // C1071  
```