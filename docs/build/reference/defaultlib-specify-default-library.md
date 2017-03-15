---
title: "/DEFAULTLIB (Especificar la biblioteca predeterminada) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.DefaultLibraries"
  - "/defaultlib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DEFAULTLIB (opción del vinculador)"
  - "DEFAULTLIB (opción del vinculador)"
  - "-DEFAULTLIB (opción del vinculador)"
  - "bibliotecas, agregar a una lista de"
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /DEFAULTLIB (Especificar la biblioteca predeterminada)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DEFAULTLIB:library  
```  
  
## Comentarios  
 donde:  
  
 *library*  
 Nombre de una biblioteca en la que buscar a la hora de resolver referencias externas.  
  
## Comentarios  
 La opción \/DEFAULTLIB agrega una biblioteca \(*library*\) a la lista de bibliotecas en las que LINK busca durante la resolución de referencias externas.  La búsqueda en las bibliotecas especificadas con \/DEFAULTLIB se inicia después que en las bibliotecas especificadas en la línea de comandos y antes que en las bibliotecas predeterminadas mencionadas en los archivos .obj.  
  
 La opción \/NODEFAULTLIB \([Omitir todas las bibliotecas predeterminadas](../../build/reference/nodefaultlib-ignore-libraries.md)\) reemplaza a \/DEFAULTLIB:*library*.  La opción \/NODEFAULTLIB:*library* \([Omitir bibliotecas](../../build/reference/nodefaultlib-ignore-libraries.md)\) reemplaza a \/DEFAULTLIB:*library* cuando en las dos se especifique el mismo nombre de biblioteca \(*library*\).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
-   Esta opción del vinculador no está disponible en el entorno de desarrollo de Visual Studio.  Para agregar una biblioteca a la fase de vinculación, deberá utilizarse la propiedad **Dependencias adicionales**, en la página de propiedades **Entrada**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)