---
title: Compilador advertencia (nivel 4) C4213 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4213
dev_langs: C++
helpviewer_keywords: C4213
ms.assetid: 59fc3f61-ebd2-499e-99d7-f57bec11eda1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: abe563bd91736c9dfb6c0efc6507763b03a329cf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4213"></a>Advertencia del compilador (nivel 4) C4213
ha utilizado una extensión no estándar: conversión de valor l  
  
 Con las extensiones de Microsoft (/Ze) de manera predeterminada, puede usar conversiones de tipos en el lado izquierdo de una instrucción de asignación.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4213.c  
// compile with: /W4  
void *a;  
void f()  
{  
   int   i[3];  
   a = &i;  
   *(( int * )a )++ = 3;  // C4213  
}  
  
int main()  
{  
}  
```  
  
 Tales conversiones no son válidas en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).