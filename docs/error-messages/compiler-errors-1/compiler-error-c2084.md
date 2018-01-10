---
title: C2084 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2084
dev_langs: C++
helpviewer_keywords: C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cf9e0888e0f959d77198efe036c0234c985ea365
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2084"></a>C2084 de Error del compilador
función '*función*' ya tiene un cuerpo  
  
 La función ya se ha definido.  
  
 En las versiones de Visual C++ antes de Visual Studio 2002,  
  
-   El compilador aceptaba varias especializaciones de plantilla que se resuelven en el mismo tipo real, aunque las definiciones adicionales nunca estaría disponibles. Ahora, el compilador detecta estas definiciones múltiples.  
  
-   `__int32`y `int` se trataban como tipos distintos. El compilador trata ahora `__int32` como sinónimo de `int`. Esto significa que el compilador detecta varias definiciones si una función está sobrecargada en ambos `__int32` y `int` y produce un error.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2084:  
  
```cpp  
// C2084.cpp  
void Func(int);  
void Func(int) {}   // define function  
void Func(int) {}   // C2084 second definition  
```  
  
Para corregir este error, quite la definición de duplicados:  
  
```  
// C2084b.cpp  
// compile with: /c  
void Func(int);  
void Func(int) {}  
```