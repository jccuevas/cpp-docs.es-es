---
title: -WINMDFILE (especificar archivo de winmd) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
dev_langs:
- C++
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d34bdfd2d80690efae8efbc1f95ba0c50a530af3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425789"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (especificar archivo winmd)

Especifica el nombre de archivo para el archivo de salida de metadatos en tiempo de ejecución de Windows (.winmd) generado por el [/WINMD](../../build/reference/winmd-generate-windows-metadata.md) opción del vinculador.

```
/WINMDFILE:filename
```

## <a name="remarks"></a>Comentarios

Use el valor que se especifica en `filename` para reemplazar el nombre de archivo .winmd predeterminado (`binaryname`.winmd). Tenga en cuenta que no se anexa ".winmd" al `filename`.  Si se muestran varios valores en el **/WINMDFILE** línea de comandos, la última de ellas tiene prioridad.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **vinculador** carpeta.

1. Seleccione el **Windows metadatos** página de propiedades.

1. En el **archivo de metadatos de Windows** , escriba la ubicación del archivo.

## <a name="see-also"></a>Vea también

[/WINMD (Generar metadatos de Windows)](../../build/reference/winmd-generate-windows-metadata.md)<br/>
[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)