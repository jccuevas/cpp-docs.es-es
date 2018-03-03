---
title: Error del compilador C2589 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2589
dev_langs:
- C++
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0c75c6c42bcaa60f95e6f7e5214bb28ce72f65f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2589"></a>Error del compilador C2589
'identificador': símbolo no válido en el lado derecho de '::'  
  
 Si una clase, estructura o unión nombre aparece a la izquierda del operador de resolución de ámbito (dos puntos dobles), el símbolo (token) de la derecha debe ser una clase, estructura o miembro de unión. De lo contrario, cualquier identificador global puede aparecer a la derecha.  
  
 No se pueden sobrecargar el operador de resolución de ámbito.  
  
 El ejemplo siguiente genera C2589:  
  
```  
// C2589.cpp  
void Test(){}  
class A {};  
void operator :: ();   // C2589  
  
int main() {  
   ::Test();  
}  
```