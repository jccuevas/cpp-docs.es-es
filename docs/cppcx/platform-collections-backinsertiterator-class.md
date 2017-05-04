---
title: "Platform::Collections::BackInsertIterator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::BackInsertIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BackInsertIterator (Clase)"
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::Collections::BackInsertIterator (Clase)
Representa un iterador que inserta, en lugar de sobrescribir, elementos en el back\-end de una colección secuencial.  
  
## Sintaxis  
  
```  
template <  
   typename T  
>  
class BackInsertIterator : public ::std::iterator< ::std::output_iterator_tag, void, void, void, void>;  
```  
  
#### Parámetros  
 `T`  
 El tipo de elemento de la colección actual.  
  
## Comentarios  
 La clase BackInsertIterator implementa las reglas requeridas por [back\_insert\_iterator \(Clase\)](../standard-library/back-insert-iterator-class.md).  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[BackInsertIterator::BackInsertIterator \(Constructor\)](../cppcx/backinsertiterator-backinsertiterator-constructor.md)|Inicializa una nueva instancia de la clase BackInsertIterator.|  
  
### Operadores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[BackInsertIterator::operator\* \(Operador\)](../cppcx/backinsertiterator-operator-dereference-operator.md)|Recupera una referencia al objeto BackInsertIterator actual.|  
|[BackInsertIterator::operator\+\+ \(Operador\)](../cppcx/backinsertiterator-operator-increment-operator.md)|Devuelve una referencia al objeto BackInsertIterator actual. El iterador no se modifica.|  
|[BackInsertIterator::operator\= \(Operador\)](../cppcx/backinsertiterator-operator-assign-operator.md)|Anexa el objeto especificado al final de la colección secuencial actual.|  
  
## Jerarquía de herencia  
 `BackInsertIterator`  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Espacio de nombres de plataforma \(NOTINBUILD\)](http://msdn.microsoft.com/es-es/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)