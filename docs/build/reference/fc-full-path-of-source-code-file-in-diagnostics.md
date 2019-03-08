---
title: /FC (Ruta de acceso completa de archivo de código fuente en diagnósticos)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
ms.openlocfilehash: 96809f09efd068b80f04a70d4356c1ceaf5f113c
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422486"
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC (Ruta de acceso completa de archivo de código fuente en diagnósticos)

Hace que el compilador mostrar la ruta de acceso completa de los archivos de código fuente pasados al compilador en diagnósticos.

## <a name="syntax"></a>Sintaxis

> /FC

## <a name="remarks"></a>Comentarios

Tenga en cuenta el siguiente ejemplo de código:

```cpp
// compiler_option_FC.cpp
int main( ) {
   int i   // C2143
}
```

Sin **/FC**, el texto de diagnóstico tendría un aspecto similar al siguiente texto de diagnóstico:

- compiler_option_FC.cpp(5) : error C2143: syntax error : missing ';' before '}'

Con **/FC**, el texto de diagnóstico tendría un aspecto similar al siguiente texto de diagnóstico:

- c:\test\compiler_option_fc.cpp(5) : error C2143: syntax error : missing ';' before '}'

**/FC** también es necesario si desea ver la ruta de acceso completa de un nombre de archivo cuando se usa el &#95; &#95;archivo&#95; &#95; macro. Consulte [Predefined Macros](../../preprocessor/predefined-macros.md) para obtener más información sobre &#95; &#95;archivo&#95;&#95;.

El **/FC** opción está implícita en **/Zi**. Para obtener más información acerca de **/Zi**, consulte [/Z7, / Zi, /ZI (formato de la información de depuración)](../../build/reference/z7-zi-zi-debug-information-format.md).

**/FC** da como resultado las rutas de acceso completas en minúsculas.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **avanzadas** página de propiedades.

1. Modificar el **rutas de acceso completas** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
