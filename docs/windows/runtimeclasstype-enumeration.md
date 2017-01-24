---
title: "RuntimeClassType (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::RuntimeClassType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RuntimeClassType (enumeración)"
ms.assetid: d380712d-672e-4ea9-b7c5-cf9fa7dbb770
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClassType (Enumeraci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica el tipo de instancia de [RuntimeClass](../windows/runtimeclass-class.md) se admite que.  
  
## Sintaxis  
  
```  
enum RuntimeClassType;  
```  
  
## Miembros  
  
### Valores  
  
|Name|Descripción|  
|----------|-----------------|  
|`ClassicCom`|Una clase COM clásica en tiempo de ejecución.|  
|`Delegate`|Equivalente a **ClassicCom**.|  
|`InhibitFtmBase`|Deshabilita `FtmBase` admiten mientras `__WRL_CONFIGURATION_LEGACY__` no está definido.|  
|`InhibitWeakReference`|Deshabilita la compatibilidad parcial de referencia.|  
|`WinRt`|Clase [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].|  
|`WinRtClassicComMix`|Combinación de `WinRt` y `ClassicCom`.|  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)