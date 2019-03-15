---
title: /Gw (optimizar datos globales)
ms.date: 11/04/2016
f1_keywords:
- /Gw
helpviewer_keywords:
- /Gw compiler option [C++]
- -Gw compiler option [C++]
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
ms.openlocfilehash: 5796f353414a021908147bdd2f296ef8e02f69ad
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816911"
---
# <a name="gw-optimize-global-data"></a>/Gw (optimizar datos globales)

Empaquete los datos globales en las secciones COMDAT para la optimización.

## <a name="syntax"></a>Sintaxis

```
/Gw[-]
```

## <a name="remarks"></a>Comentarios

El **/Gw** opción hace que el compilador empaquete los datos globales en secciones individuales de COMDAT. De forma predeterminada, **/Gw** está desactivado y debe habilitarse explícitamente. Para deshabilitarlo explícitamente, utilice **/Gw-**. Cuando ambos **/Gw** y [/GL](gl-whole-program-optimization.md) están habilitados, el vinculador usa la optimización de todo el programa para comparar las secciones COMDAT entre varios archivos objeto con el fin de excluir los datos globales sin referencia o para combinar solo lectura globales datos idénticos. Esto puede reducir significativamente el tamaño del archivo ejecutable binario resultante.

Cuando se compila y vincula por separado, puede usar el [/OPT: ref](opt-optimizations.md) opción del enlazador para excluir del ejecutable los datos globales sin referencia en archivos objeto compilados con la **/Gw** opción.

También puede usar el [/OPT: ICF](opt-optimizations.md) y [/LTCG](ltcg-link-time-code-generation.md) opciones del vinculador juntas para fusionar mediante combinación en el archivo ejecutable cualquier idénticos de solo lectura datos globales entre varios archivos objeto compilados con la **/Gw** opción.

Para obtener más información, consulte [presentación modificador del compilador /Gw](http://blogs.msdn.com/b/vcblog/archive/2013/09/11/introducing-gw-compiler-switch.aspx) en el blog del equipo de Visual C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **C o C++** carpeta.

1. Seleccione el **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir **/Gw** y, a continuación, elija **Aceptar**.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
