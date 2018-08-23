---
title: Backinsertiterator (clase) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
dev_langs:
- C++
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c0678dbb78aaa115c0c4f3120a8bc0d74bf1c65
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612629"
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Platform::Collections::BackInsertIterator (Clase)
Representa un iterador que inserta, en lugar de sobrescribir, elementos en el back-end de una colección secuencial.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <typename T>  
class BackInsertIterator : 
public ::std::iterator<::std::output_iterator_tag, void, void, void, void>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de elemento de la colección actual.  
  
### <a name="remarks"></a>Comentarios  
 La clase BackInsertIterator implementa las reglas requeridas por [back_insert_iterator Class](../standard-library/back-insert-iterator-class.md).  
  
### <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Backinsertiterator](#ctor)|Inicializa una nueva instancia de la clase BackInsertIterator.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[BackInsertIterator::operator* (Operador)](#operator-dereference)|Recupera una referencia al objeto BackInsertIterator actual.|  
|[BackInsertIterator::operator++ (Operador)](#operator-increment)|Devuelve una referencia al objeto BackInsertIterator actual. El iterador no se modifica.|  
|[BackInsertIterator::operator= (Operador)](#operator-assign)|Anexa el objeto especificado al final de la colección secuencial actual.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `BackInsertIterator`  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
---
## <a name="ctor"></a>  Constructor Backinsertiterator
Inicializa una nueva instancia de la clase `BackInsertIterator`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
explicit BackInsertIterator(  
   Windows::Foundation::Collections::IVector<T>^ v);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `v`  
 Un IVector\<T > objeto.  
  
### <a name="remarks"></a>Comentarios  
 Un objeto `BackInsertIterator` inserta elementos a continuación del último elemento del objeto especificado por el parámetro `v`.  
 
## <a name="operator-assign"></a>  Backinsertiterator:: operator = (operador)
Anexa el objeto especificado al final de la colección secuencial actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```    
BackInsertIterator& operator=( const T& t);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `t`  
 El objeto que se va a anexar a la colección actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto BackInsertIterator actual.  

## <a name="operator-dereference"></a>  Operador de backinsertiterator:: operator
Recupera una referencia al objeto BackInsertIterator actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
BackInsertIterator& operator*();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto BackInsertIterator actual.  
  
### <a name="remarks"></a>Comentarios  
 Este operador devuelve una referencia al objeto BackInsertIterator actual, no así a ningún elemento de la colección actual.  
 
## <a name="operator-increment"></a>  Backinsertiterator:: operator ++ (operador)
Devuelve una referencia al objeto BackInsertIterator actual. El iterador no se modifica.  
  
## <a name="syntax"></a>Sintaxis  
  
``` 
  
BackInsertIterator& operator++();  
  
BackInsertIterator operator++(int);  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto BackInsertIterator actual.  
  
### <a name="remarks"></a>Comentarios  
 Por diseño, el primero ejemplo de sintaxis incrementa previamente el objeto BackInsertIterator actual y el segundo lo incrementa posteriormente. El tipo `int` de la segunda sintaxis indica una operación de incremento posterior, no un operando entero real.  
  
 Sin embargo, este operador no modifica realmente el objeto BackInsertIterator. En su lugar, este operador devuelve una referencia al iterador actual sin modificar. Este es el mismo comportamiento que [operador *](#dereference-operator).  
  
  
## <a name="see-also"></a>Vea también  
 [Plataforma Namespace](platform-namespace-c-cx.md)