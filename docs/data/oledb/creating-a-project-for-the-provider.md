---
title: Crear un proyecto para un proveedor
ms.date: 10/22/2018
helpviewer_keywords:
- ATL projects, creating
- OLE DB providers, projects
- projects [C++], creating
ms.assetid: 076a75de-1d4b-486a-bcf8-9c0f6b049fa2
ms.openlocfilehash: dc085b1f663369033947ed2a5577f334dd79c0aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362014"
---
# <a name="creating-a-project-for-the-provider"></a>Crear un proyecto para un proveedor

## <a name="to-create-a-project-in-which-the-ole-db-provider-will-reside"></a>Para crear un proyecto en el que residirá el proveedor OLE DB

1. En el menú **Archivo**, haga clic en **Nuevo** y después haga clic en **Proyecto**.

   Aparecerá el cuadro de diálogo **Nuevo proyecto** .

1. En el **tipos de proyecto** panel, haga clic en el **instalado** > **Visual C++** > **MFC/ATL** carpeta. En el **plantillas** panel, haga clic en **proyecto ATL**.

    > [!NOTE]
    > En versiones anteriores de Visual Studio, busque el tipo de proyecto en **instalado** > **plantillas** > **Visual C++**  >  **ATL**.

1. En el **nombre** cuadro, escriba un nombre para el proyecto y, a continuación, haga clic en **Aceptar**.

   El **Asistente para proyectos ATL** aparece.

1. En el **Asistente para proyectos ATL**, elija **biblioteca de vínculos dinámicos (DLL)** para **tipo de aplicación**.

1. Haga clic en **Finalizar**.

## <a name="see-also"></a>Vea también

[Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)