---
title: '/FU (Asignar nombre al archivo #using obligatorio)'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
ms.openlocfilehash: c47a45208ac5b5c7e0000516ed114c008feda7ca
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807541"
---
# <a name="fu-name-forced-using-file"></a>/FU (Asignar nombre al archivo #using obligatorio)

Una opción del compilador que puede usar como una alternativa para pasar un nombre de archivo a [#using](../../preprocessor/hash-using-directive-cpp.md) en el código fuente.

## <a name="syntax"></a>Sintaxis

> **/FU** *file*

## <a name="arguments"></a>Argumentos

*file*<br/>
Especifica el archivo de metadatos que hace referencia en esta compilación.

## <a name="remarks"></a>Comentarios

El modificador /FU toma un único nombre de archivo. Para especificar varios archivos, use /FU con cada uno de ellos.

Si usas C++ / c++ / CLI y se hace referencia a los metadatos para que utilicen el [ensamblados de confianza](../../dotnet/friend-assemblies-cpp.md) característica, no se puede usar **/FU**. Debe hacer referencia a los metadatos en el código mediante el uso de `#using`, junto con el `[as friend]` atributo. Ensamblados de confianza no se admiten en extensiones de componentes de C++ de Visual C++ / c++ / CX.

Para obtener información sobre cómo crear un ensamblado o módulo para common language runtime (CLR), consulte [/CLR (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md). Para obtener información sobre cómo compilar en C++ / c++ / CX, consulte [compilar aplicaciones y bibliotecas](../../cppcx/building-apps-and-libraries-c-cx.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **avanzadas** página de propiedades.

1. Modificar el **Force #using** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](output-file-f-options.md)<br/>
[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
