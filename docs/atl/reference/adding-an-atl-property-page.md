---
title: "Agregar una página de propiedades ATL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a7c1d7ae11873c2bc47f1bb4a7a2439768e8347b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="adding-an-atl-property-page"></a>Agregar una página de propiedades ATL
Para agregar una página de propiedades de Active Template Library (ATL) al proyecto, la debe ha creado como una aplicación ATL o como una aplicación MFC que sea compatible con ATL. Puede usar el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md) para crear una aplicación ATL o [agregar un objeto ATL a una aplicación MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad con ATL para una aplicación MFC.  
  
 Si va a agregar una página de propiedades para un control, el control debe admitir la [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) interfaz. De forma predeterminada, esta interfaz está en la lista de derivación del control de clase cuando se [crear un control ATL](../../atl/reference/adding-an-atl-control.md) mediante la [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md).  
  
> [!NOTE]
>  Si no dispone de la clase del control [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) en su lista de derivación, debe agregarse manualmente.  
  
### <a name="to-add-an-atl-property-page-to-your-project"></a>Para agregar una página de propiedades ATL al proyecto  
  
1.  En la vista **el Explorador de soluciones** o [vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic en el nombre del proyecto al que desea agregar la página de propiedades ATL.  
  
2.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar clase**.  
  
3.  En el [Agregar clase](../../ide/add-class-dialog-box.md) cuadro de diálogo, en el panel Plantillas, haga clic en **página de propiedades ATL** y, a continuación, haga clic en **abiertos** para mostrar la [Asistente para la página de propiedades de ATL](../../atl/reference/atl-property-page-wizard.md).  
  
 Una vez que cree una página de propiedades para un control, debe proporcionar el [PROP_PAGE](property-map-macros.md#prop_page) entrada en la asignación de propiedad para el control.  
  
## <a name="see-also"></a>Vea también  
 [Páginas de propiedades](../../atl/atl-com-property-pages.md)   
 [Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
 [Ejemplo: Implementar una página de propiedades](../../atl/example-implementing-a-property-page.md)

