---
title: Compilador advertencia (nivel 1) C4269 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4269
dev_langs:
- C++
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e3d276aa5744d457ee987334d65728b1835593ca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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