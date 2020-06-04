---
title: /VERSION (Información de versión)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Version
- /version
helpviewer_keywords:
- -VERSION linker option
- Version Information linker option
- version numbers, specifying in .exe
- /VERSION linker option
- VERSION linker option
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
ms.openlocfilehash: 626461fc7a9fc6dd7b6578e836733d154a66862a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316501"
---
# <a name="version-version-information"></a>/VERSION (Información de versión)

```
/VERSION:major[.minor]
```

## <a name="arguments"></a>Argumentos

*principales* y *secundaria*<br/>
El número de versión que desee en el encabezado del archivo .exe o .dll.

## <a name="remarks"></a>Comentarios

La opción /VERSION indica al enlazador que agregue un número de versión en el encabezado del archivo .exe o .dll. Utilizar DUMPBIN [/HEADERS](headers.md) para ver el campo de versión de imagen de los valores de encabezado opcional para ver el efecto de/Version.

El *principales* y *menores* argumentos son números decimales comprendidos en el intervalo entre 0 y 65.535. El valor predeterminado es la versión 0.0.

La información especificada con /VERSION no afecta a la información de versión que aparece para una aplicación cuando ve sus propiedades en el Explorador de archivos. Esa información de versión procede de un archivo de recursos que se usa para compilar la aplicación. Consulte [Editor de la información de versión](../../windows/version-information-editor.md) para obtener más información.

Es otra manera de insertar un número de versión con el [versión](version-c-cpp.md) instrucción de definición de módulo.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **General** página de propiedades.

1. Modificar el **versión** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
