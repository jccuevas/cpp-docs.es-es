---
title: "COleControlContainer Class | Microsoft Docs"
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
  - "COleControlContainer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedores de controles ActiveX [C++], control site"
  - "COleControlContainer class"
  - "controles personalizados [MFC], sites"
ms.assetid: f7ce9246-0fb7-4f07-a83a-6c2390d0fdf8
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleControlContainer Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Actúa como contenedor de control para controles ActiveX.  
  
## Sintaxis  
  
```  
class COleControlContainer : public CCmdTarget  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleControlContainer::COleControlContainer](../Topic/COleControlContainer::COleControlContainer.md)|Crea un objeto `COleControlContainer`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleControlContainer::AttachControlSite](../Topic/COleControlContainer::AttachControlSite.md)|Crea un sitio del control, hospedado en el contenedor.|  
|[COleControlContainer::BroadcastAmbientPropertyChange](../Topic/COleControlContainer::BroadcastAmbientPropertyChange.md)|Informa a todos los controles de hospedados que una propiedad de ambiente ha cambiado.|  
|[COleControlContainer::CheckDlgButton](../Topic/COleControlContainer::CheckDlgButton.md)|modifica el control de botón especificado.|  
|[COleControlContainer::CheckRadioButton](../Topic/COleControlContainer::CheckRadioButton.md)|Selecciona el botón de radio especificado de un grupo.|  
|[COleControlContainer::CreateControl](../Topic/COleControlContainer::CreateControl.md)|crea un control ActiveX hospedado.|  
|[COleControlContainer::CreateOleFont](../Topic/COleControlContainer::CreateOleFont.md)|Crea una fuente OLE.|  
|[COleControlContainer::FindItem](../Topic/COleControlContainer::FindItem.md)|Devuelve el sitio personalizado del control especificado.|  
|[COleControlContainer::FreezeAllEvents](../Topic/COleControlContainer::FreezeAllEvents.md)|Determina si el sitio del control está aceptando eventos.|  
|[COleControlContainer::GetAmbientProp](../Topic/COleControlContainer::GetAmbientProp.md)|Recupera la propiedad de ambiente especificada.|  
|[COleControlContainer::GetDlgItem](../Topic/COleControlContainer::GetDlgItem.md)|Recupera el control especificado del diálogo.|  
|[COleControlContainer::GetDlgItemInt](../Topic/COleControlContainer::GetDlgItemInt.md)|Recupera el valor del control especificado del diálogo.|  
|[COleControlContainer::GetDlgItemText](../Topic/COleControlContainer::GetDlgItemText.md)|Recupera la leyenda del control especificado del diálogo.|  
|[COleControlContainer::HandleSetFocus](../Topic/COleControlContainer::HandleSetFocus.md)|Determina si el contenedor controla los mensajes de `WM_SETFOCUS` .|  
|[COleControlContainer::HandleWindowlessMessage](../Topic/COleControlContainer::HandleWindowlessMessage.md)|Controla los mensajes enviados a un control sin ventana.|  
|[COleControlContainer::IsDlgButtonChecked](../Topic/COleControlContainer::IsDlgButtonChecked.md)|Determina el estado del botón especificado.|  
|[COleControlContainer::OnPaint](../Topic/COleControlContainer::OnPaint.md)|Denominado para volver a dibujar una parte del contenedor.|  
|[COleControlContainer::OnUIActivate](../Topic/COleControlContainer::OnUIActivate.md)|Se invoca cuando un control alrededor ser en contexto se activa.|  
|[COleControlContainer::OnUIDeactivate](../Topic/COleControlContainer::OnUIDeactivate.md)|Llamado cuando un control está a punto de desactivar.|  
|[COleControlContainer::ScrollChildren](../Topic/COleControlContainer::ScrollChildren.md)|Llamado por el marco cuando los mensajes de desplazamiento se reciben de ventana secundaria.|  
|[COleControlContainer::SendDlgItemMessage](../Topic/COleControlContainer::SendDlgItemMessage.md)|Envía un mensaje al control especificado.|  
|[COleControlContainer::SetDlgItemInt](../Topic/COleControlContainer::SetDlgItemInt.md)|Establece el valor del control especificado.|  
|[COleControlContainer::SetDlgItemText](../Topic/COleControlContainer::SetDlgItemText.md)|Establece el texto del control especificado.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleControlContainer::m\_crBack](../Topic/COleControlContainer::m_crBack.md)|El color de fondo del contenedor.|  
|[COleControlContainer::m\_crFore](../Topic/COleControlContainer::m_crFore.md)|El color de primer plano del contenedor.|  
|[COleControlContainer::m\_listSitesOrWnds](../Topic/COleControlContainer::m_listSitesOrWnds.md)|Una lista de los sitios admitidos en el control.|  
|[COleControlContainer::m\_nWindowlessControls](../Topic/COleControlContainer::m_nWindowlessControls.md)|el número de controles sin ventana hospedados.|  
|[COleControlContainer::m\_pOleFont](../Topic/COleControlContainer::m_pOleFont.md)|Un puntero a la fuente\) del sitio del control personalizado.|  
|[COleControlContainer::m\_pSiteCapture](../Topic/COleControlContainer::m_pSiteCapture.md)|Puntero al sitio del control de captura.|  
|[COleControlContainer::m\_pSiteFocus](../Topic/COleControlContainer::m_pSiteFocus.md)|Puntero al control que tiene actualmente el foco de entrada.|  
|[COleControlContainer::m\_pSiteUIActive](../Topic/COleControlContainer::m_pSiteUIActive.md)|Puntero al control que está actualmente en contexto elevado.|  
|[COleControlContainer::m\_pWnd](../Topic/COleControlContainer::m_pWnd.md)|Puntero a la ventana que implementa el contenedor del control.|  
|[COleControlContainer::m\_siteMap](../Topic/COleControlContainer::m_siteMap.md)|El mapa del sitio.|  
  
## Comentarios  
 Esto se hace proporcionando compatibilidad para uno o más sitios de controles ActiveX \(implementados por `COleControlSite`\).  `COleControlContainer` implementa todas las interfaces de [IOleInPlaceFrame](http://msdn.microsoft.com/library/windows/desktop/ms692770) y de [IOleContainer](http://msdn.microsoft.com/library/windows/desktop/ms690103) , permitiendo a los controles ActiveX contenido satisfacen las clasificaciones como elementos en contexto.  
  
 Normalmente, esta clase se utiliza junto con `COccManager` y `COleControlSite` para implementar un contenedor personalizado del control ActiveX, con los sitios personalizadas para uno o más controles ActiveX.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlContainer`  
  
## Requisitos  
 **encabezado:** afxocc.h  
  
## Vea también  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleControlSite Class](../../mfc/reference/colecontrolsite-class.md)   
 [COccManager Class](../../mfc/reference/coccmanager-class.md)