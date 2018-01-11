---
title: Compilador advertencia (nivel 1) C4661 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4661
dev_langs: C++
helpviewer_keywords: C4661
ms.assetid: 603bb8b7-356d-4eef-924b-64d769bac5bd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 369644c97430abe3d0f2c263a61aa3ce27663ed6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4661"></a>Advertencia del compilador (nivel 1) C4661
'identificador': ninguna definición adecuada proporcionada para la solicitud de creación de instancias de plantilla explícitos  
  
 Un miembro de la clase de plantilla no está definido.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4661.cpp  
// compile with: /W1 /LD  
template<class T> class MyClass {  
public:  
   void i();   // declaration but not definition  
};  
template MyClass< int >;  // C4661  
```