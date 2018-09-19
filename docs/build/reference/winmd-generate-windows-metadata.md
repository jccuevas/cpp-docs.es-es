---
title: -WINMD (generar metadatos de Windows) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
dev_langs:
- C++
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25b8b34e55fc0814653f4c44be50e545633be373
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705736"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (generar metadatos de Windows)

Habilita la generación de un archivo de metadatos en tiempo de ejecución de Windows (.winmd).

```
/WINMD[:{NO|ONLY}]
```

## <a name="remarks"></a>Comentarios

**/ WINMD**<br/>
La configuración predeterminada para aplicaciones de la plataforma Universal de Windows. El vinculador genera el archivo ejecutable binario y el archivo de metadatos de winmd.

**/WINMD:NO**<br/>
El vinculador genera solo el archivo ejecutable binario, pero no es un archivo winmd.

**/ WINMD: SOLO**<br/>
El vinculador genera solo el archivo .winmd, pero no el archivo ejecutable binario.

De forma predeterminada, el nombre de archivo de salida tiene el formato `binaryname`.winmd. Para especificar un nombre de archivo diferente, use el [/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md) opción.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **vinculador** carpeta.

1. Seleccione el **Windows metadatos** página de propiedades.

1. En el **generar metadatos de Windows** lista desplegable, seleccione la opción que desee.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)