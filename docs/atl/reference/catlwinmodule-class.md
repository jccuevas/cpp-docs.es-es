---
title: "CAtlWinModule Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAtlWinModule"
  - "ATL.CAtlWinModule"
  - "CAtlWinModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlWinModule class"
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CAtlWinModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona compatibilidad para los componentes de visualización en una ventana de ATL.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CAtlWinModule : public _ATL_WIN_MODULE  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlWinModule::CAtlWinModule](../Topic/CAtlWinModule::CAtlWinModule.md)|el constructor.|  
|[CAtlWinModule::~CAtlWinModule](../Topic/CAtlWinModule::~CAtlWinModule.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlWinModule::AddCreateWndData](../Topic/CAtlWinModule::AddCreateWndData.md)|agrega un objeto de datos.|  
|[CAtlWinModule::ExtractCreateWndData](../Topic/CAtlWinModule::ExtractCreateWndData.md)|Devuelve un puntero al objeto de datos del módulo de la ventana.|  
  
## Comentarios  
 Esta clase proporciona compatibilidad para todas las clases ATL que requieren características de visualización en una ventana.  
  
## Jerarquía de herencia  
 [\_ATL\_WIN\_MODULE](../Topic/_ATL_WIN_MODULE.md)  
  
 `CAtlWinModule`  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [\_ATL\_WIN\_MODULE](../Topic/_ATL_WIN_MODULE.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)