---
title: "TerminateMap (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::TerminateMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TerminateMap (función)"
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# TerminateMap (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
inline bool TerminateMap(  
   _In_ ModuleBase *module,   
   _In_opt_z_ const wchar_t *serverName,   
    bool forceTerminate) throw()  
```  
  
## <a name="parameters"></a>Parámetros  
 `module`  
 Un [módulo](../windows/module-class.md).  
  
 `serverName`  
 El nombre de un subconjunto de los generadores de clases en el módulo especificado por el parámetro `module`.  
  
 `forceTerminate`  
 `true` para finalizar la clase generadores independientemente de estén activas; `false` no finalice los generadores de clases si cualquier fábrica está activo.  
  
## <a name="return-value"></a>Valor devuelto  
 `true` Si se han terminado todos los generadores de clases; de lo contrario, `false`.  
  
## <a name="remarks"></a>Comentarios  
 Cierra los generadores de clases en el módulo especificado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de wrl](../windows/microsoft-wrl-details-namespace.md)