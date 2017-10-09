---
title: Agregar un consumidor OLE DB de ATL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- OLE DB, adding ATL OLE DB consumer to projects
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: c55726a1728185f699afbac4ba68a6dc0f70c2bf
ms.openlocfilehash: 41e31e82c97252a2ab5e34a78db5af1fd4e24f98
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="adding-an-atl-ole-db-consumer"></a>Agregar un consumidor OLE DB de ATL
Use este asistente para agregar un consumidor OLE DB ATL a un proyecto. Un consumidor OLE DB ATL está formada por una OLE DB descriptor de acceso (clase) y enlaces de datos necesarios para tener acceso a un origen de datos. El proyecto se debe haber creado como una aplicación ATL COM o como una aplicación MFC o Win32 que tenga compatibilidad con ATL (que el Asistente para consumidores OLE DB ATL agrega de forma automática).  
  
 **Tenga en cuenta** puede agregar un consumidor OLE DB a un proyecto MFC. Si lo hace, el Asistente para consumidores OLE DB ATL agrega la compatibilidad con COM necesario al proyecto. Esto implica que cuando creó el proyecto MFC, se activó la **controles ActiveX** casilla de verificación (en el **características avanzadas** página del Asistente para aplicaciones MFC), que está activada de forma predeterminada. Al seleccionar esta opción garantiza que la aplicación llama a **CoInitialize** y **CoUninitialize**. Si no ha seleccionado **controles ActiveX** al crear el proyecto MFC, debe llamar a **CoInitialize** y **CoUninitialize** en el código principal.  
  
### <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>Para agregar un consumidor OLE DB ATL al proyecto  
  
1.  En la vista de clases, haga clic en el proyecto. En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar clase**.  
  
2.  En la carpeta Visual C++, haga doble clic en el **consumidores OLE DB ATL** icono o selecciónelo y haga clic en **abiertos**.  
  
     Se abre el Asistente para consumidores OLE DB ATL.  
  
3.  Defina la configuración como se describe en [el Asistente para consumidores OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).  
  
4.  Haga clic en **finalizar** para cerrar el asistente. El código de consumidor OLE DB recién creado se insertará en el proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Agregar funcionalidad con los asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)


