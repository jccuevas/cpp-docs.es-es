---
title: "ModuleBase (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::ModuleBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ModuleBase (clase)"
ms.assetid: edce7591-6893-46f7-94a7-382827775548
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# ModuleBase (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class ModuleBase;  
```  
  
## <a name="remarks"></a>Comentarios  
 Representa la clase base de la [módulo](../windows/module-class.md) clases.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Constructor Modulebase](../windows/modulebase-modulebase-constructor.md)|Inicializa una instancia de la clase de módulo.|  
|[ModuleBase:: ~ ModuleBase (destructor)](../windows/modulebase-tilde-modulebase-destructor.md)|Deinitializes la instancia actual de la clase de módulo.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Modulebase:: Decrementobjectcount (método)](../Topic/ModuleBase::DecrementObjectCount%20Method.md)|Cuando se implementa, disminuye el número de objetos realizando el seguimiento del módulo.|  
|[Modulebase:: Incrementobjectcount (método)](../windows/modulebase-incrementobjectcount-method.md)|Cuando se implementa, aumenta el número de objetos que se realiza el seguimiento del módulo.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ModuleBase`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de wrl](../windows/microsoft-wrl-details-namespace.md)