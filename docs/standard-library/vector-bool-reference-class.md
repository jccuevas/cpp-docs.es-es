---
title: "vector&lt;bool&gt;::reference (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vector<bool>::reference"
  - "std::vector<bool>::reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vector<bool> (clase de referencia)"
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# vector&lt;bool&gt;::reference (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase `vector<bool>::reference` es una clase proxy proporcionada por [vector\<bool\> Class](../standard-library/vector-bool-class.md) para simular `bool&`.  
  
## Comentarios  
 Se requiere una referencia simulada porque C\+\+ no permite de forma nativa referencias directas a bits.  `vector<bool>` solo utiliza un bit por elemento, al que se puede hacer referencia mediante esta clase proxy.  Sin embargo, la simulación de referencia no se completa porque algunas asignaciones no son válidas.  Por ejemplo, dado que no se puede tomar la dirección del objeto `vector<bool>::reference`, el siguiente código, que utiliza [vector\<bool\>::operator &#91;&#93;](../Topic/vector%3Cbool%3E::operator.md), no es correcto:  
  
```cpp  
    vector<bool> vb;  
...  
    bool* pb = &vb[1]; // conversion error - do not use  
    bool& refb = vb[1];   // conversion error - do not use  
  
```  
  
### Funciones miembro  
  
|||  
|-|-|  
|[voltear](../standard-library/vector-bool-reference-flip.md)|Invierte el valor booleano de un elemento vector.|  
|[operador bool](../standard-library/vector-bool-reference-operator-bool.md)|Proporciona una conversión implícita de `vector<bool>::reference` en `bool`.|  
|[operator\=](../standard-library/vector-bool-reference-operator-assign.md)|Asigna un valor booleano a un bit o asigna el valor contenido en un elemento al que se hace referencia a un bit.|  
  
## Requisitos  
 **Encabezado**: \<vector\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<vector\>](../standard-library/vector.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)