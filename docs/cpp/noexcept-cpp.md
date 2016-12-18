---
title: "noexcept (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "noexcept_cpp"
dev_langs: 
  - "C++"
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# noexcept (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C \+\+ 11:** especifica si una función podría generar excepciones.  
  
## Sintaxis  
  
```vb  
ReturnType FunctionName(params) noexcept;  
ReturnType FunctionName(params) noexcept(noexcept(expression);  
```  
  
#### Parámetros  
 expresión  
 Una expresión constante que se evalúa como true o false.  La versión incondicional es equivalente a noexcept\(true\).  
  
## Comentarios  
 `noexcept` \(y su sinónimo `noecept(true)`\) especifican que la función nunca generará una excepción ni permitirá que una excepción se propague desde cualquier otra función a la que invoque de manera directa o indirecta.  Más específicamente, `noexcept` significa que la función es `noexcept` solo si todas las funciones a las que llama también son noexcept o const y no hay conversiones dinámicas evaluadas potencialmente que requieran una comprobación en tiempo de ejecución, expresiones typeid aplicadas a una expresión glvalue cuyo tipo es un tipo de clase polimórfico ni expresiones throw.  Sin embargo, el compilador no comprueba necesariamente cada ruta de acceso del código en busca de excepciones que podrían ascender hasta una función `noexcept`.  Si una excepción llega a una función marcada `noexcept`, [std::terminate](../Topic/terminate%20\(%3Cexception%3E\).md) se invoca de inmediato y no hay ninguna garantía de que se vayan a invocar los destructores de ningún objeto del ámbito.  
  
 Una función declarada con un noexcept condicional que se evalúa como noexcept\(false\) especifica que permite que las excepciones se propaguen.  Por ejemplo, una función que copia su argumento podría declararse noexcept a condición de que el objeto que se está copiando sea un tipo de datos antiguos sin formato \(POD\).  Este tipo de función podría declararse de este modo:  
  
```  
#include <type_traits>  
  
template <typename T>  
T copy_object(T& obj) noexcept(std::is_pod<T>)  
{  
 //. . .   
}  
  
```  
  
 Utilice `noexcept` en lugar del especificador de excepción `throw`, que está en desuso en C\+\+11 y versiones posteriores.  Le recomendamos que aplique `noexcept` a una función si está seguro de que nunca permitirá que una excepción se propague hacia arriba en la pila de llamadas.  Una función que se declara con `noexcept` permite a los compiladores generar un código más eficaz en varios contextos distintos.  
  
## Vea también  
 [Control de excepciones de C\+\+](../cpp/cpp-exception-handling.md)