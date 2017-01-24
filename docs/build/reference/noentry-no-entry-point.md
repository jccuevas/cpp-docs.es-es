---
title: "/NOENTRY (Sin punto de entrada) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.ResourceOnlyDLL"
  - "/noentry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/NOENTRY (opción del vinculador) [C++]"
  - "DLL [C++], crear"
  - "puntos de entrada [C++], especificación de vinculador"
  - "NOENTRY (opción del vinculador)"
  - "-NOENTRY (opción del vinculador)"
  - "DLL sólo de recursos [C++], crear"
ms.assetid: 0214dd41-35ad-43ab-b892-e636e038621a
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /NOENTRY (Sin punto de entrada)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/NOENTRY  
```  
  
## Comentarios  
 La opción \/NOENTRY es necesaria para la creación de un archivo DLL solo de recursos que contenga código no ejecutable.  Para obtener más información, vea [Crear un archivo DLL de recursos](../../build/creating-a-resource-only-dll.md).  
  
 Se utiliza para evitar que LINK vincule una referencia con `_main` en la DLL.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **Vinculador**.  
  
3.  Seleccione la página de propiedades **Avanzadas**.  
  
4.  Modifique la propiedad **Ningún punto de entrada**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>.  
  
## Vea también  
 [Crear un archivo DLL de recursos](../../build/creating-a-resource-only-dll.md)   
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)