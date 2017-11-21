---
title: Compilador advertencia (nivel 4) C4256 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4256
dev_langs: C++
helpviewer_keywords: C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3bb16c84a03bddad1eeb7dd5cfc6c652857d83b7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4256"></a>Advertencia del compilador (nivel 4) C4256
'función': constructor de clase con bases virtuales tiene '...'; las llamadas pueden no ser compatibles con versiones anteriores de Visual C++  
  
 Posible incompatibilidad.  
  
 Observe el siguiente ejemplo de código. Si la definición del constructor S2:: s2 (int i,...) se ha compilado con una versión del compilador de Visual C++ antes de la versión 7, pero en el siguiente ejemplo se compila con la versión actual, la llamada al constructor para S3 no funcionaría correctamente debido un caso especial de cambio de convención de llamada. Si ambos se compilaron con Visual C++ 6.0, la llamada no funcionaría bastante derecha, a menos que se pasa ningún parámetro para los puntos suspensivos.  
  
 Para corregir esta advertencia,  
  
1.  No utilice puntos suspensivos en un constructor.  
  
2.  Asegúrese de que todos los componentes de su proyecto se generan con la versión actual (incluida cualquier biblioteca que pueda definir o hacer referencia a esta clase), a continuación, deshabilita el uso de advertencia la [advertencia](../../preprocessor/warning.md) pragma.  
  
 El ejemplo siguiente genera C4256:  
  
```  
// C4256.cpp  
// compile with: /W4  
// #pragma warning(disable : 4256)  
struct S1  
{  
};  
  
struct S2: virtual public S1  
{  
   S2( int i, ... )    // C4256  
   {  
      i = 0;  
   }  
   /*  
   // try the following line instead  
   S2( int i)  
   {  
      i = 0;  
   }  
   */  
};  
  
void func1()  
{  
   S2 S3( 2, 1, 2 );   // C4256  
   // try the following line instead  
   // S2 S3( 2 );  
}  
  
int main()  
{  
}  
```