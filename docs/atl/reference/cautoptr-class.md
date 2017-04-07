---
title: Clase CAutoPtr | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 309a3d0ddceab2995c85e156c7db09ddd7edfa86
ms.lasthandoff: 02/24/2017

---
# <a name="cautoptr-class"></a>Clase CAutoPtr
Esta clase representa un objeto de puntero inteligente.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAutoPtr::CAutoPtr](#cautoptr)|El constructor.|  
|[CAutoPtr:: ~ CAutoPtr](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAutoPtr::Attach](#attach)|Llamar a este método para tomar posesión de un puntero existente.|  
|[CAutoPtr::Detach](#detach)|Llamar a este método para liberar la propiedad de un puntero.|  
|[CAutoPtr::Free](#free)|Llamar a este método para eliminar un objeto al que señala un `CAutoPtr`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAutoPtr::operator T *](#operator_t_star)|El operador de conversión.|  
|[CAutoPtr::operator =](#operator_eq)|El operador de asignación.|  
|[CAutoPtr::operator->](#operator_ptr)|El operador de puntero a miembro.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAutoPtr::m_p](#m_p)|La variable de miembro de datos de puntero.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona métodos para crear y administrar un puntero inteligente, que le ayudará a proteger frente a pérdidas de memoria al liberar automáticamente los recursos cuando se encuentra fuera del ámbito.  
  
 Además, `CAutoPtr`del constructor de copias y propiedad de transferencia del operador de asignación del puntero, copia el puntero de origen en el puntero de destino y establecer el puntero de origen en NULL. Por lo tanto, es imposible tener dos `CAutoPtr` objetos entre almacenar el mismo puntero, y esto reduce la posibilidad de eliminar el mismo puntero dos veces.  
  
 `CAutoPtr`También simplifica la creación de colecciones de punteros. En lugar de derivar una clase de colección y reemplazar el destructor, es más fácil crear una colección de `CAutoPtr` objetos. Cuando se elimina la colección, el `CAutoPtr` objetos se salen del ámbito y eliminarse automáticamente.  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md) y variantes funcionan de la misma manera que `CAutoPtr`, excepto en que asignan y liberan memoria utilizando las funciones del montón diferente en lugar de C++ **nueva** y **eliminar** operadores. [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) es similar a `CAutoPtr`, la única diferencia que usa **vector new []** y **vector delete []** para asignar y liberar memoria.  
  
 Consulte también [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) y [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) cuando se necesitan las matrices o listas de punteros inteligentes.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#74;](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]  
  
##  <a name="attach"></a>CAutoPtr::Attach  
 Llamar a este método para tomar posesión de un puntero existente.  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 La `CAutoPtr` objeto tomará posesión de este puntero.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un `CAutoPtr` objeto toma posesión de un puntero, eliminará automáticamente el puntero y los datos asignados cuando sale del ámbito. Si [CAutoPtr::Detach](#detach) es llama, el programador es nuevo dada la responsabilidad para liberar cualquier recursos asignado.  
  
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
 El tipo que se está administrando mediante otro `CAutoPtr`, que se usa para inicializar el objeto actual.  
  
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
 Libera la posesión de un puntero, se establece la [CAutoPtr::m_p](#m_p) variable de miembro de datos en NULL y devuelve una copia del puntero. Después de llamar a **separar**, es hasta el programador para liberarlos recursos asignado que la `CAutoPtr` objeto puede haber supuesto previamente reponsibility.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de la [CAutoPtr Introducción](../../atl/reference/cautoptr-class.md).  
  
##  <a name="free"></a>CAutoPtr::Free  
 Llamar a este método para eliminar un objeto al que señala un `CAutoPtr`.  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El objeto al que apunta el `CAutoPtr` se liberan y el [CAutoPtr::m_p](#m_p) variable de miembro de datos se establece en NULL.  
  
##  <a name="m_p"></a>CAutoPtr::m_p  
 La variable de miembro de datos de puntero.  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>Comentarios  
 Esta variable miembro contiene la información de puntero.  
  
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
 El operador de asignación se separa la `CAutoPtr` objeto desde el puntero actual y se asocia el nuevo puntero, `p`, en su lugar.  
  
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
 Utilice este operador para llamar a un método en una clase que apunta la `CAutoPtr` objeto. En compilaciones de depuración, se producirá un error de aserción si el `CAutoPtr` apunta a NULL.  
  
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
 [Información general de la clase](../../atl/atl-class-overview.md)

