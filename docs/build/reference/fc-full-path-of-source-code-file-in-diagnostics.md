---
title: "-FC (ruta de acceso completa del archivo de código fuente en diagnósticos) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
dev_langs: C++
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b055b5431d41bc09fbdd2750c01d3efca8f21287
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC (Ruta de acceso completa de archivo de código fuente en diagnósticos)

Hace que el compilador mostrar la ruta de acceso completa de archivos de código fuente que se pasó al compilador en diagnósticos.

## <a name="syntax"></a>Sintaxis

> /FC

## <a name="remarks"></a>Comentarios

Tenga en cuenta el ejemplo de código siguiente:

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

**/FC** también es necesario si desea ver la ruta de acceso completa de un nombre de archivo cuando se usa el &#95; &#95; ARCHIVO de &#95; &#95; macro.  Vea [Macros predefinidas](../../preprocessor/predefined-macros.md) para obtener más información sobre &#95; &#95; ARCHIVO de &#95; &#95;.

El **/FC** opción está implícito en **/Zi**. Para obtener más información acerca de **/Zi**, consulte [/Z7, / Zi, /ZI (formato de información de depuración)](../../build/reference/z7-zi-zi-debug-information-format.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Expanda el **propiedades de configuración** nodo.

1. Expanda el **C/C++** nodo.

1. Seleccione el **avanzadas** página de propiedades.

1. Modificar el **Use rutas de acceso completas** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)   
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)