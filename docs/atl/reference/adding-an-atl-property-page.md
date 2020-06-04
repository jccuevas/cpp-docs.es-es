---
title: Adición de una página de propiedades ATL
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
ms.openlocfilehash: 3e27d276e5500c1e32ca7b576b355f14f18a47f6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075275"
---
# <a name="adding-an-atl-property-page"></a>Adición de una página de propiedades ATL

> [!NOTE]
> El Asistente para páginas de propiedades ATL no está disponible en Visual Studio 2019 ni en versiones posteriores.

Para agregar una página de propiedades de Active Template Library (ATL) al proyecto, este debe haberse creado como aplicación ATL o como aplicación MFC con compatibilidad ATL. Puede usar el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md) para crear una aplicación ATL, o bien [agregar un objeto ATL a la aplicación MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad ATL con una aplicación MFC.

Si agrega una página de propiedades para un control, su control debe admitir la interfaz [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md). De forma predeterminada, esta interfaz está en la lista de derivación de su clase de control al [crear un control ATL](../../atl/reference/adding-an-atl-control.md) mediante el [Asistente para controles ATL](../../atl/reference/atl-control-wizard.md).

> [!NOTE]
> Si su clase de control no tiene [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) en su lista de derivación, debe agregarla manualmente.

## <a name="to-add-an-atl-property-page-to-your-project"></a>Para agregar una página de propiedades ATL al proyecto.

1. En el **Explorador de soluciones** o la [Vista de clases](/visualstudio/ide/viewing-the-structure-of-code), haga clic con el botón derecho en el nombre del proyecto al que quiera agregar la página de propiedades ATL.

1. En el menú contextual, haga clic en **Agregar** y después en **Agregar clase**.

1. En el cuadro de diálogo [Agregar clase](../../ide/add-class-dialog-box.md), en el panel **Plantillas**, haga clic en **Página de propiedades ATL** y, a continuación, en **Abrir** para mostrar el [Asistente para páginas de propiedades ATL](../../atl/reference/atl-property-page-wizard.md).

Una vez que crea una página de propiedades para un control, debe proporcionar la entrada [PROP_PAGE](property-map-macros.md#prop_page) en la asignación de propiedades para el control.

## <a name="see-also"></a>Consulte también

[Páginas de propiedades](../../atl/atl-com-property-pages.md)<br/>
[Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Ejemplo: Implementar una página de propiedades](../../atl/example-implementing-a-property-page.md)
