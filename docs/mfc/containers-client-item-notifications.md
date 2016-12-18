---
title: "Contenedores: Notificaciones de elementos de cliente | Microsoft Docs"
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
  - "elementos de cliente y contenedores OLE"
  - "notificaciones, contenedor de elementos cliente"
  - "contenedores OLE, notificaciones de elementos de cliente"
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Contenedores: Notificaciones de elementos de cliente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se abordan las funciones reemplazables que el marco de trabajo de MFC llama cuando las aplicaciones de servidor modifican elementos en el documento de la aplicación cliente.  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md) define varias funciones reemplazables que se llama en respuesta a las solicitudes de la aplicación componente, que también se denomina la aplicación de servidor.  Estos overridables actúan normalmente como notificaciones.  Informa a la aplicación contenedora varios eventos, como desplazamiento, activación, o un cambio de posición, y los cambios que el usuario crea al editar u otro manipular el elemento.  
  
 El marco notifica a la aplicación contenedora de cambios con una llamada a `COleClientItem::OnChange`, una función overridable cuya se requiere implementación.  Esta función protegida recibe dos argumentos.  El primer especifica la razón por la que el servidor ha cambiado el elemento:  
  
|Notificación|Significado|  
|------------------|-----------------|  
|`OLE_CHANGED`|El aspecto OLE del elemento ha cambiado.|  
|`OLE_SAVED`|Se ha guardado el elemento.|  
|`OLE_CLOSED`|El elemento OLE se ha cerrado.|  
|**OLE\_RENAMED**|El documento del servidor que contiene el elemento OLE se ha cambiado.|  
|`OLE_CHANGED_STATE`|El elemento OLE ha cambiado de un estado a otro.|  
|**OLE\_CHANGED\_ASPECT**|El aspecto OLE de dibujo del elemento ha sido modificado por el marco.|  
  
 Estos valores son de enumeración de **OLE\_NOTIFICATION** , que se define en AFXOLE.H.  
  
 El segundo argumento de esta función especifica cómo el elemento ha cambiado o qué estado entra en:  
  
|Cuando el primer argumento|Segundo argumento|  
|--------------------------------|-----------------------|  
|`OLE_SAVED` o `OLE_CLOSED`|No se utiliza.|  
|`OLE_CHANGED`|Especifica la apariencia del elemento OLE que ha cambiado.|  
|`OLE_CHANGED_STATE`|Describe el estado que se introdujo \(`emptyState`, **loadedState**, `openState`, `activeState`, o `activeUIState`\).|  
  
 Para obtener más información sobre los estados que un elemento de cliente puede suponer, vea [Contenedores: Estados de Cliente\- elemento](../mfc/containers-client-item-states.md).  
  
 El marco de trabajo llama a `COleClientItem::OnGetItemPosition` cuando un elemento se está activando para la edición en contexto.  La implementación es necesaria para las aplicaciones que la edición en contexto admiten.  El asistente para aplicaciones MFC proporciona una implementación básica, que asigna las coordenadas del elemento al objeto de `CRect` que se pasa como argumento a `OnGetItemPosition`.  
  
 Si los cambios de OLE de posición o del tamaño de un elemento durante la edición en contexto, la información del contenedor de la posición del elemento y los rectángulos de recorte deben actualizarse y el servidor debe recibir información sobre los cambios.  El marco de trabajo llama a `COleClientItem::OnChangeItemPosition` con este fin.  El asistente para aplicaciones MFC proporciona un reemplazo que llame a la función de clase base.  Debe modificar la función que el asistente para aplicaciones escribe para `COleClientItem`\- clase derivada de modo que la función actualice cualquier información conservará por el objeto de cliente\- elemento.  
  
## Vea también  
 [Contenedores](../mfc/containers.md)   
 [Contenedores: Estados de elementos de cliente](../mfc/containers-client-item-states.md)   
 [COleClientItem::OnChangeItemPosition](../Topic/COleClientItem::OnChangeItemPosition.md)