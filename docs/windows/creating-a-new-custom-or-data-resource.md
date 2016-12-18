---
title: "Creating a New Custom or Data Resource | Microsoft Docs"
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
  - "vc.editors.binary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "custom resources [C++]"
  - "data resources [C++]"
  - "resources [Visual Studio], creating"
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating a New Custom or Data Resource
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para crear un nuevo recurso personalizado o de datos, coloque el recurso en un archivo independiente con sintaxis de archivo de script de recursos \(.rc\) normal y luego incluya ese archivo haciendo clic con el botón secundario en el proyecto en el Explorador de soluciones y haciendo clic en **Archivos de inclusión de recursos** en el menú contextual.  
  
### Para crear un nuevo recurso personalizado o de datos  
  
1.  [Cree un archivo .rc](../windows/how-to-create-a-resource-script-file.md) que contenga el recurso personalizado o de datos.  
  
     Puede escribir datos personalizados en un archivo .rc como cadenas entre comillas terminadas en null o como enteros en formato octal, hexadecimal o decimal.  
  
2.  Enel  **Explorador de soluciones**, haga clic con el botón secundario en el archivo .rc del proyecto y luego haga clic en **Archivos de inclusión de recursos** en el menú contextual.  
  
3.  En el cuadro **Directivas de tiempo de compilación** escriba una instrucción **\#include** que ofrece el nombre del archivo que contiene el recurso personalizado. Por ejemplo:  
  
    ```  
    #include mydata.rc  
    ```  
  
     Asegúrese de que la sintaxis y la ortografía de lo que escribe son correctas. El contenido del cuadro **Directivas de tiempo de compilación** se insertan en el archivo de script de recursos exactamente como lo escribió.  
  
4.  Haga clic en **Aceptar** para registrar sus cambios.  
  
 Otra forma de crear un recurso personalizado es importar un archivo externo como recurso personalizado. Para más información, vea [Importación y exportación de recursos](../windows/how-to-import-and-export-resources.md).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [Binary Editor](../mfc/binary-editor.md)