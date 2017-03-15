---
title: "Cambiar los estilos de control de lista | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CListCtrl (clase), cambiar estilos"
  - "CListCtrl (clase), estilos"
  - "estilos, CListCtrl"
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Cambiar los estilos de control de lista
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede cambiar el estilo de ventana de un control de lista \([CListCtrl](../mfc/reference/clistctrl-class.md)\) en cualquier momento después de crearlo.  Cambiar la orientación de ventana, cambia la clase de vista que utiliza el control.  Por ejemplo, emular el Explorador, es posible que proporcione elementos de menú o los botones de la barra de herramientas para cambiar el control entre vistas diferentes: vista de iconos, vista de lista, etc.  
  
 Por ejemplo, cuando el usuario selecciona el elemento de menú, podría hacer una llamada a [GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584) para recuperar el estilo del control actual y después llamar a [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) para restaurar el estilo.  Para obtener más información, vea [Utilizar Controles de vista de lista](http://msdn.microsoft.com/library/windows/desktop/bb774736) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
 Los estilos disponibles se muestran en [crear](../Topic/CListCtrl::Create.md).  Los estilos `LVS_ICON`, `LVS_SMALLICON`, `LVS_LIST`, y `LVS_REPORT` señalan las cuatro vistas de control list.  
  
## Estilos extendidos  
 Además de los estilos estándar para un control de lista, hay otro conjunto, como estilos extendidos.  Estos estilos, descritos en [Estilos extendidos de la vista de lista](http://msdn.microsoft.com/library/windows/desktop/bb774732) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)], proporcionan varias funciones útiles que personalizan el comportamiento de control de la lista.  Para implementar el comportamiento de un estilo \(como selección de suspensión\), haga una llamada a [CListCtrl::SetExtendedStyle](../Topic/CListCtrl::SetExtendedStyle.md), pasando el estilo necesario.  El ejemplo siguiente se muestra la llamada de función:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/CPP/changing-list-control-styles_1.cpp)]  
  
> [!NOTE]
>  Para que la selección de suspensión funcione, debe hacer **LVS\_EX\_ONECLICKACTIVATE** o **LVS\_EX\_TWOCLICKACTIVATE** activar.  
  
## Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)