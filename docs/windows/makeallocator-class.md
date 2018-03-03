---
title: MakeAllocator (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
dev_langs:
- C++
helpviewer_keywords:
- MakeAllocator class
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 523bcdb17fc0a1b74fe615e5ff15a6fcef99cc32
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="makeallocator-class"></a>MakeAllocator (clase)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
template<  
   typename T,  
   bool hasWeakReferenceSupport =   
         !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,   
   T)> , T)> class MakeAllocator;  
  
template<  
   typename T  
>  
class MakeAllocator<T, false>;  
  
template<  
   typename T  
>  
class MakeAllocator<T, true>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Nombre de tipo.  
  
 `hasWeakReferenceSupport`  
 `true`asignar memoria para un objeto que admite referencias débiles; `false` asignar memoria para un objeto que no es compatible con referencias débiles.  
  
## <a name="remarks"></a>Comentarios  
 Asigna memoria para una clase activable, con o sin compatibilidad con la referencia débil.  
  
 Reemplace la clase MakeAllocator para implementar un modelo de asignación de memoria definido por el usuario.  
  
 MakeAllocator normalmente se utiliza para evitar pérdidas de memoria si un objeto que se produce durante la construcción.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[MakeAllocator::MakeAllocator (constructor)](../windows/makeallocator-makeallocator-constructor.md)|Inicializa una nueva instancia de la clase MakeAllocator.|  
|[MakeAllocator::~MakeAllocator (destructor)](../windows/makeallocator-tilde-makeallocator-destructor.md)|Desinicializa la instancia actual de la clase MakeAllocator.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[MakeAllocator::Allocate (método)](../windows/makeallocator-allocate-method.md)|Asigna memoria y lo asocia con el objeto de MakeAllocator actual.|  
|[MakeAllocator::Detach (método)](../windows/makeallocator-detach-method.md)|Desasocia la memoria asignada por el [Allocate](../windows/makeallocator-allocate-method.md) método MakeAllocator del objeto actual.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `MakeAllocator`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)