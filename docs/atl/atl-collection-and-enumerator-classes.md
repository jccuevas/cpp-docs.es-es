---
title: "ATL Collection and Enumerator Classes | Microsoft Docs"
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
  - "clases de colección, ATL"
  - "enumeradores, clases ATL"
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL Collection and Enumerator Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL proporciona las siguientes clases para ayudarle colecciones y enumeradores de implementan.  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|implementación de la interfaz de intercalación|  
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|Implementación de la interfaz de enumerador \(supone los datos almacenados en un contenedor de STL\-compatible\)|  
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|Implementación de la interfaz de enumerador \(supone los datos almacenados en una matriz\)|  
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|Implementación del objeto de enumerador \(utiliza `IEnumOnSTLImpl`\)|  
|[CComEnum](../atl/reference/ccomenum-class.md)|Implementación del objeto de enumerador \(utiliza `CComEnumImpl`\)|  
|[\_Copy](../atl/atl-copy-policy-classes.md)|Copie la clase de directiva|  
|[\_CopyInterface](../atl/atl-copy-policy-classes.md)|Copie la clase de directiva|  
|[CAdapt](../atl/reference/cadapt-class.md)|Clase del adaptador \(operador **de oculta y** el permitir`CComPtr``CComQIPtr`, y`CComBSTR` almacenar en contenedores STL\)|  
  
## Vea también  
 [Colecciones y enumeradores](../atl/atl-collections-and-enumerators.md)