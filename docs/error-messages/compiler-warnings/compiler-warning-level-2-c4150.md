---
title: Compilador advertencia (nivel 2) C4150 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4150
dev_langs:
- C++
helpviewer_keywords:
- C4150
ms.assetid: ff1760ec-0d9f-4d45-b797-94261624becf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3108da1b203160456e0823b4d9a3fd594b705a8b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-2-c4150"></a>Compilador advertencia (nivel 2) C4150
eliminación de puntero a tipo incompleto 'type'; no llama a un destructor  
  
 El **eliminar** operador se llama para eliminar un tipo que se ha declarado pero no definido, por lo que el compilador no encuentra un destructor.  
  
 El ejemplo siguiente genera C4150:  
  
```  
// C4150.cpp  
// compile with: /W2  
class  IncClass;  
  
void NoDestruct( IncClass* pIncClass )  
{  
   delete pIncClass;  
} // C4150, define class to resolve  
  
int main()  
{  
}  
```