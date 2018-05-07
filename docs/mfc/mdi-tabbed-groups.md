---
title: Grupos con pestañas MDI | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- mdi [MFC], tabbed groups
- tabbed grous [MFC]
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a7cf6420a331d46f2a158c16a30d439f334a46b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="mdi-tabbed-groups"></a>Grupos con pestañas MDI
La característica de grupos con pestañas de varios documentos MDI (interfaz) permite que varias aplicaciones de MDI (interfaz) del documento mostrar una o varias ventanas con pestañas (o grupos de ventanas con pestañas, conocidos como *grupos con pestañas*) en el área de cliente MDI. Las ventanas con pestañas se puedan Alinear horizontal o verticalmente. Si una aplicación hospeda más de un grupo con pestañas MDI, los grupos se separan mediante separadores.  
  
## <a name="features"></a>Características  
 Éstas son las características de grupos MDI con fichas:  
  
-   Una aplicación puede crear ventanas con pestañas dinámicamente.  
  
-   Una aplicación puede alinear las ventanas con pestañas horizontal o verticalmente.  
  
-   Grupos de ventanas con fichas se separan mediante separadores. El usuario puede cambiar el tamaño de grupos con pestañas mediante el divisor.  
  
-   El usuario puede arrastrar fichas individuales entre grupos.  
  
-   El usuario puede arrastrar fichas individuales para crear grupos nuevos.  
  
-   El usuario puede mover las pestañas o crear nuevos grupos mediante el uso de un menú contextual.  
  
-   Una aplicación puede guardar y cargar el diseño de las ventanas con pestañas.  
  
-   Una aplicación puede guardar y cargar la lista de documentos MDI.  
  
-   Una aplicación puede tener acceso a grupos con pestañas individuales y modificar sus parámetros.  
  
### <a name="using-mdi-tabbed-groups"></a>Uso de MDI con grupos con pestañas  
 Las siguientes tareas se realizan normalmente con grupos MDI con fichas son:  
  
-   Para habilitar los grupos de una ventana de marco principal MDI con fichas, llame a [CMDIFrameWndEx:: Enablemditabbedgroups](../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups). El segundo parámetro de este método es una instancia de la `CMDITabInfo` clase. Puede usar los parámetros predeterminados o modificarlos antes de llamar a `CMDIFrameWndEx::EnableMDITabbedGroups`.  
  
-   Para modificar las propiedades de un grupo con pestañas MDI en tiempo de ejecución, crear o modificar un `CMDITabInfo` objeto y llame al método `CMDIFrameWndEx::EnableMDITabbedGroups` nuevo  
  
-   Para obtener una lista de MDI con fichas windows, llame al método `CMDIFrameWndEx::GetMDITabGroups`.  
  
-   Para crear un nuevo grupo con pestañas MDI junto a un grupo de pestañas activo, llame a `CMDIFrameWndEx::MDITabNewGroup`.  
  
-   Para cambiar el foco de entrada a la ventana anterior o siguiente de un grupo de pestañas, llame a `CMDIFrameWndEx::MDITabMoveToNextGroup`.  
  
-   Para determinar si una ventana es un miembro de los formularios MDI con fichas llamada grupo `CMDIFrameWndEx::IsMemberOfMDITabGroup`.  
  
-   Para determinar si las fichas MDI o grupos MDI con fichas están habilitados para una ventana de marco principal, llame a `CMDIFrameWndEx::AreMDITabs`. Para determinar solo si están habilitados los grupos MDI con pestañas, llame a `CMDIFrameWndEx::IsMDITabbedGroup`.  
  
-   Para mostrar un menú contextual cuando el usuario hace clic en una pestaña o lo arrastra al otro grupo con pestañas MDI, invalidar `CMDIFrameWndEx::OnShowMDITabContextMenu` en el `CMDIFrameWndEx`-clase derivada. Si no implementa este método, la aplicación no mostrará el menú contextual.  
  
-   Para guardar el diseño de los grupos MDI con fichas en una aplicación, llame a `CMDIFrameWndEx::SaveMDIState`. Para cargar una MDI guardada anteriormente con fichas perfil de grupo, llame al método `CMDIFrameWndEx::LoadMDIState`. También puede llamar a estos métodos para cargar o guardar la lista de los documentos abiertos en una aplicación MDI. Para obtener más información sobre cómo guardar y cargar el estado MDI, vea [CMDIFrameWndEx::LoadMDIState](../mfc/reference/cmdiframewndex-class.md#loadmdistate).  
  
## <a name="see-also"></a>Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)   
 [CMDIFrameWndEx (clase)](../mfc/reference/cmdiframewndex-class.md)   
 [Clase CMDIChildWndEx](../mfc/reference/cmdichildwndex-class.md)   
 [CMDITabInfo (clase)](../mfc/reference/cmditabinfo-class.md)
