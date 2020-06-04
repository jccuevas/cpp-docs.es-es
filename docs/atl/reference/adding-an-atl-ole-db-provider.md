---
title: Adición de un proveedor OLE DB ATL
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, adding ATL OLE DB provider to projects
- ATL projects, adding ATL OLE DB providers
- ATL OLE DB providers
ms.assetid: 26fba1e3-880f-4bc6-90e5-2096a48a3a6c
ms.openlocfilehash: 36c07da6249a106836433e127f95258d4ed5b509
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706945"
---
# <a name="adding-an-atl-ole-db-provider"></a>Adición de un proveedor OLE DB ATL

::: moniker range="vs-2019"

El Asistente para proveedores OLE DB ATL no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

Use este asistente para agregar un proveedor OLE DB ATL a un proyecto. Un proveedor OLE DB ATL consta de clases de origen de datos, sesión, comando y conjunto de filas. El proyecto debe haberse creado como aplicación COM de ATL.

## <a name="to-add-an-atl-ole-db-provider-to-your-project"></a>Para agregar un proveedor OLE DB ATL al proyecto

1. En **Vista de clases**, haga clic con el botón derecho en el proyecto. En el menú contextual, haga clic en **Agregar** y después en **Agregar clase**.

1. En la carpeta **Visual C++**, haga doble clic en el icono **Proveedor OLE DB ATL** o selecciónelo y haga clic en **Abrir**.

   Se abre el Asistente para proveedores OLE DB ATL.

1. Defina la configuración tal como se describe en [Asistente para proveedores OLE DB ATL](../../atl/reference/atl-ole-db-provider-wizard.md).

1. Haga clic en **Finalizar** para cerrar el asistente, que insertará el código del proveedor OLE DB recién creado en el proyecto.

::: moniker-end

## <a name="see-also"></a>Vea también

[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)
