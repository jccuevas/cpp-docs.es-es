---
title: "/DRIVER (Controlador de modo kernel de Windows NT) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.driver"
  - "/driver"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DRIVER (opción del vinculador)"
  - "DRIVER (opción del vinculador)"
  - "-DRIVER (opción del vinculador)"
  - "controlador de modo kernel"
ms.assetid: aeee8e28-5d97-40f5-ba16-9f370fe8a1b8
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /DRIVER (Controlador de modo kernel de Windows NT)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DRIVER[:UPONLY | :WDM]  
```  
  
## Comentarios  
 Use la opción \/DRIVER para compilar un controlador modo kernel de Windows NT.  
  
 La palabra clave **\/DRIVER:UPONLY** hace que el vinculador agregue el bit **IMAGE\_FILE\_UP\_SYSTEM\_ONLY** a las características del encabezado de resultados para especificar que se trata de un controlador monoprocesador \(UP\).  El sistema operativo rechazará la carga de un controlador de este tipo en un sistema multiprocesador.  
  
 La palabra clave **\/DRIVER:WDM** hace que el vinculador establezca el bit **IMAGE\_DLLCHARACTERISTICS\_WDM\_DRIVER** en el campo DllCharacteristics del encabezado opcional.  
  
 Si no se especifica **\/DRIVER**, el vinculador no establece estos bits.  
  
 Si se especifica **\/DRIVER**:  
  
-   \/FIXED:NO está activa \([\/FIXED \(Dirección base fija\)](../../build/reference/fixed-fixed-base-address.md)\).  
  
-   La extensión del archivo de salida será .sys.  Utilice **\/OUT** para cambiar la extensión y el nombre de archivo predeterminados \([\/OUT \(Nombre del archivo de resultados\)](../../build/reference/out-output-file-name.md)\).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Sistema**.  
  
4.  Modifique la propiedad **Driver**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea `P:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.driver`.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)