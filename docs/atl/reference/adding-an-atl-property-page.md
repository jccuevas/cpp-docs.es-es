---
title: "Agregar una página de propiedades ATL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: 7b6a6220a33890d99e6fb2bd81ce832b38720c50
ms.lasthandoff: 02/24/2017

---
# <a name="adding-an-atl-property-page"></a>Agregar una página de propiedades ATL
Para agregar una página de propiedades de Active Template Library (ATL) a su proyecto, el proyecto debe haber creado como una aplicación ATL o como una aplicación MFC con compatibilidad ATL. Puede usar el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md) para crear una aplicación ATL o [agregar un objeto ATL a una aplicación MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad con ATL para una aplicación MFC.  
  
 Si va a agregar una página de propiedades para un control, el control debe admitir la [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) interfaz. De forma predeterminada, esta interfaz está en la lista de derivación del control de clase cuando se [crear un control ATL](../../atl/reference/adding-an-atl-control.md) utilizando la [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md).  
  
> [!NOTE]
>  Si no tiene una clase de control [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) en su lista de derivación, debe agregarlo manualmente.  
  
### <a name="to-add-an-atl-property-page-to-your-project"></a>Para agregar una página de propiedades ATL al proyecto  
  
1.  En el **el Explorador de soluciones** o [la vista de clases](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic en el nombre del proyecto al que desea agregar la página de propiedades ATL.  
  
2.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar clase**.  
  
3.  En el [Agregar clase](../../ide/add-class-dialog-box.md) cuadro de diálogo, en el panel Plantillas, haga clic en **página de propiedades ATL** y, a continuación, haga clic en **abiertos** para mostrar la [Asistente para páginas de propiedades ATL](../../atl/reference/atl-property-page-wizard.md).  
  
 Una vez creada una página de propiedades para un control, debe proporcionar el [PROP_PAGE](http://msdn.microsoft.com/library/2155973e-b96c-4385-bf85-5d6112c969b8) entrada en el mapa de propiedades para el control.  
  
## <a name="see-also"></a>Vea también  
 [Páginas de propiedades](../../atl/atl-com-property-pages.md)   
 [Fundamentos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
 [Ejemplo: Implementar una página de propiedades](../../atl/example-implementing-a-property-page.md)


