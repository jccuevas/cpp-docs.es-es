---
title: Agregar un consumidor OLE DB de ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- OLE DB, adding ATL OLE DB consumer to projects
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
ms.openlocfilehash: d93bf715f8fd8a03c75b1d1bf2e44f12c1d1b9c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261382"
---
# <a name="adding-an-atl-ole-db-consumer"></a>Agregar un consumidor OLE DB de ATL

Use este asistente para agregar un consumidor OLE DB ATL a un proyecto. Un consumidor OLE DB ATL consta de una OLE DB descriptor de acceso clase y enlaces de datos necesarios para tener acceso a un origen de datos. El proyecto se debe haber creado como una aplicación ATL COM o como una aplicación MFC o Win32 que contiene la compatibilidad con ATL (que el Asistente para consumidores OLE DB ATL agrega automáticamente).

> [!NOTE]
> Puede agregar un consumidor OLE DB a un proyecto MFC. Si lo hace, el Asistente para consumidores OLE DB ATL agrega la compatibilidad con COM necesario al proyecto. Esto implica que cuando creó el proyecto MFC, se activó la **controles ActiveX** casilla de verificación (en el **características avanzadas** página de proyecto MFC Application Wizard), que está activada de forma predeterminada. Al seleccionar esta opción garantiza que la aplicación llama a `CoInitialize` y `CoUninitialize`. Si no seleccionó **controles ActiveX** cuando creó el proyecto MFC, deberá llamar a `CoInitialize` y `CoUninitialize` en el código principal.

## <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>Para agregar un consumidor OLE DB ATL al proyecto

1. En **vista de clases**, haga clic en el proyecto. En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar clase**.

1. En la carpeta de Visual C++, haga doble clic en el **consumidores OLE DB ATL** icono o selecciónelo y haga clic en **abierto**.

   Se abre el Asistente para consumidores OLE DB ATL.

1. Definir la configuración como se describe en [el Asistente para consumidores OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).

1. Haga clic en **finalizar** para cerrar el asistente. El código de consumidor OLE DB recién creado se insertará en el proyecto.

## <a name="see-also"></a>Vea también

[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)
