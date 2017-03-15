---
title: "/WINMDDELAYSIGN (firmar parcialmente un archivo winmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.WINMDDelaySign"
dev_langs: 
  - "C++"
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /WINMDDELAYSIGN (firmar parcialmente un archivo winmd)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Habilita la firma parcial de un archivo de metadatos en tiempo de ejecución de Windows \(.winmd\) colocando la clave pública del archivo.  
  
```  
  
/WINMDDELAYSIGN[:NO]  
  
```  
  
## Comentarios  
 Es similar a la opción del vinculador [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md) que se aplica al archivo de .winmd.  Utilice **\/WINMDDELAYSIGN** si desea colocar sólo la clave pública del archivo de .winmd.  De forma predeterminada, el vinculador actúa como si **\/WINMDDELAYSIGN:NO** fuera especificado; es decir, no firma el archivo de winmd.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **Vinculador**.  
  
3.  Seleccione la página de propiedades **Metadatos de Windows**.  
  
4.  En el cuadro de lista desplegable de **Retrasar firma de metadatos de Windows** , seleccione la opción que desee.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)