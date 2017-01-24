---
title: "/WINMDKEYFILE (especificar archivo de clave winmd) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.WINMDKeyFile"
dev_langs: 
  - "C++"
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /WINMDKEYFILE (especificar archivo de clave winmd)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica una clave o un par clave para firmar un archivo de metadatos en tiempo de ejecución de Windows \(.winmd\).  
  
```  
  
/WINMDKEYFILE:filename  
  
```  
  
## Comentarios  
 Es similar a la opción del vinculador [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) que se aplica a un archivo de .winmd.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **Vinculador**.  
  
3.  Seleccione la página de propiedades **Metadatos de Windows**.  
  
4.  En el cuadro de **Archivo de clave de metadatos de Windows** , escriba la ubicación del archivo.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)