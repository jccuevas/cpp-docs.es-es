---
title: Clase CHeapPtrBase | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
dev_langs: C++
helpviewer_keywords: CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59520211ae577c4ca4358874ef1d8ff71de59921
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cheapptrbase-class"></a>Clase CHeapPtrBase
Esta clase constituye la base para varias clases de puntero inteligente de montón.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T, class Allocator = CCRTAllocator>  
class CHeapPtrBase
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de objeto que se almacenará en el montón.  
  
 `Allocator`  
 La clase de asignación de memoria utilizada. De forma predeterminada las rutinas de CRT se usan para asignar y liberar memoria.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeapPtrBase:: ~ CHeapPtrBase](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeapPtrBase::AllocateBytes](#allocatebytes)|Llamar a este método para asignar memoria.|  
|[CHeapPtrBase::Attach](#attach)|Llamar a este método para tomar posesión de un puntero existente.|  
|[CHeapPtrBase::Detach](#detach)|Llamar a este método para liberar la propiedad de un puntero.|  
|[CHeapPtrBase::Free](#free)|Llamar a este método para eliminar un objeto al que señala un `CHeapPtrBase`.|  
|[CHeapPtrBase::ReallocateBytes](#reallocatebytes)|Llamar a este método para volver a asignar memoria.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeapPtrBase::operator T *](#operator_t_star)|El operador de conversión.|  
|[CHeapPtrBase::operator &](#operator_amp)|La & (operador).|  
|[CHeapPtrBase::operator ->](#operator_ptr)|El operador de puntero a miembro.|  

  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeapPtrBase::m_pData](#m_pdata)|La variable de miembro de datos de puntero.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase constituye la base para varias clases de puntero inteligente de montón. Las clases derivadas, por ejemplo, [CHeapPtr](../../atl/reference/cheapptr-class.md) y [plantilla CComHeapPtr](../../atl/reference/ccomheapptr-class.md), agregar sus propios constructores y operadores. Vea estas clases para obtener ejemplos de implementación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcore.h  
  
##  <a name="allocatebytes"></a>CHeapPtrBase::AllocateBytes  
 Llamar a este método para asignar memoria.  
  
```
bool AllocateBytes(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nBytes`  
 El número de bytes de memoria para asignar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la memoria está correctamente asignada, false en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 En compilaciones de depuración, se producirá un error de aserción si el [CHeapPtrBase::m_pData](#m_pdata) variable miembro actualmente apunta a un valor existente; es decir, no es igual a NULL.  
  
##  <a name="attach"></a>CHeapPtrBase::Attach  
 Llamar a este método para tomar posesión de un puntero existente.  
  
```
void Attach(T* pData) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pData`  
 La `CHeapPtrBase` objeto tomará posesión de this (puntero).  
  
### <a name="remarks"></a>Comentarios  
 Cuando un `CHeapPtrBase` objeto toma posesión de un puntero, eliminará automáticamente el puntero y los datos asignados cuando sale del ámbito.  
  
 En compilaciones de depuración, se producirá un error de aserción si el [CHeapPtrBase::m_pData](#m_pdata) variable miembro actualmente apunta a un valor existente; es decir, no es igual a NULL.  
  
##  <a name="dtor"></a>CHeapPtrBase:: ~ CHeapPtrBase  
 Destructor.  
  
```
~CHeapPtrBase() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados.  
  
##  <a name="detach"></a>CHeapPtrBase::Detach  
 Llamar a este método para liberar la propiedad de un puntero.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una copia del puntero.  
  
### <a name="remarks"></a>Comentarios  
 Libera la propiedad de un puntero, Establece la [CHeapPtrBase::m_pData](#m_pdata) variable miembro en NULL y devuelve una copia del puntero.  
  
##  <a name="free"></a>CHeapPtrBase::Free  
 Llamar a este método para eliminar un objeto al que señala un `CHeapPtrBase`.  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El objeto señalado por el `CHeapPtrBase` se libera y el [CHeapPtrBase::m_pData](#m_pdata) variable miembro se establece en NULL.  
  
##  <a name="m_pdata"></a>CHeapPtrBase::m_pData  
 La variable de miembro de datos de puntero.  
  
```
T* m_pData;
```  
  
### <a name="remarks"></a>Comentarios  
 Esta variable miembro contiene la información del puntero.  
  
##  <a name="operator_amp"></a>CHeapPtrBase::operator&amp;  
 La & (operador).  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la dirección del objeto que señala el `CHeapPtrBase` objeto.  
  

##  <a name="operator_ptr"></a>CHeapPtrBase::operator-&gt;  

 El operador de puntero a miembro.  
  
```
T* operator->() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la [CHeapPtrBase::m_pData](#m_pdata) variable miembro.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este operador para llamar a un método en una clase que señala el `CHeapPtrBase` objeto. En compilaciones de depuración, se producirá un error de aserción si el `CHeapPtrBase` apunta a NULL.  
  
##  <a name="operator_t_star"></a>CHeapPtrBase::operator T *  
 El operador de conversión.  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Devuelve [CHeapPtrBase::m_pData](#m_pdata).  
  
##  <a name="reallocatebytes"></a>CHeapPtrBase::ReallocateBytes  
 Llamar a este método para volver a asignar memoria.  
  
```
bool ReallocateBytes(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nBytes`  
 La nueva cantidad de memoria para asignar, en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la memoria está correctamente asignada, false en caso contrario.  
  
## <a name="see-also"></a>Vea también  
 [Clase CHeapPtr](../../atl/reference/cheapptr-class.md)   
 [Clase de plantilla CComHeapPtr](../../atl/reference/ccomheapptr-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
