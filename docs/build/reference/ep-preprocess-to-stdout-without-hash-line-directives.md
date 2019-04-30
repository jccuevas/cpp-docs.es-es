---
title: '/EP (Preprocesar para stdout sin directivas #line)'
ms.date: 11/04/2016
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
ms.openlocfilehash: 49745b644234c0e5ce92661f14304531aaca5c69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293256"
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP (Preprocesar para stdout sin directivas #line)

Preprocesa archivos de código fuente de C y C++ y copia los archivos preprocesados en el dispositivo de salida estándar.

## <a name="syntax"></a>Sintaxis

```
/EP
```

## <a name="remarks"></a>Comentarios

En el proceso, las directivas de preprocesador se llevan a cabo, expansiones de macros y se eliminan los comentarios. Para conservar los comentarios en el resultado preprocesado, utilice la [/C (conservar los comentarios durante el preprocesamiento)](c-preserve-comments-during-preprocessing.md) opción con **/EP**.

El **/EP** opción suprime la compilación. Debe volver a enviar el archivo preprocesado para la compilación. **/EP** también suprime los archivos de salida desde el **/FA**, **/Fa**, y **/Fm** opciones. Para obtener más información, consulte [/FA, /Fa (archivo de lista)](fa-fa-listing-file.md) y [/Fm (nombre de archivo de asignaciones)](fm-name-mapfile.md).

Errores generados durante las fases finales del procesamiento hacen referencia a los números de línea del archivo preprocesado en lugar de un archivo de origen. Si desea que los números de línea para hacer referencia al archivo de origen original, utilice [/E (Preprocesar para stdout)](e-preprocess-to-stdout.md) en su lugar. El **/E** opción agrega `#line` directivas a la salida para este propósito.

Para enviar el resultado preprocesado, con `#line` directivas, en un archivo, utilice el [/P (Preprocesar para un archivo)](p-preprocess-to-a-file.md) opción en su lugar.

Para enviar el resultado preprocesado a stdout, con `#line` directivas, utilice **/P** y **/EP** juntos.

No se puede usar encabezados precompilados con la **/EP** opción.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **preprocesador** página de propiedades.

1. Modificar el **generar archivo preprocesado** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Ejemplo

La siguiente línea de comandos preprocesa el archivo `ADD.C`, conserva los comentarios y muestra el resultado en el dispositivo de salida estándar:

```
CL /EP /C ADD.C
```

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
