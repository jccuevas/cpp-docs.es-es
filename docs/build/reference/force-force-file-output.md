---
title: -FORCE (Forzar resultados de archivo) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
dev_langs:
- C++
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95a746a37183f26585fd013327a964b922589221
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699770"
---
# <a name="force-force-file-output"></a>/FORCE (Forzar resultados de archivo)

```
/FORCE:[MULTIPLE|UNRESOLVED]
```

## <a name="remarks"></a>Comentarios

La opción /FORCE indica al vinculador que cree un archivo .exe válido o DLL aunque se haga referencia a un símbolo pero no definida o bien se defina.

La opción/Force puede tomar un argumento opcional:

- Use/Force: Multiple para crear un archivo de salida independientemente de que LINK encuentre más de una definición para un símbolo o no.

- Use/Force: UNRESOLVED para crear un archivo de salida independientemente de que LINK encuentre un símbolo no definido o no. / FORCE: sin resolver se omite si el símbolo de punto de entrada no está resuelto.

/Force sin argumentos implica definiciones múltiples y sin resolver.

Un archivo creado con esta opción puede no funcionar según lo previsto. El vinculador no se vinculará de forma incremental cuando se especifica la opción/Force.

Si se compila un módulo con **/CLR**, **/FORCE** no creará una imagen.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción en el **opciones adicionales** cuadro.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)