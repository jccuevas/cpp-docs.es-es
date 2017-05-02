---
title: "Platform::Collections::InputIterator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::InputIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InputIterator (Clase)"
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::Collections::InputIterator (Clase)
Proporciona un InputIterator de la Biblioteca de plantillas estándar para las colecciones derivadas de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].  
  
## Sintaxis  
  
```  
template <  
   typename X  
>  
class InputIterator;  
```  
  
#### Parámetros  
 `X`  
 El typename de la clase de plantilla InputIterator.  
  
## Miembros  
  
### Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|------------|-----------------|  
|`difference_type`|Una diferencia de puntero \(ptrdiff\_t\).|  
|`iterator_category`|La categoría de un iterador de entrada \(::std::input\_iterator\_tag\).|  
|`pointer`|Puntero a `const` `X`|  
|`reference`|Referencia a `const` `X`|  
|`value_type`|El typename `X`.|  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[InputIterator::InputIterator \(Constructor\)](../cppcx/inputiterator-inputiterator-constructor.md)|Inicializa una nueva instancia de la clase InputIterator.|  
  
### Operadores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[InputIterator::operator\!\= \(Operador\)](../cppcx/inputiterator-operator-inequality-operator.md)|Indica si el objeto InputIterator actual no es igual a un objeto InputIterator especificado.|  
|[InputIterator::operator\* \(Operador\)](../cppcx/inputiterator-operator-decrementoperator.md)|Recupera una referencia al elemento especificado por el objeto InputIterator actual.|  
|[InputIterator::operator\+\+ \(Operador\)](../cppcx/inputiterator-operator-increment-operator.md)|Incrementa el objeto InputIterator actual.|  
|[InputIterator::operator\=\= \(Operador\)](../cppcx/inputiterator-operator-equality-operator.md)|Indica si el objeto InputIterator actual es igual que un objeto InputIterator especificado.|  
|[InputIterator::operator\-\> \(Operador\)](../cppcx/inputiterator-operator-arrow-operator.md)|Recupera la dirección del elemento al que hace referencia el objeto InputIterator actual.|  
  
## Jerarquía de herencia  
 `InputIterator`  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Espacio de nombres de plataforma \(NOTINBUILD\)](http://msdn.microsoft.com/es-es/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)