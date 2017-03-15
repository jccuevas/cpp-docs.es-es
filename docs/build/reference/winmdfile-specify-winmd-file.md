---
title: "/WINMDFILE (especificar archivo winmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.GenerateWindowsMetadataFile"
dev_langs: 
  - "C++"
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /WINMDFILE (especificar archivo winmd)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica el nombre de archivo para el archivo de salida de los metadatos en tiempo de ejecución de Windows \(.winmd\) generado por la opción del vinculador [\/WINMD](../../build/reference/winmd-generate-windows-metadata.md) .  
  
```  
  
/WINMDFILE:filename  
  
```  
  
## Comentarios  
 Utilice el valor especificado en `filename` para invalidar el nombre de archivo predeterminado .winmd \(`binaryname`.winmd\).  Observe que no anexa “.winmd” a `filename`.  Si varios valores aparecen en la línea de comandos de **\/WINMDFILE** , la última tiene prioridad.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **Vinculador**.  
  
3.  Seleccione la página de propiedades **Metadatos de Windows**.  
  
4.  En el cuadro de **Archivos de metadatos de Windows** , escriba la ubicación del archivo.  
  
## Vea también  
 [\/WINMD \(generar metadatos de Windows\)](../../build/reference/winmd-generate-windows-metadata.md)   
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)