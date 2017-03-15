---
title: "/NOLOGO (Suprimir el titular de inicio) (Vinculador) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.SuppressStartupBanner"
  - "/nologo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/NOLOGO (opción del vinculador)"
  - "titulares, suprimir inicio"
  - "mensaje de copyright"
  - "NOLOGO (opción del vinculador)"
  - "-NOLOGO (opción del vinculador)"
  - "suprimir el titular de inicio (opción del vinculador)"
  - "números de versión, impedir la presentación del vinculador"
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /NOLOGO (Suprimir el titular de inicio) (Vinculador)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/NOLOGO  
```  
  
## Comentarios  
 La opción \/NOLOGO impide que se muestre el mensaje de copyright y el número de versión.  
  
 También suprime la repetición de los archivos de comandos.  Para obtener más información, vea [Archivos de comandos de LINK](../../build/reference/link-command-files.md).  
  
 De forma predeterminada, el vinculador envía esta información a la Ventana de salida.  En la línea de comandos, la información se envía a la salida estándar y puede redirigirse a un archivo.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Esta opción sólo debe utilizarse desde la línea de comandos.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Esta opción del vinculador no puede variarse por medio de programación.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)