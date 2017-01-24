---
title: "Registry and TypeLib Global Functions | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RegistryDataExchange function, funciones globales"
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Registry and TypeLib Global Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Estas funciones proporcionan compatibilidad para cargar y registrar una biblioteca de tipos.  
  
> [!IMPORTANT]
>  Las funciones enumeradas en las tablas siguientes no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
|||  
|-|-|  
|[AtlRegisterTypeLib](../Topic/AtlRegisterTypeLib.md)|esta función se denomina para registrar una biblioteca de tipos.|  
|[AtlUnRegisterTypeLib](../Topic/AtlUnRegisterTypeLib.md)|Esta función se denomina anular el registro de una biblioteca de tipos|  
|[AtlLoadTypeLib](../Topic/AtlLoadTypeLib.md)|esta función se denomina para cargar una biblioteca de tipos.|  
|[AtlUpdateRegistryFromResourceD](../Topic/AtlUpdateRegistryFromResourceD.md)|Esta función se denomina para actualizar el registro de recurso proporcionado.|  
|[RegistryDataExchange](../Topic/RegistryDataExchange.md)|Esta función se denomina para leer de, o escriba, el sistema.  Llamado por [Macros de intercambio de datos del registro](../../atl/reference/registry-data-exchange-macros.md).|  
  
 Control de estas funciones que el nodo en el registro el programa utiliza para almacenar información.  
  
|||  
|-|-|  
|[AtlGetPerUserRegistration](../Topic/AtlGetPerUserRegistration.md)|Recupera si la aplicación redirige el acceso del registro en el nodo de **HKEY\_CURRENT\_USER** \(**HKCU**\).|  
|[AtlSetPerUserRegistration](../Topic/AtlSetPerUserRegistration.md)|Establece si la aplicación redirige el acceso del registro en el nodo de **HKEY\_CURRENT\_USER** \(**HKCU**\).|  
  
## Vea también  
 [Funciones](../../atl/reference/atl-functions.md)