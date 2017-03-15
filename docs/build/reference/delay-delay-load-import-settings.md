---
title: "/DELAY (Configuraci&#243;n de las importaciones de carga retrasada) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/delay"
  - "VC.Project.VCLinkerTool.DelayNoBind"
  - "VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL"
  - "VC.Project.VCLinkerTool.DelayUnload"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DELAY (opción del vinculador)"
  - "DELAY (opción del vinculador)"
  - "-DELAY (opción del vinculador)"
  - "carga retrasada de archivos DLL, /DELAY (opción)"
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /DELAY (Configuraci&#243;n de las importaciones de carga retrasada)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DELAY:UNLOAD  
/DELAY:NOBIND  
```  
  
## Comentarios  
 La opción \/DELAY controla la [carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md) de DLL:  
  
-   El calificador UNLOAD le indica a la función auxiliar de carga retrasada que admita la descarga explícita de la DLL.  La tabla de direcciones de importación \(IAT\) se restablece a su forma original. Al hacerlo, invalida los punteros de IAT y hace que se sobrescriban.  
  
     Si no elige UNLOAD, las llamadas a [FUnloadDelayLoadedDLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md) no se realizarán correctamente.  
  
-   El calificador NOBIND le indica al enlazador que no incluya una IAT enlazable en la imagen final.  Con la configuración predeterminada, se crea la IAT enlazable para las DLL de carga retrasada.  La imagen resultante no se puede enlazar de manera estática.  \(Las imágenes con IAT enlazables se pueden enlazar de forma estática antes de la ejecución\). Consulte [\/BIND](../../build/reference/bind.md).  
  
     Si la DLL está enlazada, la función auxiliar tratará de usar la información enlazada en lugar de llamar a [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx) en cada una de las importaciones a las que se haga referencia.  Si la marca de tiempo o la dirección preferida no coinciden con las de la DLL cargada, la función auxiliar supondrá que la IAT enlazada no está actualizada y actuará como si la IAT enlazada no existiera.  
  
     NOBIND aumenta el tamaño de la imagen del programa, pero puede reducir el tiempo de carga de la DLL.  Si nunca trata de enlazar la DLL, NOBIND impedirá que se genere la IAT enlazada.  
  
 Para especificar las DLL de la carga retrasada, utilice la opción [\/DELAYLOAD](../../build/reference/delayload-delay-load-import.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda **Propiedades de configuración** y **Vinculador** y, luego, elija **Avanzadas**.  
  
3.  Modifique la propiedad **DLL de carga retrasada**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)