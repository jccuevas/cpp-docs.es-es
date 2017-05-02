---
title: "Platform::Collections::VectorViewIterator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator (Clase)"
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# Platform::Collections::VectorViewIterator (Clase)
Ofrece un iterador de la Biblioteca de plantillas estándar para los objetos derivados de la interfaz [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] de `IVectorView`.  
  
 `ViewVectorIterator` es un iterador de proxy que almacena los elementos de tipo `VectorProxy<T>`. Sin embargo, el objeto proxy casi nunca está visible en el código del usuario. Para obtener más información, consulta [Colecciones \(C\+\+\/CX\)](../cppcx/collections-c-cx.md).  
  
## Sintaxis  
  
```  
template <  
   typename T  
>  
class VectorViewIterator;  
```  
  
#### Parámetros  
 `T`  
 El typename de la clase de plantilla VectorViewIterator.  
  
## Miembros  
  
### Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|------------|-----------------|  
|`difference_type`|Una diferencia de puntero \(ptrdiff\_t\).|  
|`iterator_category`|La categoría de un iterador de acceso aleatorio \(::std::random\_access\_iterator\_tag\).|  
|`pointer`|Un puntero a un tipo interno necesario para la implementación de VectorViewIterator.|  
|`reference`|Una referencia a un tipo interno necesario para la implementación de VectorViewIterator.|  
|`value_type`|El typename `T`.|  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[VectorViewIterator::VectorViewIterator \(Constructor\)](../cppcx/vectorviewiterator-vectorviewiterator-constructor.md)|Inicializa una nueva instancia de la clase VectorViewIterator.|  
  
### Operadores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[VectorViewIterator::operator\- \(Operador\)](../cppcx/vectorviewiterator-operator-minus-operator.md)|Resta un número especificado de elementos del iterador actual produciendo un nuevo iterador, o un iterador especificado del iterador actual produciendo el número de elementos entre los iteradores.|  
|[VectorViewIterator::operator\-\- \(Operador\)](../cppcx/vectorviewiterator-operator-decrement-operator.md)|Disminuye el objeto VectorViewIterator actual.|  
|[VectorViewIterator::operator\!\= \(Operador\)](../cppcx/vectorviewiterator-operator-inequality-operator.md)|Indica si el objeto VectorViewIterator actual no es igual que un objeto VectorViewIterator especificado.|  
|[VectorViewIterator::operator\* \(Operador\)](../cppcx/vectorviewiterator-operator-dereference-operator.md)|Recupera una referencia al elemento especificado por el objeto VectorViewIterator actual.|  
|[VectorViewIterator::operatorOperator](../cppcx/vectorviewiterator-operatoroperator.md)|Recupera una referencia al elemento que es un desplazamiento especificado del objeto VectorViewIterator actual.|  
|[VectorViewIterator::operator\+ \(Operador\)](../cppcx/vectorviewiterator-operator-plus-operator.md)|Devuelve un objeto VectorViewIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorViewIterator especificado.|  
|[VectorViewIterator::operator\+\+ \(Operador\)](../cppcx/vectorviewiterator-operator-increment-operator.md)|Incrementa el objeto VectorViewIterator actual.|  
|[VectorViewIterator::operator\+\= \(Operador\)](../cppcx/vectorviewiterator-operator-plus-assign-operator.md)|Incrementa el VectorViewIterator actual según el desplazamiento especificado.|  
|[VectorViewIterator::operator\< \(Operador\)](../cppcx/vectorviewiterator-operator-less-than-operator.md)|Indica si el objeto VectorViewIterator actual es menor que un objeto VectorViewIterator especificado.|  
|[VectorViewIterator::operator\<\= \(Operador\)](../cppcx/vectorviewiterator-operator-less-than-or-equals-operator.md)|Indica si el objeto VectorViewIterator actual es menor o igual que un objeto VectorViewIterator especificado.|  
|[VectorViewIterator::operator\-\= \(Operador\)](../cppcx/vectorviewiterator-operator-subtract-assign-operator.md)|Disminuye el objeto VectorViewIterator actual según el desplazamiento especificado.|  
|[VectorViewIterator::operator\=\= \(Operador\)](../cppcx/vectorviewiterator-operator-equality-operator.md)|Indica si el objeto VectorViewIterator actual es igual que un objeto VectorViewIterator especificado.|  
|[VectorViewIterator::operator\> \(Operador\)](../cppcx/vectorviewiterator-operator-greater-than-operator.md)|Indica si el objeto VectorViewIterator actual es mayor que un objeto VectorViewIterator especificado.|  
|[VectorViewIterator::operator\-\> \(Operador\)](../cppcx/vectorviewiterator-operator-arrow-operator.md)|Recupera la dirección del elemento al que hace referencia el objeto VectorViewIterator actual.|  
|[VectorViewIterator::operator\>\= \(Operador\)](../cppcx/vectorviewiterator-operator-greater-than-or-equals-operator.md)|Indica si el objeto VectorViewIterator actual es mayor o igual que un objeto VectorViewIterator especificado.|  
  
## Jerarquía de herencia  
 `VectorViewIterator`  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Espacio de nombres de plataforma \(NOTINBUILD\)](http://msdn.microsoft.com/es-es/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)