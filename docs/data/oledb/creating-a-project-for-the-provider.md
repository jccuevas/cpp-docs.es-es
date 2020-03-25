---
title: Crear un proyecto para un proveedor
ms.date: 10/22/2018
helpviewer_keywords:
- ATL projects, creating
- OLE DB providers, projects
- projects [C++], creating
ms.assetid: 076a75de-1d4b-486a-bcf8-9c0f6b049fa2
ms.openlocfilehash: f2ff42ba8a2e908f672db7e96fc9f24f51a1fd9b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211411"
---
# <a name="creating-a-project-for-the-provider"></a>Crear un proyecto para un proveedor

## <a name="to-create-a-project-in-which-the-ole-db-provider-will-reside"></a>Para crear un proyecto en el que residirá el proveedor de OLE DB

1. En el menú **Archivo**, haga clic en **Nuevo** y en **Proyecto**.

   Aparecerá el cuadro de diálogo **Nuevo proyecto** .

1. En el panel **tipos de proyecto** , haga clic en la carpeta **instalado** > **Visual C++**  > **MFC/ATL** . En el panel **plantillas** , haga clic en **proyecto ATL**.

    > [!NOTE]
    > En versiones anteriores de Visual Studio, busque el tipo de proyecto en **instalado** > **plantillas** > **Visual C++**  > **ATL**.

1. En el cuadro **nombre** , escriba un nombre para el proyecto y, a continuación, haga clic en **Aceptar**.

   Aparece el **Asistente para proyectos ATL** .

1. En el **Asistente para proyectos ATL**, elija **biblioteca de vínculos dinámicos (dll)** como **tipo de aplicación**.

1. Haga clic en **Finalizar**

## <a name="see-also"></a>Consulte también

[Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
