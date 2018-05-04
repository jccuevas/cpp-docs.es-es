---
title: -DELAY (configuración de importación de carga retrasada) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /delay
- VC.Project.VCLinkerTool.DelayNoBind
- VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL
- VC.Project.VCLinkerTool.DelayUnload
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, /DELAY option
- DELAY linker option
- /DELAY linker option
- -DELAY linker option
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c898727504a8ae530bcdffb3e01bde68c31c8e87
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="delay-delay-load-import-settings"></a>/DELAY (Configuración de las importaciones de carga retrasada)
```  
/DELAY:UNLOAD  
/DELAY:NOBIND  
```  
  
## <a name="remarks"></a>Comentarios  
 La opción /DELAY controla [carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md) de archivos DLL:  
  
-   El calificador UNLOAD le indica a la función auxiliar de carga retrasada que admita la descarga explícita de la DLL. La tabla de direcciones de importación (IAT) se restablece a su forma original. Al hacerlo, invalida los punteros de IAT y hace que se sobrescriban.  
  
     Si no se selecciona UNLOAD, las llamadas a [FUnloadDelayLoadedDLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md) se producirá un error.  
  
-   El calificador NOBIND le indica al enlazador que no incluya una IAT enlazable en la imagen final. Con la configuración predeterminada, se crea la IAT enlazable para las DLL de carga retrasada. La imagen resultante no se puede enlazar de manera estática. (Las imágenes con IAT enlazables se pueden enlazar de forma estática antes de la ejecución). Vea [/enlazar](../../build/reference/bind.md).  
  
     Si la DLL está enlazada, la función auxiliar intentará utilizar la información de enlace en lugar de llamar [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx) en cada una de las importaciones que se hace referencia. Si la marca de tiempo o la dirección preferida no coinciden con las de la DLL cargada, la función auxiliar supondrá que la IAT enlazada no está actualizada y actuará como si la IAT enlazada no existiera.  
  
     NOBIND aumenta el tamaño de la imagen del programa, pero puede reducir el tiempo de carga de la DLL. Si nunca trata de enlazar la DLL, NOBIND impedirá que se genere la IAT enlazada.  
  
 Para especificar archivos DLL para carga retrasada, utilice la [/DELAYLOAD](../../build/reference/delayload-delay-load-import.md) opción.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda **propiedades de configuración**, **vinculador**y, a continuación, seleccione **avanzadas**.  
  
3.  Modificar el **DLL de carga retrasada** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)