---
title: "/FORCE (Forzar resultados de archivo) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.ForceLink"
  - "/force"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FORCE (opción del vinculador)"
  - "archivo de resultados del vinculador"
  - "FORCE (opción del vinculador)"
  - "-FORCE (opción del vinculador)"
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FORCE (Forzar resultados de archivo)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/FORCE:[MULTIPLE|UNRESOLVED]  
```  
  
## Comentarios  
 La opción \/FORCE le indica al vinculador que cree una DLL o archivo .exe válidos, independientemente de que se haga referencia a un símbolo sin definir o definido de forma múltiple.  
  
 Esta opción puede aceptar argumentos opcionales:  
  
-   Use \/FORCE:MULTIPLE para crear un archivo de salida independientemente de que LINK encuentre o no más de una definición para un símbolo.  
  
-   Use \/FORCE:UNRESOLVED para crear un archivo de salida independientemente de que LINK encuentre o no un símbolo no definido. \/FORCE:UNRESOLVED se omite si el símbolo del punto de entrada no está resuelto.  
  
 \/FORCE sin argumentos implica definiciones múltiples y sin resolver.  
  
 La ejecución de archivos creados con esta opción podría causar resultados imprevistos.  Si la opción \/FORCE está especificada, el vinculador no vinculará de forma incremental  
  
 Si un módulo se compila con **\/clr**, **\/FORCE** no se creará una imagen.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)