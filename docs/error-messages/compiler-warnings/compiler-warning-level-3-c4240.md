---
title: Compilador advertencia (nivel 3) C4240 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4240
dev_langs:
- C++
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f0691230454ffd935d67c99f58b857cdc1ce0f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4240"></a>Advertencia del compilador (nivel 3) C4240
ha utilizado una extensión no estándar: acceso a 'nombredeclase' ahora definida como 'especificador de acceso', previamente se definió para ser 'especificador de acceso'  
  
 La compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), no se puede cambiar el acceso a una clase anidada. En las extensiones de Microsoft (/Ze) de manera predeterminada, es posible, con esta advertencia.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4240.cpp  
// compile with: /W3  
class X  
{  
private:  
   class N;  
public:  
   class N  
   {   // C4240  
   };  
};  
  
int main()  
{  
}  
```