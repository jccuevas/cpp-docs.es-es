---
title: Agregar una página de propiedades ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- property pages, adding
- ATL projects, adding property pages
- controls [ATL], property pages
ms.assetid: ddf92b49-42a2-46d2-b6b8-d37baedebeca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c46adc199a5d6b0bc814cc203b94ac3d268a560d
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860633"
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
