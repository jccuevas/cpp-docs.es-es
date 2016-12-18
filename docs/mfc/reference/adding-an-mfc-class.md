---
title: "Agregar una clase MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.classes.adding.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases [C++], agregar MFC"
  - "MFC, agregar clases"
ms.assetid: 9a96b67f-40bf-43d4-8872-2f8dfc5404f1
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar una clase MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para agregar al proyecto clases derivadas de las clases pertenecientes a la biblioteca MFC \(Microsoft Foundation Class\), use el comando **Agregar clase**, disponible en la [Vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  Especifique el nombre de la nueva clase, seleccione la clase base y después elija el identificador del cuadro de diálogo con el que está asociada \(si procede\).  El asistente de código crea un archivo de encabezado y otro de implementación, y los agrega al proyecto.  
  
> [!NOTE]
>  Se pueden agregar clases MFC a una aplicación COM ATL si inicialmente se [creó una aplicación compatible con MFC](../../atl/reference/mfc-support-in-atl-projects.md).  También se pueden agregar clases MFC a proyectos Win32 que sean compatibles con MFC.  
  
### Para agregar una clase MFC a un proyecto  
  
1.  En la Vista de clases, haga clic con el botón secundario del mouse en el nombre de proyecto.  Haga clic en **Agregar** y a continuación en **Agregar clase** para abrir el cuadro de diálogo [Agregar clase](../../ide/add-class-dialog-box.md).  
  
2.  En el panel Plantillas, seleccione **Clase MFC** y presione el botón **Agregar**.  
  
3.  Defina la configuración de la nueva control en el cuadro de diálogo [Asistente para clases MFC](../../mfc/reference/mfc-add-class-wizard.md).  
  
4.  Haga clic en **Finalizar** para cerrar el asistente y ver la nueva clase en la Vista de clases.  También puede ver los archivos creados por el asistente en el **Explorador de soluciones**.  
  
## Vea también  
 [Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Información general de clases](../../mfc/class-library-overview.md)