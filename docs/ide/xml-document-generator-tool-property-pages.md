---
title: "Herramienta Generador de documentos XML (P&#225;ginas de propiedades) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCXDCMakeTool.ValidateIntelliSense"
  - "VC.Project.VCXDCMakeTool.SuppressStartupBanner"
  - "VC.Project.VCXDCMakeTool.DocumentLibraryDependencies"
  - "VC.Project.VCXDCMakeTool.OutputDocumentFile"
  - "VC.Project.VCXDCMakeTool.AdditionalDocumentFiles"
dev_langs: 
  - "C++"
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Herramienta Generador de documentos XML (P&#225;ginas de propiedades)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La página de propiedades de la herramienta Generador de documentos XML expone la funcionalidad de xdcmake.exe.  Xdcmake.exe combina archivos .xdc en un archivo .xml cuando su código fuente contiene comentarios de documentación y [\/doc \(procesar comentarios de documentación\)](../build/reference/doc-process-documentation-comments-c-cpp.md).  Vea [Etiquetas recomendadas para comentarios de documentación](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) para obtener información sobre cómo agregar comentarios de documentación al código fuente.  
  
> [!NOTE]
>  Las opciones de xdcmake.exe en el entorno de desarrollo \(páginas de propiedades\) difieren de las opciones de uso de xdcmake.exe en la línea de comandos.  Para obtener información sobre cómo utilizar xdcmake.exe en la línea de comandos, vea [XDCMake \(Referencia\)](../ide/xdcmake-reference.md).  
  
## Lista de UIElement  
 **Suprimir la pancarta de inicio**  
 Suprime el mensaje de copyright.  
  
 **Archivos de documento adicionales**  
 Directorios adicionales en los que desea que el sistema de proyectos busque archivos .xdc.  xdcmake siempre buscará archivos .xdc generados por el proyecto.  Se puede especificar varios directorios.  
  
 **Archivo de documento de resultados**  
 Nombre y ubicación del directorio del archivo de salida .xml.  Vea [Macros para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md) para obtener información sobre cómo utilizar macros para especificar ubicaciones de directorio.  
  
 **Dependencias de biblioteca de documentos**  
 Si el proyecto tiene un dependencia de un proyecto .lib en la solución, puede procesar archivos .xdc del proyecto .lib en archivos .xml para el proyecto actual.  
  
## Vea también  
 [Páginas de propiedades](../ide/property-pages-visual-cpp.md)   
 [Páginas de propiedades](../ide/property-pages-visual-cpp.md)