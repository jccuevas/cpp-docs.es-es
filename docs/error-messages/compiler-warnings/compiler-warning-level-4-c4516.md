---
title: Compilador advertencia (nivel 4) C4516 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4516
dev_langs:
- C++
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 137fe601e911b309d28281ecee7e67a88e1bb0a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4516"></a>Advertencia del compilador (nivel 4) C4516
'clase:: símbolo': las declaraciones de acceso están en desuso; las declaraciones using de miembro son una alternativa mejor  
  
 El Comité de ANSI C++ ha declarado las declaraciones de acceso (cambiar el acceso de un miembro en una clase derivada sin la [con](../../cpp/using-declaration.md) palabra clave) a estar obsoletas. Pueden que las futuras versiones de C++ no admite las declaraciones de acceso.  
  
 El ejemplo siguiente genera C4516:  
  
```  
// C4516.cpp  
// compile with: /W4  
class A  
{  
public:  
   void x(char);  
};  
  
class B : protected A  
{  
public:  
   A::x;  // C4516 on access-declaration  
   // use the following line instead  
   // using A::x; // using-declaration, ok  
};  
  
int main()  
{  
}  
```