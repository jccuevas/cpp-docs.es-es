---
title: Error del compilador C3409 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3409
dev_langs:
- C++
helpviewer_keywords:
- C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1964cffd0593e87a790befd8a76ae13847f2058d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257275"
---
# <a name="compiler-error-c3409"></a>Error del compilador C3409
no se permite el bloque de atributos vacío  
  
 Los corchetes se interpretaron en el compilador como un [atributo](../../windows/cpp-attributes-reference.md) se encontraron bloque, pero ningún atributo.  
  
 El compilador puede generar este error cuando se usan corchetes como parte de la definición de una expresión lambda. Este error se produce cuando el compilador no puede determinar si los corchetes forman parte de la definición de una expresión lambda o de un bloque de atributos. Para obtener más información sobre las expresiones lambda, vea [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Si los corchetes forman parte de un bloque de atributos:  
  
    1.  Proporcionar uno o más atributos en el bloque de atributos.  
  
    2.  Quite el bloque de atributos.  
  
2.  Si los corchetes forman parte de una expresión lambda:  
  
    1.  Asegúrese de que la expresión lambda sigue las reglas de sintaxis válida.  
  
         Para obtener más información acerca de la sintaxis de las expresiones lambda, vea [sintaxis de expresiones Lambda](../../cpp/lambda-expression-syntax.md).  
  
    2.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera el error C3409.  
  
```  
// C3409.cpp  
// compile with: /c  
#include <windows.h>  
[]   // C3409  
class a {};  
  
// OK  
[object, uuid("00000000-0000-0000-0000-000000000000")]  
__interface x {};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000001")]  
class b : public x {};  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera el error C3409 porque una expresión lambda usa la `mutable` especificación, pero no proporciona una lista de parámetros. El compilador no puede determinar si los corchetes forman parte de la definición de una expresión lambda o de un bloque de atributos.  
  
```  
// C3409b.cpp  
  
int main()  
{  
   [] mutable {}();  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Atributo](../../windows/cpp-attributes-reference.md)   
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)   
 [Sintaxis de la expresión lambda](../../cpp/lambda-expression-syntax.md)