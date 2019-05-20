---
title: Adición de un consumidor OLE DB ATL
ms.date: 05/09/2019
helpviewer_keywords:
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
ms.openlocfilehash: 1e384a283a2a149faa5b8d6e0817eac3cacfeff9
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706919"
---
# <a name="adding-an-atl-ole-db-consumer"></a>Adición de un consumidor OLE DB ATL

::: moniker range="vs-2019"

El Asistente para proveedores OLE DB ATL no está disponible en Visual Studio 2019 ni en versiones posteriores. Puede seguir agregando la funcionalidad manualmente. Para obtener más información, consulte [Crear un consumidor sin utilizar un asistente](../../data/oledb/creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=vs-2017"

Use este asistente para agregar un consumidor OLE DB ATL a un proyecto. Un consumidor OLE DB ATL consta de una clase de descriptor de acceso OLE DB y enlaces de datos necesarios para obtener acceso a un origen de datos. El proyecto debe haberse creado como aplicación COM de ATL o como aplicación MFC o Win32 que contiene compatibilidad ATL (que el Asistente para consumidores OLE DB ATL agrega automáticamente).

> [!NOTE]
> Puede agregar un consumidor OLE DB a un proyecto MFC. Si lo hace, el Asistente para consumidores OLE DB ATL agrega la compatibilidad con COM necesaria al proyecto. Esto implica que cuando creó el proyecto MFC, activó la casilla **Controles ActiveX** (en la página **Características avanzadas** del Asistente para aplicaciones del proyecto MFC), que está activada de forma predeterminada. Al seleccionarse esta opción se garantiza que la aplicación llame a `CoInitialize` y `CoUninitialize`. Si no activó **Controles ActiveX** cuando creó el proyecto MFC, debe llamar a `CoInitialize` y `CoUninitialize` en su código principal.

## <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>Para agregar un consumidor OLE DB ATL al proyecto

1. En **Vista de clases**, haga clic con el botón derecho en el proyecto. En el menú contextual, haga clic en **Agregar** y después en **Agregar clase**.

1. En la carpeta Visual C++, haga doble clic en el icono **Consumidor OLE DB ATL** o selecciónelo y haga clic en **Abrir**.

   Se abre el Asistente para consumidores OLE DB ATL.

1. Defina la configuración tal como se describe en [Asistente para consumidores OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).

1. Haga clic en **Finalizar** para cerrar el asistente. El código del consumidor OLE DB recién creado se insertará en el proyecto.

::: moniker-end

## <a name="see-also"></a>Vea también

[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)
