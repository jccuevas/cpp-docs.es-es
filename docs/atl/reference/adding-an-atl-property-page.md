---
title: Agregar una página de propiedades ATL
ms.date: 11/04/2016
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
ms.openlocfilehash: c61f666865d3e1db4cdcf2dc6d3e07c2113a79c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62249104"
---
# <a name="adding-an-atl-property-page"></a>Agregar una página de propiedades ATL

Para agregar una página de propiedades de Active Template Library (ATL) al proyecto, el proyecto debe se crearon como una aplicación ATL o como una aplicación MFC con compatibilidad con ATL. Puede usar el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md) para crear una aplicación ATL o [agregar un objeto ATL a una aplicación MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad con ATL para una aplicación MFC.

Si va a agregar una página de propiedades para un control, el control debe admitir la [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) interfaz. De forma predeterminada, esta interfaz está en la lista de derivación del control de clase cuando se [crear un control ATL](../../atl/reference/adding-an-atl-control.md) utilizando el [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md).

> [!NOTE]
> Si no dispone de la clase del control [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) en su lista de derivación, debe agregarlo manualmente.

## <a name="to-add-an-atl-property-page-to-your-project"></a>Para agregar una página de propiedades ATL al proyecto

1. En el **el Explorador de soluciones** o [vista de clases](/visualstudio/ide/viewing-the-structure-of-code), haga clic en el nombre del proyecto al que desea agregar la página de propiedades ATL.

1. En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar clase**.

1. En el [Agregar clase](../../ide/add-class-dialog-box.md) cuadro de diálogo el **plantillas** panel, haga clic en **página de propiedades ATL** y, a continuación, haga clic en **abierto** para mostrar el [Asistente para páginas de propiedades ATL](../../atl/reference/atl-property-page-wizard.md).

Una vez que cree una página de propiedades para un control, debe proporcionar el [PROP_PAGE](property-map-macros.md#prop_page) entrada en el mapa de propiedades para el control.

## <a name="see-also"></a>Vea también

[Páginas de propiedades](../../atl/atl-com-property-pages.md)<br/>
[Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Ejemplo: Implementar una página de propiedades](../../atl/example-implementing-a-property-page.md)
