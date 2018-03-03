---
title: C2687 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2687
dev_langs:
- C++
helpviewer_keywords:
- C2687
ms.assetid: 1d24b24a-cd0f-41cc-975c-b08dcfb7f402
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd6879fafa12a9757e18256520e7bd75957ca52b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2687"></a>C2687 de Error del compilador
'type': declaración de excepción no puede ser 'void' o denotar un tipo incompleto, puntero o referencia a un tipo incompleto  
  
 Para que un tipo que forme parte de una declaración de excepción, debe ser definida y no es void.  
  
 El ejemplo siguiente genera C2687:  
  
```  
// C2687.cpp  
class C;  
  
int main() {  
   try {}  
   catch (C) {}   // C2687 error  
}  
```  
  
 Posible resolución:  
  
```  
// C2687b.cpp  
// compile with: /EHsc  
class C {};  
  
int main() {  
   try {}  
   catch (C) {}  
}  
```