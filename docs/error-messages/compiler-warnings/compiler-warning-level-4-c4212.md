---
title: Compilador advertencia (nivel 4) C4212 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4212
dev_langs:
- C++
helpviewer_keywords:
- C4212
ms.assetid: df781ea1-182d-4f9f-9a31-55b6ce80c711
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9573a6e29ce20a87fb75aa5810ebf4d696695a45
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4212"></a>Advertencia del compilador (nivel 4) C4212
ha utilizado una extensión no estándar: declaración de función utilizado puntos suspensivos  
  
 El prototipo de función tiene un número variable de argumentos. La definición de función no lo hace.  
  
 El ejemplo siguiente genera C4212:  
  
```  
// C4212.c  
// compile with: /W4 /Ze /c  
void f(int , ...);  
void f(int i, int j) {}  
```