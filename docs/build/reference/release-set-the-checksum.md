---
title: "/RELEASE (Establecer la suma de comprobaci&#243;n) | Microsoft Docs"
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
  - "/release"
  - "VC.Project.VCLinkerTool.SetChecksum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/RELEASE (opción del vinculador)"
  - "configuración de suma de comprobación"
  - "RELEASE (opción del vinculador)"
  - "-RELEASE (opción del vinculador)"
ms.assetid: 93bcadf4-29ac-4824-914b-6997e3751d22
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /RELEASE (Establecer la suma de comprobaci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/RELEASE  
```  
  
## Comentarios  
 La opción \/RELEASE establece la suma de comprobación en el encabezado de un archivo .exe.  
  
 El sistema operativo requiere la suma de comprobación para los controladores de dispositivo.  La suma de comprobación se establece en las versiones de lanzamiento de controladores de dispositivo a fin de garantizar la compatibilidad con futuros sistemas operativos.  
  
 La opción \/RELEASE se establece de forma predeterminada cuando se especifica la opción [\/SUBSYSTEM:NATIVE](../../build/reference/subsystem-specify-subsystem.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Avanzadas**.  
  
4.  Modifique la propiedad **Establecer suma de comprobación**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SetChecksum%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)