---
title: -FC (ruta de acceso completa del archivo de código fuente en diagnósticos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
dev_langs:
- C++
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d34fe85354d218d2499dbece70964c2e55e2592
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702712"
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

- compiler_option_FC.cpp (5): error C2143: error de sintaxis: falta ';' antes de '}'

Con **/FC**, el texto de diagnóstico tendría un aspecto similar al siguiente texto de diagnóstico:

- c:\test\compiler_option_FC.cpp(5): error C2143: error de sintaxis: falta ';' antes de '}'

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
