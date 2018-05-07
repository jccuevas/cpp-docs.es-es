---
title: Compilador advertencia (nivel 1) C4269 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4269
dev_langs:
- C++
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e393c657e12f84d3cadfacd469e35e3472a39d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4269"></a>Advertencia del compilador (nivel 1) C4269
'identificador': 'const' automática de los datos inicializada con el constructor predeterminado de generados por el compilador produce resultados no confiables  
  
 A **const** automáticas de instancias de una clase no trivial se inicializan con un constructor predeterminado generado por el compilador.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4269.cpp  
// compile with: /c /LD /W1  
class X {  
public:  
   int m_data;  
};  
  
void g() {  
   const X x1;   // C4269  
};  
```  
  
 Dado que esta instancia de la clase se genera en la pila, el valor inicial de `m_data` puede ser cualquier cosa. Además, ya que es un **const** de instancia, el valor de `m_data` nunca se puede cambiar.