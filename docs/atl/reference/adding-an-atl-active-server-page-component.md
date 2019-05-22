---
title: Adición de un componente de páginas Active Server ATL
ms.date: 05/09/2019
ms.assetid: 7be2204c-6e58-4099-8892-001b848c8987
ms.openlocfilehash: b6c1d23efdff6885cc8ab900aaf552db39631e6e
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706926"
---
# <a name="adding-an-atl-active-server-page-component"></a>Adición de un componente de páginas Active Server ATL


::: moniker range="vs-2019"

El Asistente para componentes de páginas Active Server ATL no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

Para agregar un objeto Active Template Library (ATL) al proyecto, este se debe haber creado como aplicación COM ATL o como aplicación MFC con compatibilidad ATL. Puede usar el [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md) para crear una aplicación ATL, puede seleccionar **Agregar compatibilidad de ATL a MFC** en el cuadro de diálogo [Agregar clase](../../ide/add-class-dialog-box.md), o bien [agregar un objeto ATL a la aplicación MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad de ATL con una aplicación MFC.

Los componentes de páginas Active Server forman parte de la arquitectura Internet Information Services, que proporciona las siguientes características avanzadas de desarrollo web:

- Puede insertar componentes ASP en las páginas HTML para crear contenido dinámico, independiente del explorador.

- Puede usar las páginas ASP para proporcionar conectividad de base de datos basada en estándares.

- Puede usar las funciones de control de errores de ASP para las aplicaciones basadas en web.

## <a name="to-add-an-atl-active-server-pages-component-to-your-project"></a>Para agregar un componente de páginas Active Server ATL al proyecto

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nombre del proyecto al que quiera agregar el componente de páginas Active Server ATL.

1. En el menú contextual, haga clic en **Agregar** y después en **Agregar clase**.

1. En el cuadro de diálogo [Agregar clase](../../ide/add-class-dialog-box.md), en el panel **Plantillas**, haga clic en **Componente de páginas Active Server ATL** y después en **Abrir** para mostrar el [Asistente para componentes de páginas Active Server ATL](../../atl/reference/atl-active-server-page-component-wizard.md).

::: moniker-end

## <a name="see-also"></a>Vea también

[Agregar una clase](../../ide/adding-a-class-visual-cpp.md)<br/>
[Adición de una nueva interfaz a un proyecto ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[Agregar puntos de conexión a un objeto](../../atl/adding-connection-points-to-an-object.md)<br/>
[Agregar un método](../../ide/adding-a-method-visual-cpp.md)<br/>
[Clase MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Agregar una clase genérica de C++](../../ide/adding-a-generic-cpp-class.md)
