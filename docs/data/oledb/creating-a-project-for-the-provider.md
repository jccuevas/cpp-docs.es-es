---
title: Crear un proyecto para un proveedor | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, creating
- OLE DB providers, projects
- projects [C++], creating
ms.assetid: 076a75de-1d4b-486a-bcf8-9c0f6b049fa2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 86f85b95b4b45624a778bc183cabadda886d002d
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990092"
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