---
title: "Compatibilidad con Unicode en el compilador y el vinculador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.UseUnicodeResponseFiles"
  - "VC.Project.VCLibrarianTool.UseUnicodeResponseFiles"
  - "VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles"
  - "VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unicode, Visual C++"
ms.assetid: acc1d322-56b9-4696-a30e-2af891a4e288
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Compatibilidad con Unicode en el compilador y el vinculador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema, se describe la compatibilidad de Unicode en las herramientas de compilación de Visual C\+\+.  
  
 Nombres de archivo  
 Los nombres de archivo especificados en la línea de comandos o en directivas de compilador \(como \#include\) ahora pueden contener caracteres Unicode.  
  
 Archivos de código fuente  
 Ahora se admiten caracteres Unicode en identificadores, macros, literales de cadena y de carácter, y en comentarios.  También se admiten nombres de carácter universales.  
  
 Se puede utilizar Unicode en un archivo de código fuente con las codificaciones siguientes:  
  
-   UTF\-16 little endian con o sin marca de orden de bytes \(BOM\)  
  
-   UTF\-16 big endian con o sin BOM  
  
-   UTF\-8 con BOM  
  
 Resultados  
 Durante la compilación, el compilador genera diagnósticos en la consola en UTF\-16.  Los caracteres que se pueden mostrar en la consola dependen de las propiedades de ventana de la consola.  Los resultados del compilador redirigidos a un archivo están en la página de códigos ANSI actual de la consola.  
  
 Archivos de respuesta del vinculador y archivos .DEF  
 Los archivos de respuesta y los archivos DEF o pueden ser UTF\-16 con marca de orden de bytes o ANSI.  Previamente, sólo se admitía ANSI.  
  
 Volcados de memoria .asm y .cod  
 Los volcados de memoria .asm y .cod están en ANSI de manera predeterminada, por compatibilidad con MASM.  Use \/FAu para generar UTF\-8.  Tenga en cuenta que, si especifica \/FAs, la fuente entremezclada se imprimirá directamente y podrá aparecer confusa, por ejemplo, si el código fuente es UTF\-8 y no se ha especificado \/FAsu.  
  
 Puede habilitar nombres de archivo Unicode en el entorno de desarrollo \(vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md)\). Para ello, seleccione la herramienta apropiada y elija la propiedad **Habilitar Archivos de respuesta Unicode**, que está habilitada de forma predeterminada.  Una razón para cambiar esta opción predeterminada es si se modifica el entorno de desarrollo para utilizar un compilador que no es compatible con Unicode.  
  
## Vea también  
 [Compilar en la línea de comandos](../../build/building-on-the-command-line.md)