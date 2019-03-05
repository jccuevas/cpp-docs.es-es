---
title: Adición de un objeto Simple ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.adding.atl
helpviewer_keywords:
- ATL projects, adding objects
- objects [ATL]
- ATL, simple objects
ms.assetid: 9c57d2ef-0447-4c84-8982-3304b8e49847
ms.openlocfilehash: 95a93268ca76516c1b3f736c106518ae6d94cc27
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326821"
---
# <a name="adding-an-atl-simple-object"></a>Adición de un objeto Simple ATL

Para agregar un objeto ATL (Active Template Library) a su proyecto, el proyecto debe se crearon como una aplicación ATL o como una aplicación MFC con compatibilidad con ATL. Puede usar el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md) para crear una aplicación ATL, o bien [agregar un objeto ATL a una aplicación MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad con ATL para una aplicación MFC.

Puede definir interfaces COM para un nuevo objeto ATL al crearlo en primer lugar, o agregarlos más adelante mediante el uso de la [Implementar interfaz](../../ide/implement-interface-wizard.md) comando desde el **vista de clases** menú contextual.

## <a name="to-add-an-atl-simple-object-to-your-atl-com-project"></a>Para agregar un objeto simple ATL al proyecto ATL COM

1. En el **el Explorador de soluciones** o [vista de clases](/visualstudio/ide/viewing-the-structure-of-code), haga clic en el nombre del proyecto al que desea agregar el objeto simple ATL.

1. En el menú contextual, haga clic en **Agregar** y después en **Agregar clase**.

1. En el [Agregar clase](../../ide/add-class-dialog-box.md) cuadro de diálogo el **plantillas** panel, haga clic en **objeto Simple ATL**y, a continuación, haga clic en **abierto** para mostrar el [Asistente para objetos simples ATL](../../atl/reference/atl-simple-object-wizard.md).

1. Establezca opciones adicionales para el proyecto en el [opciones](../../atl/reference/options-atl-simple-object-wizard.md) página de la **objeto Simple ATL** asistente.

1. Haga clic en **finalizar** para agregar el objeto al proyecto.

## <a name="see-also"></a>Vea también

[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Adición de una nueva interfaz a un proyecto ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[Agregar puntos de conexión a un objeto](../../atl/adding-connection-points-to-an-object.md)<br/>
[Agregar un método](../../ide/adding-a-method-visual-cpp.md)<br/>
[Clase MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Agregar una clase genérica de C++](../../ide/adding-a-generic-cpp-class.md)
