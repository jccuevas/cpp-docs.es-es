---
title: Compilador advertencia (nivel 4) C4212 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4212
dev_langs:
- C++
helpviewer_keywords:
- C4212
ms.assetid: df781ea1-182d-4f9f-9a31-55b6ce80c711
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb70cf045a1cc563e4eb009ed00ffe82be812b0b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292008"
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