---
title: "Agregar un consumidor OLE DB ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "consumidores OLE DB ATL"
  - "ATL projects, agregar consumidores OLE DB ATL"
  - "OLE DB, agregar un consumidor OLE DB ATL a proyectos"
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Agregar un consumidor OLE DB ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Use este asistente para agregar un consumidor OLE DB ATL a un proyecto.  Un consumidor OLE DB ATL está formado por una clase de descriptor de acceso OLE DB y los enlaces de datos necesarios para el acceso a un origen de datos.  El proyecto debe haberse creado como una aplicación ATL COM, o bien como una aplicación MFC o Win32 que tenga compatibilidad con ATL \(que agrega de forma automática el Asistente para consumidores OLE DB ATL\).  
  
 **Note** puede agregar un consumidor OLE DB a un proyecto MFC.  Si lo hace, el Asistente para consumidores OLE DB ATL agrega al proyecto el código necesario para la compatibilidad con COM.  Esto implica que, al crear el proyecto MFC, se activó la casilla **Controles ActiveX** \(en la página **Características avanzadas** del Asistente para aplicaciones MFC\), que está activada de forma predeterminada.  Al activar esta opción, se asegura que la aplicación llama a **CoInitialize** y **CoUninitialize**.  Si no activó la casilla **Controles ActiveX** al crear el proyecto MFC, deberá llamar a **CoInitialize** y **CoUninitialize** en el código principal.  
  
### Para agregar un consumidor OLE DB ATL a un proyecto  
  
1.  En la Vista de clases, haga clic con el botón secundario del mouse en el proyecto.  En el menú contextual, haga clic en **Agregar** y, después, en **Agregar clase**.  
  
2.  En la carpeta Visual C\+\+, haga doble clic en el icono **Consumidor OLE DB ATL** o bien selecciónelo y haga clic en **Abrir**.  
  
     Se abre el Asistente para consumidores OLE DB ATL.  
  
3.  Defina la configuración que se describe en el [Asistente para consumidores OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).  
  
4.  Haga clic en **Finalizar** para cerrar el asistente.  Se inserta en el proyecto el código del consumidor OLE DB recién creado.  
  
## Vea también  
 [Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)