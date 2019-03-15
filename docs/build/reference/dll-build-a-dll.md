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
ms.openlocfilehash: 5f7907d659ee3bedc590b88320df03edce005b06
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820512"
---
# <a name="dll-build-a-dll"></a>/DLL (Compilar un archivo DLL)

```
/DLL
```

## <a name="remarks"></a>Comentarios

La opción /DLL genera un archivo DLL como el archivo de salida principal. Normalmente, un archivo DLL contiene exportaciones que se pueden usar otro programa. Hay tres métodos para especificar exportaciones, aparece en el orden recomendado de uso:

1. [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) en el código fuente

1. Un [exportaciones](exports.md) instrucción en un archivo .def

1. Un [/EXPORT](export-exports-a-function.md) especificación en un comando LINK

Un programa puede usar más de un método.

Es otra manera de generar un archivo DLL con la **biblioteca** instrucción de definición de módulo. Las opciones /BASE y /DLL juntos son equivalentes a la **biblioteca** instrucción.

No se especifica esta opción en el entorno de desarrollo; Esta opción es para su uso solo en la línea de comandos. Esta opción se establece cuando se crea un proyecto DLL con un Asistente para aplicaciones.

Tenga en cuenta que si crea la biblioteca de importación en un paso preliminar, antes de crear el archivo .dll, debe pasar el mismo conjunto de archivos de objeto al compilar el archivo .dll, que se pasa al compilar la biblioteca de importación.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **propiedades de configuración** carpeta.

1. Haga clic en el **General** página de propiedades.

1. Modificar el **configuración tipo** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
