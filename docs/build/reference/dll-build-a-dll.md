---
title: /DLL (Compilar un archivo DLL)
ms.date: 11/04/2016
f1_keywords:
- /dll
helpviewer_keywords:
- -DLL linker option
- /DLL linker option [C++]
- exporting DLLs [C++], specifying exports
- DLLs [C++], building
- DLL linker option [C++]
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
ms.openlocfilehash: 71696e4ffae91ed1fa8a13e69e75523ce66e8361
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546349"
---
# <a name="dll-build-a-dll"></a>/DLL (Compilar un archivo DLL)

```
/DLL
```

## <a name="remarks"></a>Comentarios

La opción /DLL genera un archivo DLL como el archivo de salida principal. Normalmente, un archivo DLL contiene exportaciones que se pueden usar otro programa. Hay tres métodos para especificar exportaciones, aparece en el orden recomendado de uso:

1. [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) en el código fuente

1. Un [exportaciones](../../build/reference/exports.md) instrucción en un archivo .def

1. Un [/EXPORT](../../build/reference/export-exports-a-function.md) especificación en un comando LINK

Un programa puede usar más de un método.

Es otra manera de generar un archivo DLL con la **biblioteca** instrucción de definición de módulo. Las opciones /BASE y /DLL juntos son equivalentes a la **biblioteca** instrucción.

No se especifica esta opción en el entorno de desarrollo; Esta opción es para su uso solo en la línea de comandos. Esta opción se establece cuando se crea un proyecto DLL con un Asistente para aplicaciones.

Tenga en cuenta que si crea la biblioteca de importación en un paso preliminar, antes de crear el archivo .dll, debe pasar el mismo conjunto de archivos de objeto al compilar el archivo .dll, que se pasa al compilar la biblioteca de importación.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **propiedades de configuración** carpeta.

1. Haga clic en el **General** página de propiedades.

1. Modificar el **configuración tipo** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)