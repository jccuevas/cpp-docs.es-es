---
title: "SyncLockWithStatusT (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SyncLockWithStatusT (clase)"
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# SyncLockWithStatusT (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename SyncTraits  
>  
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `SyncTraits`  
 Un tipo que puede tomar exclusivo o compartido posesión de un recurso.  
  
## <a name="remarks"></a>Comentarios  
 Representa un tipo que puede tomar exclusivo o compartido posesión de un recurso.  
  
 SyncLockWithStatusT (clase) se utiliza para implementar el [Mutex](../Topic/Mutex%20Class1.md) y [semáforo](../windows/semaphore-class.md) clases.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Constructor Synclockwithstatust](../Topic/SyncLockWithStatusT::SyncLockWithStatusT%20Constructor.md)|Inicializa una nueva instancia de la clase SyncLockWithStatusT.|  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Constructor Synclockwithstatust](../Topic/SyncLockWithStatusT::SyncLockWithStatusT%20Constructor.md)|Inicializa una nueva instancia de la clase SyncLockWithStatusT.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Synclockwithstatust:: GetStatus (método)](../windows/synclockwithstatust-getstatus-method.md)|Recupera el estado de espera del objeto SyncLockWithStatusT actual.|  
|[Synclockwithstatust:: IsLocked (método)](../windows/synclockwithstatust-islocked-method.md)|Indica si el objeto de SyncLockWithStatusT actual es propietario de un recurso; es decir, el objeto SyncLockWithStatusT *bloqueado*.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Miembro de datos Status_](../windows/synclockwithstatust-status-data-member.md)|Contiene el resultado de subyacente esperar la operación después de una operación de bloqueo en un objeto basado en el objeto de SyncLockWithStatusT actual.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `SyncLockT`  
  
 `SyncLockWithStatusT`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres Wrappers](../windows/microsoft-wrl-wrappers-details-namespace.md)