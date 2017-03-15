---
title: "Error del compilador C3409 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3409"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3409"
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# Error del compilador C3409
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se permite un bloque de atributos vacío  
  
 Los corchetes se interpretaron en el compilador como un bloque de [atributos](../../windows/cpp-attributes-reference.md), pero no se hallaron atributos.  
  
 El compilador puede generar este error si se usan corchetes como parte de la definición de una expresión lambda.  Este error se produce cuando el compilador no puede determinar si los corchetes forman parte de la definición de una expresión lambda o de un bloque de atributos.  Para obtener más información sobre las expresiones lambda, vea [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md).  
  
### Para corregir este error  
  
1.  Si los corchetes forman parte de un bloque de atributos:  
  
    1.  Proporcione uno o varios atributos en el bloque de atributos.  
  
    2.  Quite el bloque de atributos.  
  
2.  Si los corchetes forman parte de una expresión lambda:  
  
    1.  Asegúrese de que la expresión lambda sigue reglas de sintaxis válidas.  
  
         Para obtener más información sobre la sintaxis de las expresiones lambda, vea [Sintaxis de las expresiones lambda](../../cpp/lambda-expression-syntax.md).  
  
## Ejemplo  
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
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3409 porque una expresión lambda usa la especificación `mutable`, pero no proporciona una lista de parámetros.  El compilador no puede determinar si los corchetes forman parte de la definición de una expresión lambda o de un bloque de atributos.  
  
```  
// C3409b.cpp  
  
int main()  
{  
   [] mutable {}();  
}  
```  
  
## Vea también  
 [atributo](../../windows/cpp-attributes-reference.md)   
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)   
 [Sintaxis de las expresiones lambda](../../cpp/lambda-expression-syntax.md)