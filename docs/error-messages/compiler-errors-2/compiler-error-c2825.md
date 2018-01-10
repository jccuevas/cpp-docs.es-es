---
title: Error del compilador C2825 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2825
dev_langs: C++
helpviewer_keywords: C2825
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4b907c94b6c83354c139fd3df8b56b1b2287c0b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2825"></a>Error del compilador C2825
var: debe ser una clase o espacio de nombres cuando seguido de '::'  
  
 Se realiza un intento incorrecto para formar un nombre completo.  
  
 Por ejemplo, asegúrese de que el código no contiene una declaración de función donde el nombre de función comienza con::.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2825:  
  
```  
// C2825.cpp  
typedef int i;  
int main() {  
   int* p = new int;  
   p->i::i();   // C2825  
   // try the following line instead  
   // p->i::~i();  
}  
```