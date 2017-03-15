---
title: "How to: Create a Resource Script File | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rc files, creating"
  - ".rc files, creating"
  - "resource script files, creating"
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# How to: Create a Resource Script File
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  El Editor de recursos no está disponible en las ediciones Express.  
>   
>  Este material se aplica a aplicaciones de escritorio de Windows. Los proyectos en lenguajes .NET no utilizan archivos de script de recursos. Para obtener más información, vea [Archivos de recursos](../mfc/resource-files-visual-studio.md).  
  
### Para crear un nuevo archivo de script de recursos \(.rc\)  
  
1.  Sitúe el foco en la carpeta del proyecto existente en `Solution Explorer`; por ejemplo, "MyProject".  
  
    > [!NOTE]
    >  No confunda la carpeta del proyecto con la carpeta de soluciones del Explorador de soluciones. Si coloca el foco en la carpeta de soluciones, las opciones del cuadro de diálogo **Agregar nuevo elemento** \(en el paso 3\) serán diferentes.  
  
2.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
3.  En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en la carpeta **Visual C\+\+** y elija **Archivo de recursos \(.rc\)** en el panel de la derecha.  
  
4.  Asigne un nombre al archivo de script de recursos en el cuadro de texto **Nombre**y después haga clic en **Abrir**.  
  
 A partir de ese momento, podrá [crear](../windows/how-to-create-a-resource.md) y agregar recursos al archivo .rc.  
  
> [!NOTE]
>  Solo se puede agregar un script de recursos \(archivo .rc\) a un proyecto existente que esté cargado en el IDE de Visual Studio. No es posible crear archivos .rc independientes \(fuera de un proyecto\).[Las plantillas de recursos](../Topic/How%20to:%20Use%20Resource%20Templates.md) \(archivos .rct\) pueden crearse en cualquier momento.  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)