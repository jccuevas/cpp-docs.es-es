---
title: "How to: Open a Resource Script File Outside of a Project (Standalone) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.resource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resources [Visual Studio], viewing"
  - "rc files, viewing resources"
  - ".rc files, viewing resources"
  - "resource script files, viewing resources"
ms.assetid: bc350c60-178d-4c5d-9a7e-6576b0c936e4
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Open a Resource Script File Outside of a Project (Standalone)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede ver los recursos en un archivo .rc sin tener un proyecto abierto.  El archivo .rc se abrirá en una ventana de documento en lugar de abrirse en la ventana de la [Vista de recursos](../windows/resource-view-window.md) \(como ocurre cuando el archivo se abre dentro de un proyecto\).  
  
> [!NOTE]
>  Esta distinción es importante porque algunos comandos solo están disponibles cuando el archivo se abre de forma independiente \(fuera de un proyecto\).  Por ejemplo, solo puede guardar un archivo en un formato diferente o como un nombre de archivo diferente cuando el archivo se abre fuera de un proyecto \(el comando **Guardar como** no está disponible cuando se abre un archivo dentro de un proyecto\).  
  
### Para abrir un archivo .rc fuera de un proyecto  
  
1.  En el menú **Archivo**, seleccione **Abrir** y, a continuación, haga clic en **Archivo**.  
  
2.  En el cuadro de diálogo **Abrir archivo**, navegue hasta al archivo de script de recursos que desee ver, resalte el archivo y, a continuación, haga clic en **Abrir**.  
  
    > [!NOTE]
    >  Si abre primero el proyecto \(**Archivo**, **Abrir**, **Proyecto**\), algunos comandos no estarán disponibles para usted.  Abrir un archivo "independiente" significa abrir sin cargar primero el proyecto.  
  
 Para abrir y ver el archivo de recursos en formato de texto, consulte el archivo [Editar un script de recursos \(.rc\)](../windows/how-to-open-a-resource-script-file-in-text-format.md).  
  
#### Para abrir varios archivos .rc fuera de un proyecto  
  
1.  Abra ambos archivos de recursos de manera independiente.  Por ejemplo, abra Source1.rf y Source2.rc.  
  
    1.  En el menú **Archivo**, seleccione **Abrir** y, a continuación, haga clic en **Archivo**.  
  
    2.  En el cuadro de diálogo **Abrir archivo**, navegue hasta el primer archivo de script de recursos que desee abrir \(Source 1.rc\), resalte el archivo y haga clic en **Abrir**.  
  
    3.  Repita el paso anterior para abrir el segundo archivo .rc \(Source2.rc\).  
  
         Los archivos .rc ahora están abiertos en ventanas de documentos independientes.  
  
2.  Cuando los archivos .rc estén abiertos, coloque las ventanas en mosaico para poder verlos simultáneamente:  
  
    -   Desde el menú **Ventana**, elija **Nuevo grupo de tabulación horizontal** o **Nuevo grupo de tabulación vertical**.  
  
         o bien  
  
    -   Haga clic con el botón derecho en uno de los archivos .rc y en el menú contextual elija **Nuevo grupo de tabulación horizontal** o **Nuevo grupo de tabulación vertical**.  
  
> [!NOTE]
>  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener más información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, consulte [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
### Requisitos  
 Win32  
  
## Vea también  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)