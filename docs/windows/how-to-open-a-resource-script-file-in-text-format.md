---
title: "How to: Open a Resource Script File in Text Format | Microsoft Docs"
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
  - "resource script files, opening in text format"
  - ".rc files, opening in text format"
  - "rc files, opening in text format"
ms.assetid: 0bc57527-f53b-40c9-99a9-4dcbc5c9af57
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Open a Resource Script File in Text Format
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede haber ocasiones en que desee ver el contenido del archivo de script de recursos \(.rc\) del proyecto sin abrir un recurso, como un cuadro de diálogo, en su editor de recursos específico.  Por ejemplo, es posible que desee buscar una cadena en todos los cuadros de diálogo del archivo de recursos sin tener que abrir cada uno de ellos independientemente.  
  
> [!NOTE]
>  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
 Puede abrir fácilmente el archivo de recursos en formato de texto para ver todos los recursos que contiene y realizar operaciones globales admitidas por el [Editor de texto](http://msdn.microsoft.com/es-es/508e1f18-99d5-48ad-b5ad-d011b21c6ab1).  
  
> [!NOTE]
>  Los editores de recursos no leen directamente los archivos .rc o resource.h.  El compilador de recursos los compila en archivos .aps, que son utilizados por los editores de recursos.  Este archivo es un paso de compilación y solamente almacena datos simbólicos.  Como en un proceso de compilación normal, la información que no es simbólica \(por ejemplo, los comentarios\) se descarta durante el proceso de compilación.  Siempre que el archivo .aps se desincroniza con el archivo .rc, este se vuelve a generar \(por ejemplo, al guardar, el editor de recursos sobrescribe los archivos .rc y resource.h\).  Los cambios realizados en los propios recursos permanecerán en el archivo .rc, pero siempre se perderán los comentarios una vez que se sobrescriba el archivo .rc.  Para obtener información sobre cómo conservar los comentarios, vea [Incluir recursos en tiempo de compilación](../Topic/How%20to:%20Include%20Resources%20at%20Compile%20Time.md).  
  
### Para abrir un archivo de script de recursos como texto  
  
1.  En el menú **Archivo**, seleccione **Abrir** y, a continuación, haga clic en **Archivo**.  
  
2.  En el cuadro de diálogo **Abrir archivo**, vaya al archivo de script de recursos que desee ver en formato de texto.  
  
3.  Resalte el archivo, haga clic en la flecha desplegable del botón **Abrir** \(que se encuentra a la derecha del botón\).  
  
4.  Seleccione **Abrir con** en el menú desplegable.  
  
5.  En el cuadro de diálogo **Abrir con**, haga clic en **Editor de código fuente \(texto\)**.  
  
6.  En la lista desplegable **Abrir como**, seleccione **Texto**.  
  
     El recurso se abre en el editor de código fuente.  
  
 o bien  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en el archivo .rc.  
  
2.  En el menú contextual, seleccione **Abrir con...** y, a continuación, seleccione **Editor de código fuente \(texto\)**.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, consulte [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)