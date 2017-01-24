---
title: "Creating an Aggregated Object | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregate objects [C++], crear"
  - "aggregation [C++], creating aggregated objects"
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating an Aggregated Object
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La agregación delega las llamadas de **IUnknown** , proporcionando un puntero a **IUnknown** del objeto externo al objeto interno.  
  
### para crear un objeto agregado  
  
1.  Agregue un puntero de **IUnknown** al objeto de la clase e inicialícela a **NULL** en el constructor.  
  
2.  Reemplazo [FinalConstruct](../Topic/CComObjectRootEx::FinalConstruct.md) para crear el agregado.  
  
3.  Utilice el puntero de **IUnknown** , definido en el paso 1, como segundo parámetro para las macros de [COM\_INTERFACE\_ENTRY\_AGGREGATE](../Topic/COM_INTERFACE_ENTRY_AGGREGATE.md) .  
  
4.  Reemplazo [FinalRelease](../Topic/CComObjectRootEx::FinalRelease.md) para liberar el puntero de **IUnknown** .  
  
> [!NOTE]
>  Si utiliza y libera una interfaz del objeto agregado durante `FinalConstruct`, debe agregar la macro de [DECLARE\_PROTECT\_FINAL\_CONSTRUCT](../Topic/DECLARE_PROTECT_FINAL_CONSTRUCT.md) a la definición del objeto de clase.  
  
## Vea también  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)