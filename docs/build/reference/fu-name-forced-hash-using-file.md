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
ms.openlocfilehash: 1a035be2080d9fe407799122f804668e0fc3ce76
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413165"
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

Para obtener información sobre cómo crear un ensamblado o módulo para common language runtime (CLR), consulte [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md). Para obtener información sobre cómo compilar en C++ / c++ / CX, consulte [compilar aplicaciones y bibliotecas](../../cppcx/building-apps-and-libraries-c-cx.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **avanzadas** página de propiedades.

1. Modificar el **Force #using** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](../../build/reference/output-file-f-options.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
