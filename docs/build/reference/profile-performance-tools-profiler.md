---
title: "/PROFILE (Generador de perfiles de Herramientas de rendimiento) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.Profile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/PROFILE (opción del vinculador)"
  - "-PROFILE (opción del vinculador)"
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /PROFILE (Generador de perfiles de Herramientas de rendimiento)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genera un archivo de salida que se puede utilizar con el Generador de perfiles de Herramientas de rendimiento.  
  
## Sintaxis  
  
```  
/PROFILE  
```  
  
## Comentarios  
 \/PROFILE implica las opciones del vinculador siguientes:  
  
-   [\/OPT:REF](../../build/reference/opt-optimizations.md)  
  
-   \/OPT:NOICF  
  
-   [\/INCREMENTAL:NO](../../build/reference/incremental-link-incrementally.md)  
  
-   [\/FIXED:NO](../../build/reference/fixed-fixed-base-address.md)  
  
 \/PROFILE hace que el vinculador genere una sección de reubicación en la imagen del programa.  Una sección de reubicación permite al generador de perfiles transformar la imagen del programa para obtener los datos del perfil.  
  
 **\/PROFILE** sólo está disponible en versiones Enterprise \(desarrollo en equipo\).  Para obtener más información sobre PREfast, vea [Análisis de código para obtener información general de C\/C\+\+](../Topic/Code%20Analysis%20for%20C-C++%20Overview.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **Vinculador**.  
  
4.  Seleccione la página de propiedades **Avanzadas**.  
  
5.  Modifique la propiedad **Perfil**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)