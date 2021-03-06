---
title: /FORCE (Forzar resultados de archivo)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
ms.openlocfilehash: d1d85174290faa95e73c63a25f7d80c554e83ace
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079628"
---
# <a name="force-force-file-output"></a>/FORCE (Forzar resultados de archivo)

```
/FORCE:[MULTIPLE|UNRESOLVED]
```

## <a name="remarks"></a>Observaciones

La opción/FORCE indica al enlazador que cree un archivo. exe o DLL válido incluso si se hace referencia a un símbolo pero no se define o se define de forma múltiple.

La opción/FORCE puede tomar un argumento opcional:

- Use/FORCE: MULTIPLE para crear un archivo de salida independientemente de que LINK Encuentre o no más de una definición para un símbolo.

- Use/FORCE: unresolved para crear un archivo de salida independientemente de que LINK Encuentre o no un símbolo no definido. /FORCE: unresolved se omite si el símbolo del punto de entrada no está resuelto.

/FORCE sin argumentos implica tanto varios como sin resolver.

Es posible que un archivo creado con esta opción no se ejecute según lo esperado. El enlazador no vinculará de forma incremental cuando se especifique la opción/FORCE.

Si un módulo se compila con **/CLR**, **/Force** no creará una imagen.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Haga clic con el botón derecho en el proyecto en **Explorador de soluciones** y elija **propiedades**.

1. Haga clic en la carpeta **Enlazador**.

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción en el cuadro **opciones adicionales** .

Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Consulte también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
