---
title: "Platform::Collections::VectorIterator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator (Clase)"
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Platform::Collections::VectorIterator (Clase)
Proporciona un iterador de la Biblioteca de plantillas estándar para los objetos derivados de la interfaz IVector de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].  
  
 VectorIterator es un iterador de proxy que almacena elementos de tipo VectorProxy\<T\>. Sin embargo, el objeto proxy casi nunca está visible en el código del usuario. Para obtener más información, consulta [Colecciones \(C\+\+\/CX\)](../cppcx/collections-c-cx.md).  
  
## Sintaxis  
  
```  
template <  
   typename T  
>  
class VectorIterator;  
```  
  
#### Parámetros  
 `T`  
 El typename de la clase de plantilla VectorIterator.  
  
## Miembros  
  
### Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|------------|-----------------|  
|`difference_type`|Una diferencia de puntero \(ptrdiff\_t\).|  
|`iterator_category`|La categoría de un iterador de acceso aleatorio \(::std::random\_access\_iterator\_tag\).|  
|`pointer`|Un puntero a un tipo interno, Platform::Collections::Details::VectorProxy\<T\>, necesario para la implementación de VectorIterator.|  
|`reference`|Una referencia a un tipo interno, Platform::Collections::Details::VectorProxy\<T\>, necesario para la implementación de VectorIterator.|  
|`value_type`|El typename `T`.|  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[VectorIterator::VectorIterator \(Constructor\)](../cppcx/vectoriterator-vectoriterator-constructor.md)|Inicializa una nueva instancia de la clase VectorIterator.|  
  
### Operadores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[VectorIterator::operator\- \(Operador\)](../cppcx/vectoriterator-operator-minus-operator.md)|Resta un número especificado de elementos del iterador actual produciendo un nuevo iterador, o un iterador especificado del iterador actual produciendo el número de elementos entre los iteradores.|  
|[VectorIterator::operator\-\- \(Operador\)](../cppcx/vectoriterator-operator-decrement-operator.md)|Disminuye el objeto VectorIterator actual.|  
|[VectorIterator::operator\!\= \(Operador\)](../cppcx/vectoriterator-operator-inequality-operator.md)|Indica si el objeto VectorIterator actual no es igual que un objeto VectorIterator especificado.|  
|[VectorIterator::operator\* \(Operador\)](../cppcx/vectoriterator-operator-dereference-operator.md)|Recupera una referencia al elemento especificado por el objeto VectorIterator actual.|  
|[VectorIterator::operatorOperator](../cppcx/vectoriterator-operatoroperator.md)|Recupera una referencia al elemento que es un desplazamiento especificado del objeto VectorIterator actual.|  
|[\(ELIMINAR\) VectorIterator::operator\+ \(Operador\)](http://msdn.microsoft.com/es-es/b0b1af2c-e2a8-4876-99dc-7351bfc46ce4)|Devuelve un objeto VectorIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorIterator especificado.|  
|[VectorIterator::operator\+\+ \(Operador\)](../cppcx/vectoriterator-operator-increment-operator.md)|Incrementa el objeto VectorIterator actual.|  
|[VectorIterator::operator\+\= \(Operador\)](../cppcx/vectoriterator-operator-plus-assign-operator.md)|Incrementa el objeto VectorIterator actual en el desplazamiento especificado.|  
|[VectorIterator::operator\< \(Operador\)](../cppcx/vectoriterator-operator-less-than-operator.md)|Indica si el objeto VectorIterator actual es menor que un objeto VectorIterator especificado.|  
|[VectorIterator::operator\<\= \(Operador\)](../cppcx/vectoriterator-operator-less-than-or-equals-operator.md)|Indica si el objeto VectorIterator actual es menor o igual que un objeto VectorIterator especificado.|  
|[VectorIterator::operator\-\= \(Operador\)](../cppcx/vectoriterator-operator-subtract-assign-operator.md)|Disminuye el VectorIterator actual según el desplazamiento especificado.|  
|[VectorIterator::operator\=\= \(Operador\)](../cppcx/vectoriterator-operator-equality-operator.md)|Indica si el objeto VectorIterator actual es igual que un objeto VectorIterator especificado.|  
|[VectorIterator::operator\> \(Operador\)](../cppcx/vectoriterator-operator-greater-than-operator.md)|Indica si el objeto VectorIterator actual es mayor que un objeto VectorIterator especificado.|  
|[VectorIterator::operator\-\> \(Operador\)](../cppcx/vectoriterator-operator-arrow-operator.md)|Recupera la dirección del elemento al que hace referencia el objeto VectorIterator actual.|  
|[VectorIterator::operator\>\= \(Operador\)](../cppcx/vectoriterator-operator-greater-than-or-equal-operator.md)|Indica si el objeto VectorIterator actual es mayor o igual que el objeto VectorIterator especificado.|  
  
## Jerarquía de herencia  
 `VectorIterator`  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Espacio de nombres de plataforma \(NOTINBUILD\)](http://msdn.microsoft.com/es-es/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)