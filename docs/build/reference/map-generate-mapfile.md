---
title: /MAP (Generar archivo de asignaciones)
ms.date: 11/04/2016
f1_keywords:
- /map
- VC.Project.VCLinkerTool.MapFileName
- VC.Project.VCLinkerTool.GenerateMapFile
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
ms.openlocfilehash: 9a45fd5ea44b8908e77f847275bde42b86385cdb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321610"
---
# <a name="map-generate-mapfile"></a>/MAP (Generar archivo de asignaciones)

```
/MAP[:filename]
```

## <a name="arguments"></a>Argumentos

*filename*<br/>
Un nombre especificado por el usuario para el archivo de asignaciones. Reemplaza el nombre predeterminado.

## <a name="remarks"></a>Comentarios

La opción /MAP indica al vinculador que cree un archivo de asignaciones.

De forma predeterminada, el vinculador nombres asignaciones con el nombre base del programa y la extensión de Map. El elemento opcional *filename* le permite invalidar el nombre predeterminado para un archivo de asignaciones.

Un archivo de asignaciones es un archivo de texto que contiene la siguiente información sobre el programa que se están vinculando:

- El nombre del módulo, que es el nombre base del archivo

- La marca de tiempo desde el encabezado del archivo de programa (no del sistema de archivos)

- Una lista de grupos en el programa, con la dirección de inicio de cada grupo (como *sección*:*desplazamiento*), longitud, el nombre del grupo y la clase

- Una lista de símbolos públicos, con cada dirección (como *sección*:*desplazamiento*), nombre, dirección plana y archivo .obj donde se define el símbolo de símbolos

- El punto de entrada (como *sección*:*desplazamiento*)

El [/MAPINFO](mapinfo-include-information-in-mapfile.md) opción especifica información adicional que se incluirán en el archivo de asignaciones.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **depurar** página de propiedades.

1. Modificar el **generar archivo de asignaciones** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
