---
title: /WINMDFILE (especificar archivo winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
ms.openlocfilehash: 5d24d1d1aad8442f549dcb1aa4bd6414070c282c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815988"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (especificar archivo winmd)

Especifica el nombre de archivo para el archivo de salida de metadatos en tiempo de ejecución de Windows (.winmd) generado por el [/WINMD](winmd-generate-windows-metadata.md) opción del vinculador.

```
/WINMDFILE:filename
```

## <a name="remarks"></a>Comentarios

Use el valor que se especifica en `filename` para reemplazar el nombre de archivo .winmd predeterminado (`binaryname`.winmd). Tenga en cuenta que no se anexa ".winmd" al `filename`.  Si se muestran varios valores en el **/WINMDFILE** línea de comandos, la última de ellas tiene prioridad.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **vinculador** carpeta.

1. Seleccione el **Windows metadatos** página de propiedades.

1. En el **archivo de metadatos de Windows** , escriba la ubicación del archivo.

## <a name="see-also"></a>Vea también

[/WINMD (Generar metadatos de Windows)](winmd-generate-windows-metadata.md)<br/>
[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
