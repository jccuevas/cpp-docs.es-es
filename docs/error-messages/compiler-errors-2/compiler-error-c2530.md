---
title: Error del compilador C2530 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2530
dev_langs: C++
helpviewer_keywords: C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1f9ea1b462f2e0b141bdc624d77f548f19c4b71a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2530"></a>Error del compilador C2530
'identificador': se deben inicializar las referencias  
  
 Debe inicializar una referencia cuando se ha declarado, a menos que ya se haya declarado:  
  
-   Con la palabra clave [extern](../../cpp/using-extern-to-specify-linkage.md).  
  
-   Como miembro de una clase, estructura o unión (y se inicializa en el constructor).  
  
-   Como un parámetro en una definición o declaración de función.  
  
-   Como el tipo de valor devuelto de una función.  
  
 El ejemplo siguiente genera C2530:  
  
```  
// C2530.cpp  
int main() {  
   int i = 0;  
   int &j;   // C2530  
   int &k = i;   // OK  
}  
```