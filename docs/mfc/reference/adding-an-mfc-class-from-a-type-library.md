---
title: "Agregar una clase MFC desde una biblioteca de tipos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases [C++], agregar MFC"
  - "MFC, agregar clases desde bibliotecas de tipos"
  - "bibliotecas de tipos, agregar clases MFC"
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar una clase MFC desde una biblioteca de tipos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Use este asistente para crear una clase MFC a partir de una interfaz de una biblioteca de tipos disponible.  Puede agregar una clase MFC a una [aplicación MFC](../../mfc/reference/creating-an-mfc-application.md), una [DLL de MFC](../../mfc/reference/creating-an-mfc-dll-project.md) o un [control ActiveX de MFC](../../mfc/reference/creating-an-mfc-activex-control.md).  
  
> [!NOTE]
>  No es necesario crear un proyecto MFC con la automatización habilitada para poder agregar una clase desde una biblioteca de tipos.  
  
 Una biblioteca de tipos contiene una descripción binaria de las interfaces expuestas por un componente, que define los métodos junto con sus parámetros y los tipos devueltos.  La biblioteca de tipos debe estar registrada para que pueda mostrarse en la lista **Bibliotecas de tipos disponibles** del cuadro de diálogo Asistente para agregar clases de la biblioteca de tipos.  Para obtener más información, vea "Dentro de COM distribuido: bibliotecas de tipos e integración del lenguaje" en MSDN Library.  
  
### Para agregar una clase MFC desde una biblioteca de tipos  
  
1.  En el **Explorador de soluciones** o en la [Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925), haga clic con el botón secundario del mouse en el nombre del proyecto al que desee agregar la clase.  
  
2.  En el menú contextual, haga clic en **Agregar** y, después, en **Agregar clase**.  
  
3.  En el panel Plantillas del cuadro de diálogo [Agregar clase](../../ide/add-class-dialog-box.md), haga clic en **Clase MFC de TypeLib** y después seleccione **Abrir**. Se ejecuta el [Asistente para agregar clases de la biblioteca de tipos](../../mfc/reference/add-class-from-typelib-wizard.md).  
  
 En el asistente puede agregar más de una clase a una biblioteca de tipos.  De igual forma, puede agregar clases de más de una biblioteca de tipos en la misma sesión del asistente.  
  
 El asistente crea una clase MFC, derivada de [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), para cada interfaz que se agregue desde la biblioteca de tipos seleccionada.  `COleDispatchDriver` implementa el cliente de la automatización OLE.  
  
## Vea también  
 [Clientes de automatización](../../mfc/automation-clients.md)   
 [Clientes de automatización: Usar bibliotecas de tipos](../../mfc/automation-clients-using-type-libraries.md)