---
title: InterfaceTraits (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
dev_langs:
- C++
helpviewer_keywords:
- InterfaceTraits structure
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c28c7c1eef2fc278a0667ec4b7c635005331467
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="interfacetraits-structure"></a>InterfaceTraits (estructura)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<  
   typename I0  
>  
struct __declspec(novtable) InterfaceTraits;  
template<  
   typename CloakedType  
>  
struct __declspec(novtable) InterfaceTraits<CloakedIid<CloakedType>>;  
  
template<>  
struct __declspec(novtable) InterfaceTraits<Nil>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `I0`  
 El nombre de una interfaz.  
  
 `CloakedType`  
 Para RuntimeClass, Implements y ChainInterfaces, una interfaz que no esté en la lista de admite identificadores de interfaz.  
  
## <a name="remarks"></a>Comentarios  
 Características comunes de implementa de una interfaz.  
  
 La segunda plantilla es una especialización para interfaces escondidos. La tercera plantilla es una especialización para parámetros nulo.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`Base`|Sinónimo del parámetro de la plantilla `I0`|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[InterfaceTraits::CanCastTo (método)](../windows/interfacetraits-cancastto-method.md)|Indica si el puntero especificado se puede convertir en un puntero a `Base`.|  
|[InterfaceTraits::CastToBase (método)](../windows/interfacetraits-casttobase-method.md)|Convierte el puntero especificado a un puntero a `Base`.|  
|[InterfaceTraits::CastToUnknown (método)](../windows/interfacetraits-casttounknown-method.md)|Convierte el puntero especificado a un puntero a IUnknown.|  
|[InterfaceTraits::FillArrayWithIid (método)](../windows/interfacetraits-fillarraywithiid-method.md)|Asigna el identificador de interfaz de `Base` al elemento de matriz especificado por el argumento de índice.|  
|[InterfaceTraits::Verify (método)](../windows/interfacetraits-verify-method.md)|Comprueba que Base se deriva correctamente.|  
  
### <a name="public-constants"></a>Constantes públicas  
  
|nombre|Descripción|  
|----------|-----------------|  
|[InterfaceTraits::IidCount (constante)](../windows/interfacetraits-iidcount-constant.md)|Contiene el número de identificadores asociados con el objeto de InterfaceTraits actual de interfaz.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `InterfaceTraits`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)