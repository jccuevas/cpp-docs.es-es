---
title: Compilador advertencia (nivel 2) C4156 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4156
dev_langs:
- C++
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 249d90712b4a8b02f10deaa4d87cdbb7a7c17ae3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296454"
---
# <a name="compiler-warning-level-2-c4156"></a>Compilador C4156 de advertencia (nivel 2)
eliminación de una expresión de matriz sin utilizar la forma de matriz de 'delete'; formato de matriz sustituido  
  
 La forma de matriz no **eliminar** no se puede eliminar una matriz. El compilador traducía **eliminar** a la forma de matriz.  
  
 Esta advertencia se produce solo en las extensiones de Microsoft (/Ze).  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4156.cpp  
// compile with: /W2  
int main()  
{  
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];  
   delete array; // C4156, changed by compiler to "delete [] array;"  
}  
```