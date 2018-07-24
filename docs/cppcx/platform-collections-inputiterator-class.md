---
title: Inputiterator (clase) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
dev_langs:
- C++
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fbd80f649b27bcb3af720871d6d1378f5fe220c8
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208489"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections::InputIterator (Clase)
Proporciona un InputIterator de la biblioteca de plantillas estándar para las colecciones que derivan el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <typename X>  
class InputIterator;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `X`  
 El typename de la clase de plantilla InputIterator.  
  
### <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`difference_type`|Una diferencia de puntero (ptrdiff_t).|  
|`iterator_category`|La categoría de un iterador de entrada (::std::input_iterator_tag).|  
|`pointer`|Puntero a `const X`|  
|`reference`|Referencia a `const X`|  
|`value_type`|El typename `X` .|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Inputiterator](#ctor)|Inicializa una nueva instancia de la clase InputIterator.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[InputIterator::operator!= (Operador)](#operator-inequality)|Indica si el objeto InputIterator actual no es igual a un objeto InputIterator especificado.|  
|[InputIterator::operator* (Operador)](#operator-decrement)|Recupera una referencia al elemento especificado por el objeto InputIterator actual.|  
|[InputIterator::operator++ (Operador)](#operator-increment)|Incrementa el objeto InputIterator actual.|  
|[InputIterator::operator== (Operador)](#operator-equality)|Indica si el objeto InputIterator actual es igual que un objeto InputIterator especificado.|  
|[InputIterator::operator-> (Operador)](#operator-arrow)|Recupera la dirección del elemento al que hace referencia el objeto InputIterator actual.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `InputIterator`  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  

## <a name="ctor"></a>  Constructor Inputiterator
Inicializa una nueva instancia de la clase InputIterator.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
InputIterator();  
explicit InputIterator(Windows::Foundation::Collections<X>^ iter);  
```  
  
### <a name="parameters"></a>Parámetros  
 `iter`  
 Objeto de iterador.  
  


## <a name="operator-arrow"></a>  Inputiterator:: operator -&gt; operador
Recupera la dirección del elemento especificado por el objeto InputIterator actual.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
pointer operator->() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Dirección del elemento especificado por el objeto InputIterator actual.  
  


## <a name="operator-dereference"></a>  Inputiterator:: operator\* operador
Recupera una referencia al elemento especificado por el objeto InputIterator actual.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
reference operator*() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El elemento especificado por el objeto InputIterator actual.  
  


## <a name="operator-equality"></a>  Inputiterator:: operator == (operador)
Indica si el objeto InputIterator actual es igual que un objeto InputIterator especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool operator== (const InputIterator& other) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `other`  
 Otro objeto InputIterator.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si el objeto InputIterator actual es igual que `other`; en caso contrario, `false`.  
  


## <a name="operator-increment"></a>  Inputiterator:: operator ++ (operador)
Incrementa el objeto InputIterator actual.  
  
### <a name="syntax"></a>Sintaxis  
  
```    
InputIterator& operator++();   
InputIterator operator++(int);  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La primera sintaxis incrementa y devuelve después el objeto InputIterator actual. La segunda sintaxis devuelve una copia del objeto InputIterator actual e incrementa después el objeto InputIterator actual.  
  
### <a name="remarks"></a>Comentarios  
 Lo primera sintaxis de InputIterator incrementa previamente el objeto InputIterator actual.  
  
 La segunda sintaxis incrementa posteriormente el objeto InputIterator actual. El tipo `int` de la segunda sintaxis indica una operación de incremento posterior, no un operando entero real.  
  


## <a name="operator-inequality"></a>  Inputiterator:: operator! = (operador)
Indica si el objeto InputIterator actual no es igual a un objeto InputIterator especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool operator!=(const InputIterator& other) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `other`  
 Otro objeto InputIterator.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si el objeto InputIterator actual no es igual a `other`; en caso contrario, `false`.   

  
## <a name="see-also"></a>Vea también  
 [Plataforma Namespace](platform-namespace-c-cx.md)