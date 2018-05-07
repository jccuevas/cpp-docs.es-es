---
title: Compilador advertencia (nivel 4) C4268 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4268
dev_langs:
- C++
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bef62649af39df950c3966ef93dddb6c71ec2fd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4268"></a>Advertencia del compilador (nivel 4) C4268
'identificador': los datos estáticos/globales 'const' inicializados con el constructor predeterminado de generados por el compilador rellenan el objeto con ceros  
  
 A **const** instancia global o estática de una clase no trivial se inicializa con un constructor predeterminado generado por el compilador.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4268.cpp  
// compile with: /c /LD /W4  
class X {  
public:  
   int m_data;  
};  
  
const X x1;   // C4268  
```  
  
 Como esta instancia de la clase es **const**, el valor de `m_data` no se puede cambiar.