---
title: Compilador advertencia (nivel 4) C4714 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4714
dev_langs:
- C++
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5d49ff1bbf6538965d277b0afdd6c96fd9c71ef0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4714"></a>Advertencia del compilador (nivel 4) C4714
la función 'función' marcada como __forceinline no está entre línea  
  
 La función especificada se seleccionaron para la expansión en línea, pero el compilador no realizó la inserción.  
  
 Aunque `__forceinline` es una indicación de mayor prioridad al compilador que `__inline`, inclusión aún se realice a discreción del compilador, pero no se utiliza heurística para determinar los beneficios de inclusión esta función.  
  
 En algunos casos, el compilador no insertará una determinada función por motivos mecánicos. Por ejemplo, el compilador no insertará:  
  
-   Una función de si el resultado de la combinación de SEH y C++ EH.  
  
-   Algunas funciones de copia construyen objetos que se pasan por valor cuando - GX//EHs//EHa está activada.  
  
-   Funciones que devuelven un objeto no se pueden desenredar por valor cuando - GX//EHs//EHa está activada.  
  
-   Funciones con código ensamblador en línea al compilar sin - Og/Ox/O1/O2.  
  
-   Funciones con una lista de argumentos de variable.  
  
-   Una función con un **intente** instrucción (control de excepciones de C++).  
  
 El ejemplo siguiente genera C4714:  
  
```  
// C4714.cpp  
// compile with: /Ob1 /GX /W4  
__forceinline void func1()  
{  
   try  
   {  
   }  
   catch (...)  
   {  
   }  
}  
  
void func2()  
{  
   func1();   // C4714  
}  
  
int main()  
{  
}  
```