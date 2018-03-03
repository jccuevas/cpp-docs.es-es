---
title: Compilador advertencia (nivel 1) C4526 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4526
dev_langs:
- C++
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a74d7d2e2c745a4c8e29736c1e3a7fc38892d5f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4526"></a>Advertencia del compilador (nivel 1) C4526
'función': una función miembro static no puede invalidar la función virtual ' virtual reemplazará, se ocultará la función virtual  
  
 La función miembro estática cumple los criterios para invalidar la función virtual, lo que hace la función miembro virtual y static.  
  
 El código siguiente genera la advertencia C4526:  
  
```  
// C4526.cpp  
// compile with: /W1 /c  
// C4526 expected  
struct myStruct1 {  
   virtual void __stdcall func( int ) = 0;  
};  
  
struct myStruct2: public myStruct1 {  
   static void __stdcall func( int );  
};  
```  
  
 Los siguientes son posibles soluciones:  
  
-   Si la función se ha diseñado para reemplazar la función virtual de clase base, quite el especificador static.  
  
-   Si la función debía ser una función miembro estática, cambie el nombre para que no entre en conflicto con la función virtual de clase base.