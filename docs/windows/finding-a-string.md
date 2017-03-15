---
title: "Finding a String | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.string"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strings [C++], searching"
  - "strings [C++]"
ms.assetid: c2497173-f356-4f77-97d6-f0ac41782510
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Finding a String
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El comando **Buscar en archivos** \(menú **Edición**\) permite buscar una o más cadenas en la tabla de cadenas, así como utilizar [expresiones regulares](../Topic/Using%20Regular%20Expressions%20in%20Visual%20Studio.md) para buscar todas las instancias de cadenas que coincidan con un modelo determinado.  
  
### Para buscar una cadena en la tabla de cadenas  
  
1.  Abra la tabla de cadenas haciendo doble clic en su icono en la [Vista de recursos](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En el menú **Edición**, haga clic en **Buscar y reemplazar** y, a continuación, elija **Buscar**.  
  
3.  En el cuadro **Buscar**, seleccione en la lista desplegable una cadena de búsqueda previamente utilizada o escriba el texto de la leyenda o el identificador de recurso de la cadena que desea encontrar.  
  
4.  Seleccione cualquiera de las opciones de **Buscar**.  
  
5.  Haga clic en **Buscar siguiente**.  
  
    > [!TIP]
    >  Para utilizar expresiones regulares en la búsqueda de archivos, utilice el comando **Buscar en archivos**.  Para que se muestre una lista de expresiones de búsqueda regulares, escriba una expresión regular que tenga que coincidir con un modelo determinado o haga clic en el botón situado a la derecha del cuadro **Buscar**.  Al seleccionar una expresión de esta lista, se usará como texto de búsqueda en el cuadro **Buscar**.  Para utilizar expresiones regulares, la casilla **Usar: Expresiones regulares** deberá estar activada.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados \(los orientados a Common Language Runtime\), vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requisitos**  
  
 Win32  
  
## Vea también  
 [String Editor](../mfc/string-editor.md)   
 [Cadenas](_win32_Strings)   
 [Acerca de cadenas](_win32_About_Strings_cpp)