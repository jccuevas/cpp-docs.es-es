---
title: Error del compilador C3068 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3068
dev_langs:
- C++
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f378a60c79defed4fb1738515ca5b65b2851056
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256560"
---
# <a name="compiler-error-c3068"></a>Error del compilador C3068
'función': una función 'naked' no puede contener objetos que requerirían desenredo si se produjera una excepción de C++  
  
 El compilador no pudo realizar el desenredo de pila en una [naked](../../cpp/naked-cpp.md) función que produjo una excepción porque se creó un objeto temporal en la función y el control de excepciones de C++ ([/EHsc](../../build/reference/eh-exception-handling-model.md)) se ha especificado.  
  
 Para resolver este error, realice al menos una de las siguientes acciones:  
  
-   No se compile con/EHsc.  
  
-   No marque la función como `naked`.  
  
-   No cree un objeto temporal en la función.  
  
 Si una función crea un objeto temporal en la pila, si la función produce una excepción, y si está habilitado el control de excepciones de C++, el compilador limpiará la pila si se produce una excepción.  
  
 Cuando se produce una excepción, compilador genera código, llamado prólogo y epílogo y que no están presentes en una función naked, se ejecuta para una función.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3068:  
  
```  
// C3068.cpp  
// compile with: /EHsc  
// processor: x86  
class A {  
public:  
   A(){}  
   ~A(){}  
};  
  
void b(A){}  
  
__declspec(naked) void c() {  
   b(A());   // C3068   
};  
```