---
title: C2785 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2785
dev_langs:
- C++
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc0ca6235e0fd4bdd22330e807464e96280ae461
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234034"
---
# <a name="compiler-error-c2785"></a>C2785 de Error del compilador
'declaration1' y 'declaración2' tienen distintos tipos de valor devueltos  
  
 El tipo de valor devuelto de especialización de plantilla de función difiere el tipo de valor devuelto de la plantilla de función principal.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Compruebe todas las especializaciones de la plantilla de función para mantener la coherencia.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2785:  
  
```  
// C2785.cpp  
// compile with: /c  
template<class T> void f(T);  
  
template<> int f(int); // C2785  
template<> void f(int); // OK  
```