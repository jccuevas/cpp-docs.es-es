---
title: "/DELAYLOAD (Retrasar importaci&#243;n de carga) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/delayload"
  - "VC.Project.VCLinkerTool.DelayLoadDLLS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DELAYLOAD (opción del vinculador)"
  - "carga retrasada de archivos DLL, /DELAYLOAD (opción)"
  - "DELAYLOAD (opción del vinculador)"
  - "-DELAYLOAD (opción del vinculador)"
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /DELAYLOAD (Retrasar importaci&#243;n de carga)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DELAYLOAD:dllname  
  
```  
  
## Parámetros  
 `dllname`  
 Nombre de un archivo DLL cuya carga se desea retrasar.  
  
## Comentarios  
 La opción \/DELAYLOAD hace que el archivo DLL especificado por `dllname` se cargue solo en la primera llamada del programa a una función en ese archivo DLL.  Para obtener más información, vea [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md).  Puede usar esta opción tantas veces como sea necesario para especificar todos los archivos DLL que desee.  Debe utilizar Delayimp.lib cuando enlace el programa o puede implementar su propia función auxiliar de retraso de carga.  
  
 La opción [\/DELAY](../../build/reference/delay-delay-load-import-settings.md) especifica las opciones de enlace y carga para cada archivo DLL de carga retrasada.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  En la carpeta **Vinculador**, seleccione la página de propiedades **Entrada**.  
  
3.  Modifique la propiedad **Archivos DLL de carga retrasada**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)