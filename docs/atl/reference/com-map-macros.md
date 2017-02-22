---
title: "COM Map Macros | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interfaces COM, COM map macros"
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# COM Map Macros
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Estas macros definen mapas de interfaz COM.  
  
|||  
|-|-|  
|[BEGIN\_COM\_MAP](../Topic/BEGIN_COM_MAP.md)|Marca el principio de las entradas de asignación de interfaz COM.|  
|[COM\_INTERFACE\_ENTRY](../Topic/COM_INTERFACE_ENTRY%20Macros.md)|Interfaces de las ENTRAR en el mapa de interfaz COM.|  
|[COM\_INTERFACE\_ENTRY2](../Topic/COM_INTERFACE_ENTRY2.md)|Use esta macro para eliminar la ambigüedad de dos bifurcaciones de herencia.|  
|[COM\_INTERFACE\_ENTRY\_IID](../Topic/COM_INTERFACE_ENTRY_IID.md)|Use esta macro para escribir la interfaz en el mapa COM y especificar su identificador IID.|  
|[COM\_INTERFACE\_ENTRY2\_IID](../Topic/COM_INTERFACE_ENTRY2_IID.md)|Igual que [COM\_INTERFACE\_ENTRY2](../Topic/COM_INTERFACE_ENTRY2.md), a menos que puede especificar otro identificador IID.|  
|[COM\_INTERFACE\_ENTRY\_AGGREGATE](../Topic/COM_INTERFACE_ENTRY_AGGREGATE.md)|Cuando la interfaz identificada por `iid` se consulta para, `COM_INTERFACE_ENTRY_AGGREGATE` reenvía a `punk`.|  
|[COM\_INTERFACE\_ENTRY\_AGGREGATE\_BLIND](../Topic/COM_INTERFACE_ENTRY_AGGREGATE_BLIND.md)|Igual que [COM\_INTERFACE\_ENTRY\_AGGREGATE](../Topic/COM_INTERFACE_ENTRY_AGGREGATE.md), salvo que consultar los resultados de IID reenvíe la consulta a `punk`.|  
|[COM\_INTERFACE\_ENTRY\_AUTOAGGREGATE](../Topic/COM_INTERFACE_ENTRY_AUTOAGGREGATE.md)|Igual que [COM\_INTERFACE\_ENTRY\_AGGREGATE](../Topic/COM_INTERFACE_ENTRY_AGGREGATE.md), excepto si `punk` es **NULL**, crea automáticamente el agregado descrito por `clsid`.|  
|[COM\_INTERFACE\_ENTRY\_AUTOAGGREGATE\_BLIND](../Topic/COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND.md)|Igual que [COM\_INTERFACE\_ENTRY\_AUTOAGGREGATE](../Topic/COM_INTERFACE_ENTRY_AUTOAGGREGATE.md), salvo que consultar cualquier IID da lugar a reenviar la consulta a `punk`, y si `punk` es **NULL**, automáticamente creando el agregado descrito por `clsid`.|  
|[COM\_INTERFACE\_ENTRY\_BREAK](../Topic/COM_INTERFACE_ENTRY_BREAK.md)|El programa para llamar a [DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297) cuando la interfaz especificada se consulta para.|  
|[COM\_INTERFACE\_ENTRY\_CACHED\_TEAR\_OFF](../Topic/COM_INTERFACE_ENTRY_CACHED_TEAR_OFF.md)|guarda los datos interfaz\-específicos para cada instancia.|  
|[COM\_INTERFACE\_ENTRY\_TEAR\_OFF](../Topic/COM_INTERFACE_ENTRY_TEAR_OFF.md)|Expone las interfaces de rasgón.|  
|[COM\_INTERFACE\_ENTRY\_CHAIN](../Topic/COM_INTERFACE_ENTRY_CHAIN.md)|Procesa el mapa COM de la clase base al procesamiento alcanza esta entrada en el mapa COM.|  
|[COM\_INTERFACE\_ENTRY\_FUNC](../Topic/COM_INTERFACE_ENTRY_FUNC.md)|Un mecanismo general para enlazar en `QueryInterface` ATL lógica.|  
|[COM\_INTERFACE\_ENTRY\_FUNC\_BLIND](../Topic/COM_INTERFACE_ENTRY_FUNC_BLIND.md)|Igual que [COM\_INTERFACE\_ENTRY\_FUNC](../Topic/COM_INTERFACE_ENTRY_FUNC.md), salvo que consultar cualquier IID produce una llamada a `func`.|  
|[COM\_INTERFACE\_ENTRY\_NOINTERFACE](../Topic/COM_INTERFACE_ENTRY_NOINTERFACE.md)|Devuelve **E\_NOINTERFACE** y finaliza el procesamiento del mapa COM cuando la interfaz especificada se consulta para.|  
|[END\_COM\_MAP](../Topic/END_COM_MAP.md)|Marca el final de las entradas de asignación de interfaz COM.|  
  
## Vea también  
 [Macros](../../atl/reference/atl-macros.md)   
 [COM Map Global Functions](../../atl/reference/com-map-global-functions.md)