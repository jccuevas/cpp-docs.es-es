---
title: "/WINMD (generar metadatos de Windows) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.GenerateWindowsMetadata"
dev_langs: 
  - "C++"
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /WINMD (generar metadatos de Windows)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Habilita la generación de un archivo de metadatos en tiempo de ejecución de Windows \(.winmd\).  
  
```  
  
/WINMD[:{NO|ONLY}]  
```  
  
## Comentarios  
 \/WINMD  
 La configuración predeterminada para las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] .  El vinculador genera el archivo ejecutable binario y el archivo de metadatos de .winmd.  
  
 \/WINMD:NO  
 El vinculador genera sólo el archivo ejecutable binario, pero no un archivo de .winmd.  
  
 \/WINMD:ONLY  
 El vinculador genera sólo el archivo de .winmd, pero no el archivo ejecutable binario.  
  
 De forma predeterminada, el nombre del archivo de salida tiene el formato `binaryname`.winmd.  Para especificar un nombre de archivo diferente, utilice la opción de [\/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md) .  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **Vinculador**.  
  
3.  Seleccione la página de propiedades **Metadatos de Windows**.  
  
4.  En el cuadro de lista desplegable de **Generar metadatos de Windows** , seleccione la opción que desee.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)