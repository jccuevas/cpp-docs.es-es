---
title: "Controles de lista virtual | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "caché, datos de elementos de control de lista virtual"
  - "controles de lista, vista de lista"
  - "controles de lista, virtual"
  - "controles de lista virtual"
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controles de lista virtual
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un control de lista virtual es un control listview que tiene el estilo de **LVS\_OWNERDATA** .  Este estilo permite al control admita un recuento de elementos hasta `DWORD` \(el número predeterminado del elemento extiende sólo a `int`\).  Sin embargo, la ventaja mayor proporcionada por este estilo es la capacidad sólo de tener un subconjunto de elementos de datos en memoria en cualquier momento.  Esto permite al control de la vista de lista virtual se preste para el uso con bases de datos grandes de información, donde ya colocados los métodos específicos de acceso a datos.  
  
> [!NOTE]
>  Además de proporcionar la funcionalidad virtual de la lista de `CListCtrl`, MFC también ofrece la misma funcionalidad en la clase de [CListView](../mfc/reference/clistview-class.md) .  
  
 Hay problemas de compatibilidad que debe tener en cuenta al desarrollar controles de lista virtuales.  Para obtener más información, vea la sección sobre los problemas de compatibilidad del tema de los Controles de la vista de lista en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## Administrar la notificación de LVN\_GETDISPINFO  
 Los controles de lista virtuales mantener información sobre el elemento muy pequeña.  Salvo la selección de elementos y la información de foco, toda la información sobre el elemento es administrada por el propietario del control.  La información es solicitada por el marco mediante un mensaje de notificación de **LVN\_GETDISPINFO** .  Para proporcionar la información solicitada, el propietario del control de lista virtual \(o el propio control\) debe controlar esta notificación.  Esto se puede facilitar la mediante la ventana Propiedades \(vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)\).  El código resultante debería tener una apariencia similar al ejemplo siguiente \(donde `CMyDialog` posee el objeto de control de lista virtual y el diálogo está administrando la notificación\):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/CPP/virtual-list-controls_1.cpp)]  
  
 En el controlador del mensaje de notificación de **LVN\_GETDISPINFO** , debe comprobar lo que se solicita el tipo de información.  Los valores posibles son:  
  
-   el miembro de`LVIF_TEXT`The `pszText` debe completarse.  
  
-   el miembro de`LVIF_IMAGE`The `iImage` debe completarse.  
  
-   El miembro  *iIndent* de**LVIF\_INDENT**The debe completarse.  
  
-   el miembro  *lParam* de`LVIF_PARAM`The debe completarse. \(No presente para los sub\- elementos\).  
  
-   el miembro  *de estado* de`LVIF_STATE`The debe completarse.  
  
 Deberá proporcionar cualquier información se solicita al marco.  
  
 El ejemplo siguiente \(tomado del cuerpo del controlador de notificación para el objeto de control de lista\) muestra un método posible proporcionando la información para los búferes de texto y la imagen de un elemento:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/CPP/virtual-list-controls_2.cpp)]  
  
## Controles de lista almacenamiento en caché y de Virtual  
 Dado que diseñan a este tipo de control list para los conjuntos de datos, se recomienda almacenar en caché datos solicitados de elemento para mejorar el rendimiento de la recuperación.  El marco de trabajo proporciona un mecanismo memoria caché\- que sugiere que ayuda a optimizar caché enviando un mensaje de notificación de **LVN\_ODCACHEHINT** .  
  
 El ejemplo siguiente actualiza la memoria caché con el intervalo pasado a la función de controlador.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/CPP/virtual-list-controls_3.cpp)]  
  
 Para obtener más información sobre la preparación y mantener de caché, vea la sección administración de la memoria caché del tema de los Controles de la vista de lista en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## Elementos específicos de buscar  
 El mensaje de notificación de **LVN\_ODFINDITEM** es enviado por el control de lista virtual a un elemento determinado del control de lista necesita encontrar.  Se envía el mensaje de notificación cuando el control de vista de lista recibe el acceso de clave rápida o cuando recibe un mensaje de **LVM\_FINDITEM** .  La información de búsqueda se envía en forma de estructura de **LVFINDINFO** , que es un miembro de la estructura de **NMLVFINDITEM** .  Controle este mensaje reemplazando la función de `OnChildNotify` de objetos y de dentro del control de lista el cuerpo del controlador, compruebe el mensaje de **LVN\_ODFINDITEM** .  Si se encuentra, realice la acción adecuada.  
  
 Debe estar preparado para buscar un elemento que coincida con la información especificada por el control de vista de lista.  Debe devolver el índice del elemento si es correcto, o \-1 si no se encuentra ningún elemento coincidente.  
  
## Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)