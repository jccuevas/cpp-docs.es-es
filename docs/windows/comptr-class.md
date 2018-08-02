---
title: ComPtr (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr class
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 21503e38bb612f935e26f6eaaa93df2097e10445
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465342"
---
# <a name="comptr-class"></a>ComPtr (clase)
Crea un tipo de *puntero inteligente* que representa la interfaz especificada por el parámetro de plantilla. **ComPtr** automáticamente mantiene un recuento de referencias para el puntero de interfaz subyacente y libera la interfaz cuando el recuento de referencias llega a cero.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <typename T>  
class ComPtr;  
  
template<class T>  
friend class ComPtr;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *T*  
 La interfaz que el **ComPtr** representa.  
  
 *U*  
 Una clase a la que el actual **ComPtr** es de confianza. (La plantilla que usa este parámetro está protegida).  
  
## <a name="remarks"></a>Comentarios  
 `ComPtr<>` declara un tipo que representa el puntero de interfaz subyacente. Usar `ComPtr<>` para declarar una variable y, a continuación, utilice el operador de acceso a miembros de flecha (`->`) para tener acceso a una función miembro de interfaz.  
  
 Para obtener más información sobre los punteros inteligentes, consulte la subsección "Punteros inteligentes de COM" de la [COM Coding Practices](http://msdn.microsoft.com/76aca556-b4d6-4e67-a2a3-4439900f0c39)tema en MSDN Library.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`InterfaceType`|Un sinónimo del tipo especificado por el *T* parámetro de plantilla.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ComPtr::ComPtr (constructor)](../windows/comptr-comptr-constructor.md)|Inicializa una nueva instancia de la **ComPtr** clase. Las sobrecargas proporcionan constructores predeterminados, así como de copia, movimiento y conversión.|  
|[ComPtr::~ComPtr (destructor)](../windows/comptr-tilde-comptr-destructor.md)|Desinicializa una instancia de **ComPtr**.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ComPtr::As (método)](../windows/comptr-as-method.md)|Devuelve un **ComPtr** objeto que representa la interfaz identificada por el parámetro de plantilla especificado.|  
|[ComPtr::AsIID (método)](../windows/comptr-asiid-method.md)|Devuelve un **ComPtr** objeto que representa la interfaz identificada por el identificador de interfaz especificado.|  
|[ComPtr::AsWeak (método)](../windows/comptr-asweak-method.md)|Recupera una referencia débil al objeto actual.|  
|[ComPtr::Attach (método)](../windows/comptr-attach-method.md)|Esto asocia **ComPtr** con el tipo de interfaz especificado por el parámetro de tipo de plantilla actual.|  
|[ComPtr::CopyTo (método)](../windows/comptr-copyto-method.md)|Copia de la interfaz actual o especificada asociada a este **ComPtr** al puntero de salida especificado.|  
|[ComPtr::Detach (método)](../windows/comptr-detach-method.md)|Desasocia esta **ComPtr** desde la interfaz que representa.|  
|[ComPtr::Get (método)](../windows/comptr-get-method.md)|Recupera un puntero a la interfaz que está asociado a este **ComPtr**.|  
|[ComPtr::GetAddressOf (método)](../windows/comptr-getaddressof-method.md)|Recupera la dirección de la [ptr_](../windows/comptr-ptr-data-member.md) miembro de datos que contiene un puntero a la interfaz representada por este **ComPtr**.|  
|[ComPtr::ReleaseAndGetAddressOf (método)](../windows/comptr-releaseandgetaddressof-method.md)|Libera la interfaz asociada a este **ComPtr** y, a continuación, recupera la dirección de la [ptr_](../windows/comptr-ptr-data-member.md) miembro de datos que contiene un puntero a la interfaz que se publicó.|  
|[ComPtr::Reset](../windows/comptr-reset.md)|Libera todas las referencias del puntero a la interfaz que está asociado a este **ComPtr**.|  
|[ComPtr::Swap (método)](../windows/comptr-swap-method.md)|Intercambia la interfaz administrada por el actual **ComPtr** con la interfaz administrada por especificado **ComPtr**.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ComPtr::InternalAddRef (método)](../windows/comptr-internaladdref-method.md)|Incrementa el recuento de referencias de la interfaz asociada a este **ComPtr**.|  
|[ComPtr::InternalRelease (método)](../windows/comptr-internalrelease-method.md)|Realiza una operación de liberación de COM en la interfaz asociada a este **ComPtr**.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ComPtr::operator Microsoft::WRL::Details::BoolType (operador)](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)|Indica si un **ComPtr** administra la duración del objeto de una interfaz.|  
|[ComPtr::operator& (operador)](../windows/comptr-operator-ampersand-operator.md)|Recupera la dirección del elemento actual **ComPtr**.|  
|[ComPtr::operator= (operador)](../windows/comptr-operator-assign-operator.md)|Asigna un valor a la actual **ComPtr**.|  
|[ComPtr::operator-> (operador)](../windows/comptr-operator-arrow-operator.md)|Recupera un puntero al tipo especificado por el parámetro de plantilla actual.|  
|[ComPtr::operator== (operador)](../windows/comptr-operator-equality-operator.md)|Indica si dos **ComPtr** objetos son iguales.|  
|[ComPtr::operator!= (operador)](../windows/comptr-operator-inequality-operator.md)|Indica si dos **ComPtr** objetos no son iguales.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[ComPtr::ptr_ (miembro de datos)](../windows/comptr-ptr-data-member.md)|Contiene un puntero a la interfaz que está asociado y administrado por este **ComPtr**.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ComPtr`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)