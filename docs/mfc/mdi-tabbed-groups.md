---
title: "Grupos con pesta&#241;as MDI | Microsoft Docs"
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
  - "mdi, grupos con pestañas"
  - "grupos con pestañas"
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Grupos con pesta&#241;as MDI
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La característica con fichas \(MDI\) grupos de interfaz de múltiples documentos permite a las aplicaciones de \(MDI\) de interfaz de múltiples documentos para mostrar una o más ventanas con fichas \(o grupos de ventanas con fichas, conocidos como *grupos con pestañas*\) en el área de cliente MDI.  Las ventanas con fichas se pueden alinear vertical u horizontalmente.  Si los hosts de una aplicación más de un MDI tabularon al grupo, a los divisores separan los grupos.  
  
## Características  
 Los siguientes son características de MDI tabularon grupos:  
  
-   Una aplicación puede crear las ventanas con fichas dinámicamente.  
  
-   Una aplicación puede clasificar las ventanas con fichas horizontal o verticalmente.  
  
-   A los divisores separan grupos de ventanas con fichas.  El usuario puede cambiar el tamaño de los grupos con fichas mediante el divisor.  
  
-   El usuario puede arrastrar las fichas individuales entre grupos.  
  
-   El usuario puede arrastrar las fichas individuales para crear otros nuevos.  
  
-   El usuario puede mover las tabulaciones o crear nuevos grupos mediante un menú contextual.  
  
-   Una aplicación puede guardar y cargar el diseño de ventanas con fichas.  
  
-   Una aplicación puede guardar y cargar la lista de documentos de MDI.  
  
-   Una aplicación puede obtener acceso a grupos con pestañas individuales y modificar sus parámetros.  
  
### Mediante MDI con grupos  
 Los siguientes son tareas realizadas normalmente con MDI tabularon grupos:  
  
-   Para habilitar MDI con grupos para una ventana de marco principal, llama a [CMDIFrameWndEx::EnableMDITabbedGroups](../Topic/CMDIFrameWndEx::EnableMDITabbedGroups.md).  El segundo parámetro de este método es una instancia de la clase de `CMDITabInfo` .  Puede utilizar los parámetros predeterminados o modificarlos antes de llamar a `CMDIFrameWndEx::EnableMDITabbedGroups`.  
  
-   Para modificar las propiedades de MDI con el grupo en tiempo de ejecución, crea o modifica un objeto de `CMDITabInfo` y llama a `CMDIFrameWndEx::EnableMDITabbedGroups` de nuevo  
  
-   Para obtener una lista de MDI con ventanas, llama a `CMDIFrameWndEx::GetMDITabGroups`.  
  
-   Para crear un nuevo grupo con MDI junto a un activo con el grupo, llama a `CMDIFrameWndEx::MDITabNewGroup`.  
  
-   Para desplazar el foco a la ventana siguiente o anterior de un grupo con fichas, llame a `CMDIFrameWndEx::MDITabMoveToNextGroup`.  
  
-   Para determinar si una ventana es un miembro de una llamada grupal tabulada MDI `CMDIFrameWndEx::IsMemberOfMDITabGroup`.  
  
-   Para determinar si habilitan las fichas MDI o grupos con pestañas MDI para una ventana de marco principal, llamada `CMDIFrameWndEx::AreMDITabs`.  Solamente para determinar si MDI con grupos están habilitadas, llamada `CMDIFrameWndEx::IsMDITabbedGroup`.  
  
-   Para mostrar un menú contextual cuando el usuario hace clic en una pestaña o la arrastra a otro grupo con MDI, reemplace `CMDIFrameWndEx::OnShowMDITabContextMenu` en `CMDIFrameWndEx`\- clase derivada.  Si no implementa este método, la aplicación no mostrará el menú contextual.  
  
-   Para guardar el diseño de MDI con grupos en una aplicación, llame a `CMDIFrameWndEx::SaveMDIState`.  Para cargar MDI previamente guardado con perfiles de grupo, llama a `CMDIFrameWndEx::LoadMDIState`.  También puede llamar a estos métodos para cargar o guardar la lista de documentos abiertos en una aplicación MDI.  Para obtener más información sobre el estado de MDI de guardar y de carga, vea [CMDIFrameWndEx::LoadMDIState](../Topic/CMDIFrameWndEx::LoadMDIState.md).  
  
## Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)   
 [CMDIFrameWndEx \(Clase\)](../mfc/reference/cmdiframewndex-class.md)   
 [Clase CMDIChildWndEx](../mfc/reference/cmdichildwndex-class.md)   
 [CMDITabInfo Class](../mfc/reference/cmditabinfo-class.md)