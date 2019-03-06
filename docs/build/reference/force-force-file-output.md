---
title: /FORCE (Forzar resultados de archivo)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
ms.openlocfilehash: fb5b5b586a9c428d20a7e931a312c8903eb6e8e2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424475"
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
