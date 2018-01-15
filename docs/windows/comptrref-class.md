---
title: ComPtrRef (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::Details::ComPtrRef
dev_langs: C++
helpviewer_keywords: ComPtrRef class
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9b1bbe134f15fdba6863f1725cbcc7effcb6d94f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="comptrref-class"></a>ComPtrRef (clase)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename T  
>  
class ComPtrRef : public ComPtrRefBase<T>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 A [ComPtr\<T >](../windows/comptr-class.md) tipo o un tipo derivado de él, no solo la interfaz representada por la clase ComPtr.  
  
## <a name="remarks"></a>Comentarios  
 Representa una referencia a un objeto de tipo ComPtr\<T >.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ComPtrRef::ComPtrRef (constructor)](../windows/comptrref-comptrref-constructor.md)|Inicializa una nueva instancia de la clase ComPtrRef desde el puntero especificado que apunta a otro objeto ComPtrRef.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ComPtrRef::GetAddressOf (método)](../windows/comptrref-getaddressof-method.md)|Recupera la dirección de un puntero a la interfaz representada por el objeto ComPtrRef actual.|  
|[ComPtrRef::ReleaseAndGetAddressOf (método)](../windows/comptrref-releaseandgetaddressof-method.md)|Elimina el objeto ComPtrRef actual y devuelve un puntero a un-puntero a la interfaz que se ha representado por el objeto ComPtrRef.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ComPtrRef::operator InterfaceType** (operador)](../windows/comptrref-operator-interfacetype-star-star-operator.md)|Elimina el objeto ComPtrRef actual y devuelve un puntero a un-puntero a la interfaz que se ha representado por el objeto ComPtrRef.|  
|[ComPtrRef::operator T* (operador)](../windows/comptrref-operator-t-star-operator.md)|Devuelve el valor de la [ptr_](../windows/comptrrefbase-ptr-data-member.md) miembro de datos del objeto ComPtrRef actual.|  
|[ComPtrRef::operator void** (operador)](../windows/comptrref-operator-void-star-star-operator.md)|Elimina el objeto ComPtrRef actual, convierte el puntero a la interfaz que se ha representado por el objeto ComPtrRef como un puntero-a-puntero-to `void`y, a continuación, devuelve el puntero de conversión.|  
|[ComPtrRef::operator* (operador)](../windows/comptrref-operator-star-operator.md)|Recupera el puntero a la interfaz representada por el objeto ComPtrRef actual.|  
|[ComPtrRef::operator== (operador)](../windows/comptrref-operator-equality-operator.md)|Indica si dos objetos ComPtrRef son iguales.|  
|[ComPtrRef::operator!= (operador)](../windows/comptrref-operator-inequality-operator.md)|Indica si dos objetos ComPtrRef no son iguales.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ComPtrRefBase`  
  
 `ComPtrRef`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)