---
title: Clase CAutoPtr | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
dev_langs: C++
helpviewer_keywords: CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2b8ded7bbf4dbe4e4f2ada7054cebab996934316
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cautoptr-class"></a>Clase CAutoPtr
Esta clase representa un objeto de puntero inteligente.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename T>  
class CAutoPtr
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de puntero.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoPtr::CAutoPtr](#cautoptr)|El constructor.|  
|[CAutoPtr:: ~ CAutoPtr](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoPtr::Attach](#attach)|Llamar a este método para tomar posesión de un puntero existente.|  
|[CAutoPtr::Detach](#detach)|Llamar a este método para liberar la propiedad de un puntero.|  
|[CAutoPtr::Free](#free)|Llamar a este método para eliminar un objeto al que señala un `CAutoPtr`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoPtr::operator T *](#operator_t_star)|El operador de conversión.|  
|[CAutoPtr::operator =](#operator_eq)|El operador de asignación.|  
|[CAutoPtr::operator ->](#operator_ptr)|El operador de puntero a miembro.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoPtr::m_p](#m_p)|La variable de miembro de datos de puntero.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos para crear y administrar un puntero inteligente, que le ayudará a protegerse frente a pérdidas de memoria mediante liberar automáticamente los recursos cuando se encuentra fuera del ámbito.  
  
 Además, `CAutoPtr`del constructor de copias y la propiedad de transferencia del operador de asignación del puntero, copia el puntero de origen en el puntero de destino y establecer el puntero de origen en NULL. Por lo tanto, es posible tener dos `CAutoPtr` objetos entre almacenar el mismo puntero, y esto reduce la posibilidad de eliminar el mismo puntero dos veces.  
  
 `CAutoPtr`También simplifica la creación de colecciones de punteros. En lugar de derivar una clase de colección y reemplazar el destructor, resulta más sencillo de crear una colección de `CAutoPtr` objetos. Cuando se elimina la colección, el `CAutoPtr` objetos se salen del ámbito y se eliminará automáticamente por sí mismos.  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md) y variantes de trabajo de la misma manera que `CAutoPtr`, excepto en que asignan y liberan memoria utilizando las funciones del montón diferente en lugar de C++ **nueva** y **eliminar** operadores. [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) es similar a `CAutoPtr`, la única diferencia consiste en que usa **vector new []** y **vector delete []** para asignar y liberar memoria.  
  
 Vea también [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) y [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) cuando se requieren matrices o listas de punteros inteligentes.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]  
  
##  <a name="attach"></a>CAutoPtr::Attach  
 Llamar a este método para tomar posesión de un puntero existente.  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 La `CAutoPtr` objeto tomará posesión de this (puntero).  
  
### <a name="remarks"></a>Comentarios  
 Cuando un `CAutoPtr` objeto toma posesión de un puntero, eliminará automáticamente el puntero y los datos asignados cuando sale del ámbito. Si [CAutoPtr::Detach](#detach) es llama, el programador se nuevo especificado responsabilidad para liberar cualquier asigna recursos.  
  
 En compilaciones de depuración, se producirá un error de aserción si el [CAutoPtr::m_p](#m_p) miembro de datos actualmente apunta a un valor existente; es decir, no es igual a NULL.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de la [CAutoPtr Introducción](../../atl/reference/cautoptr-class.md).  
  
##  <a name="cautoptr"></a>CAutoPtr::CAutoPtr  
 El constructor.  
  
```
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<> 
CAutoPtr(CAutoPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Un puntero existente.  
  
 `TSrc`  
 El tipo que se va a código administrado por otro `CAutoPtr`, que se usa para inicializar el objeto actual.  
  
### <a name="remarks"></a>Comentarios  
 El `CAutoPtr` se puede crear el objeto mediante un puntero existente, en cuyo caso transfiere la propiedad del puntero.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de la [CAutoPtr Introducción](../../atl/reference/cautoptr-class.md).  
  
##  <a name="dtor"></a>CAutoPtr:: ~ CAutoPtr  
 Destructor.  
  
```
~CAutoPtr() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera los recursos asignados. Llamadas [CAutoPtr::Free](#free).  
  
##  <a name="detach"></a>CAutoPtr::Detach  
 Llamar a este método para liberar la propiedad de un puntero.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una copia del puntero.  
  
### <a name="remarks"></a>Comentarios  
 Libera la propiedad de un puntero, Establece la [CAutoPtr::m_p](#m_p) variable de miembro de datos con valores NULL y devuelve una copia del puntero. Después de llamar a **separar**, es hasta el programador para liberarlos recursos asignado en el cual el `CAutoPtr` objeto puede haber supuesto previamente reponsibility.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de la [CAutoPtr Introducción](../../atl/reference/cautoptr-class.md).  
  
##  <a name="free"></a>CAutoPtr::Free  
 Llamar a este método para eliminar un objeto al que señala un `CAutoPtr`.  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El objeto señalado por el `CAutoPtr` se libera y el [CAutoPtr::m_p](#m_p) variable de miembro de datos se establece en NULL.  
  
##  <a name="m_p"></a>CAutoPtr::m_p  
 La variable de miembro de datos de puntero.  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>Comentarios  
 Esta variable miembro contiene la información del puntero.  
  
##  <a name="operator_eq"></a>CAutoPtr::operator =  
 El operador de asignación.  
  
```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Un puntero.  
  
 `TSrc`  
 Un tipo de clase.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia a un **CAutoPtr\< T >**.  
  
### <a name="remarks"></a>Comentarios  
 El operador de asignación se separa la `CAutoPtr` objeto de cualquier puntero actual y asocia el nuevo puntero `p`, en su lugar.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de la [CAutoPtr Introducción](../../atl/reference/cautoptr-class.md).  
  
##  <a name="operator_ptr"></a>CAutoPtr::operator-&gt;  
 El operador de puntero a miembro.  
  
```
T* operator->() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la [CAutoPtr::m_p](#m_p) variable de miembro de datos.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este operador para llamar a un método en una clase que señala el `CAutoPtr` objeto. En compilaciones de depuración, se producirá un error de aserción si el `CAutoPtr` apunta a NULL.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de la [CAutoPtr Introducción](../../atl/reference/cautoptr-class.md).  
  
##  <a name="operator_t_star"></a>CAutoPtr::operator T *  
 El operador de conversión.  
  
```  
operator T* () const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero al tipo de datos de objeto definido en la plantilla de clase.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de la [CAutoPtr Introducción](../../atl/reference/cautoptr-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Clase CHeapPtr](../../atl/reference/cheapptr-class.md)   
 [Clase CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
