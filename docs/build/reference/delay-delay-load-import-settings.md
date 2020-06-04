---
title: /DELAY (Configuración de las importaciones de carga retrasada)
ms.date: 11/04/2016
f1_keywords:
- /delay
- VC.Project.VCLinkerTool.DelayNoBind
- VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL
- VC.Project.VCLinkerTool.DelayUnload
helpviewer_keywords:
- delayed loading of DLLs, /DELAY option
- DELAY linker option
- /DELAY linker option
- -DELAY linker option
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
ms.openlocfilehash: ef6f5f768cf86f470d1322fa2a7bee6db794c2ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493005"
---
# <a name="delay-delay-load-import-settings"></a>/DELAY (Configuración de las importaciones de carga retrasada)

```
/DELAY:UNLOAD
/DELAY:NOBIND
```

## <a name="remarks"></a>Comentarios

La opción/DELAY controla la [carga retrasada](linker-support-for-delay-loaded-dlls.md) de archivos dll:

- El calificador UNLOAD le indica a la función del asistente de carga retrasada que admita la descarga explícita de la DLL. La tabla de direcciones de importación (IAT) se restablece a su forma original. Al hacerlo, invalida los punteros de IAT y hace que se sobrescriban.

   Si no selecciona Descargar, se producirá un error en cualquier llamada a [FUnloadDelayLoadedDLL](explicitly-unloading-a-delay-loaded-dll.md) .

- El calificador NOBIND le indica al enlazador que no incluya una IAT enlazable en la imagen final. Con la configuración predeterminada, se crea la IAT enlazable para las DLL de carga retrasada. La imagen resultante no se puede enlazar de manera estática. (Las imágenes con IAT enlazables se pueden enlazar de forma estática antes de la ejecución). Vea [/BIND](bind.md).

   Si el archivo DLL está enlazado, la función auxiliar intentará usar la información enlazada en lugar de llamar a [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) en cada una de las importaciones a las que se hace referencia. Si la marca de tiempo o la dirección preferida no coinciden con las de la DLL cargada, la función del asistente supondrá que la IAT enlazada no está actualizada y actuará como si la IAT enlazada no existiera.

   NOBIND aumenta el tamaño de la imagen del programa, pero puede reducir el tiempo de carga de la DLL. Si nunca trata de enlazar la DLL, NOBIND impedirá que se genere la IAT enlazada.

Para especificar los archivos dll de carga retrasada, use la opción [/DELAYLOAD](delayload-delay-load-import.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [ C++ establecer las propiedades del compilador y compilación en Visual Studio](../working-with-project-properties.md).

1. Expanda **propiedades de configuración**, **vinculador**y, a continuación, seleccione **avanzadas**.

1. Modifique la propiedad **dll de carga retrasada** .

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
