---
title: "vector&lt;bool&gt;::reference::operator bool | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "operatorbool"
  - "vector<bool>::reference::operatorbool"
  - "bool"
  - "std::vector<bool>::reference::operatorbool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BOOL (operador)"
  - "reference::operator bool"
ms.assetid: b0e57869-18cc-4296-9061-da502f30120d
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# vector&lt;bool&gt;::reference::operator bool
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Proporciona una conversión implícita de `vector<bool>::reference` en `bool`.  
  
## Sintaxis  
  
```  
operator bool( ) const;  
```  
  
## Valor devuelto  
 El valor booleano del elemento del objeto [vector\<bool\>](../standard-library/vector-bool-class.md).  
  
## Comentarios  
 Este operador no puede modificar el objeto `vector<bool>`.  
  
## Requisitos  
 **Encabezado:** \<vector\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [vector\<bool\>::reference \(Clase\)](../standard-library/vector-bool-reference-class.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)