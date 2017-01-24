---
title: "CSnapInItemImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSnapInItemImpl"
  - "ATL.CSnapInItemImpl"
  - "ATL::CSnapInItemImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSnapInItemImpl class"
  - "snap-ins"
  - "snap-ins, ATL support for"
  - "snap-ins, data items"
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSnapInItemImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para implementar un objeto de nodo del complemento.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <  
class T,  
BOOL bIsExtension= FALSE  
>  
class ATL_NO_VTABLE CSnapInItemImpl :  
public CSnapInItem  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `CSnapInItemImpl`.  
  
 *bIsExtension*  
 **TRUE** si el objeto es una extensión del complemento; si no **FALSE**.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSnapInItemImpl::CSnapInItemImpl](../Topic/CSnapInItemImpl::CSnapInItemImpl.md)|Constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSnapInItemImpl::AddMenuItems](../Topic/CSnapInItemImpl::AddMenuItems.md)|Agrega los elementos de menú a un menú contextual.|  
|[CSnapInItemImpl::Command](../Topic/CSnapInItemImpl::Command.md)|Llamado por la consola cuando se selecciona un elemento de menú personalizado.|  
|[CSnapInItemImpl::CreatePropertyPages](../Topic/CSnapInItemImpl::CreatePropertyPages.md)|Agrega las páginas a la hoja de propiedades del complemento.|  
|[CSnapInItemImpl::FillData](../Topic/CSnapInItemImpl::FillData.md)|Información de copias en el objeto del complemento en una secuencia especificada.|  
|[CSnapInItemImpl::GetResultPaneInfo](../Topic/CSnapInItemImpl::GetResultPaneInfo.md)|Recupera la estructura de **RESULTDATAITEM** del complemento.|  
|[CSnapInItemImpl::GetResultViewType](../Topic/CSnapInItemImpl::GetResultViewType.md)|Determina el tipo de vista utiliza el panel de resultados.|  
|[CSnapInItemImpl::GetScopePaneInfo](../Topic/CSnapInItemImpl::GetScopePaneInfo.md)|Recupera la estructura de **SCOPEDATAITEM** del complemento.|  
|[CSnapInItemImpl::Notify](../Topic/CSnapInItemImpl::Notify.md)|Llama a la consola para notificar al complemento de acciones realizadas por el usuario.|  
|[CSnapInItemImpl::QueryPagesFor](../Topic/CSnapInItemImpl::QueryPagesFor.md)|Denominado para ver si el nodo del complemento admite las páginas de propiedades.|  
|[CSnapInItemImpl::SetMenuInsertionFlags](../Topic/CSnapInItemImpl::SetMenuInsertionFlags.md)|Modifica los marcadores de la inserción de menú para un objeto del complemento.|  
|[CSnapInItemImpl::SetToolbarButtonInfo](../Topic/CSnapInItemImpl::SetToolbarButtonInfo.md)|Establece la información del botón de la barra de herramientas especificado.|  
|[CSnapInItemImpl::UpdateMenuState](../Topic/CSnapInItemImpl::UpdateMenuState.md)|Actualiza el estado de un elemento de menú contextual.|  
|[CSnapInItemImpl::UpdateToolbarButton](../Topic/CSnapInItemImpl::UpdateToolbarButton.md)|Actualiza el estado del botón de la barra de herramientas especificado.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSnapInItemImpl::m\_bstrDisplayName](../Topic/CSnapInItemImpl::m_bstrDisplayName.md)|El nombre del objeto del complemento.|  
|[CSnapInItemImpl::m\_resultDataItem](../Topic/CSnapInItemImpl::m_resultDataItem.md)|La estructura de Windows **RESULTDATAITEM** utilizada por el objeto de `CSnapInItemImpl` .|  
|[CSnapInItemImpl::m\_scopeDataItem](../Topic/CSnapInItemImpl::m_scopeDataItem.md)|La estructura de Windows **SCOPEDATAITEM** utilizada por el objeto de `CSnapInItemImpl` .|  
  
## Comentarios  
 `CSnapInItemImpl` proporciona una implementación básica de un objeto de nodo de complemento, como agregar elementos de menú y barras de herramientas, y los comandos de reenvío para el nodo del complemento al controlador adecuado funcionan.  Estas características se implementan utilizando varias diferentes interfaces y tipos de mapa.  Las notificaciones de los identificadores de implementación predeterminada enviadas al objeto de nodo determinando la instancia correcta de la clase derivada y después reenviando el mensaje a la instancia correcta.  
  
## Jerarquía de herencia  
 `CSnapInItem`  
  
 `CSnapInItemImpl`  
  
## Requisitos  
 **encabezado:** atlsnap.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)