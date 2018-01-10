---
title: Compilador advertencia (nivel 4) C4208 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4208
dev_langs: C++
helpviewer_keywords: C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aefe97e67c566418067c0a7bff594c42f89364b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4208"></a>Advertencia del compilador (nivel 4) C4208
ha utilizado una extensión no estándar: delete [exp] - exp evalúan pero omite  
  
 Con las extensiones de Microsoft (/Ze), puede eliminar una matriz usando un valor entre corchetes con la [delete (operador)](../../cpp/delete-operator-cpp.md). El valor se omite.  
  
```  
// C4208.cpp  
// compile with: /W4  
int main()  
{  
   int * MyArray = new int[18];  
   delete [18] MyArray;      // C4208  
   MyArray = new int[18];  
   delete [] MyArray;        // ok  
}  
```  
  
 Estos valores no son válidos en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).