---
title: -MAP (Generar archivo de asignaciones) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /map
- VC.Project.VCLinkerTool.MapFileName
- VC.Project.VCLinkerTool.GenerateMapFile
dev_langs:
- C++
helpviewer_keywords:
- mapfiles, creating linker
- generate mapfile linker option
- mapfile linker option
- mapfiles, information about program being linked
- MAP linker option
- -MAP linker option
- mapfiles, specifying file name
- /MAP linker option
ms.assetid: 9ccce53d-4e36-43da-87b0-7603ddfdea63
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10f4b23cf8f1c05fb8bd196dc9a6cd54971b1572
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="map-generate-mapfile"></a>/MAP (Generar archivo de asignaciones)
```  
/MAP[:filename]  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 *filename*  
 Un nombre especificado por el usuario para el archivo de asignaciones. Reemplaza el nombre predeterminado.  
  
## <a name="remarks"></a>Comentarios  
 La opción/MAP indica al vinculador para crear un archivo de asignaciones.  
  
 De forma predeterminada, el vinculador nombres el archivo de asignaciones con el nombre base del programa y la extensión de Map. Opcional *filename* le permite invalidar el nombre predeterminado de un archivo de asignaciones.  
  
 Un archivo de asignaciones es un archivo de texto que contiene la siguiente información sobre el programa que se están vinculando:  
  
-   El nombre del módulo, que es el nombre base del archivo  
  
-   La marca de tiempo desde el encabezado del archivo de programa (no del sistema de archivos)  
  
-   Una lista de grupos en el programa, con la dirección inicial de cada grupo (como *sección*:*desplazamiento*), longitud, el nombre del grupo y la clase  
  
-   Una lista de símbolos públicos, junto con cada dirección (como *sección*:*desplazamiento*), nombre, dirección plana y archivo .obj donde esté definido el símbolo de símbolos  
  
-   El punto de entrada (como *sección*:*desplazamiento*)  
  
 El [/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md) opción especifica información adicional que se incluirá en el archivo de asignaciones.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en el **depurar** página de propiedades.  
  
4.  Modificar el **generar archivo de asignaciones** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)