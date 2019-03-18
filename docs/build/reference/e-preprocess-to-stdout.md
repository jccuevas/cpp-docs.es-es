---
title: /E (Preprocesar para stdout)
ms.date: 11/04/2016
f1_keywords:
- /e
helpviewer_keywords:
- -E compiler option [C++]
- /E compiler option [C++]
- preprocessor output, copy to stdout
- preprocessor output
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
ms.openlocfilehash: 710be7e1dfc4de89bc1eed3e23e4803c561da10c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817364"
---
# <a name="e-preprocess-to-stdout"></a>/E (Preprocesar para stdout)

Preprocesa archivos de código fuente de C y C++ y copia los archivos preprocesados en el dispositivo de salida estándar.

## <a name="syntax"></a>Sintaxis

```
/E
```

## <a name="remarks"></a>Comentarios

En este proceso, las directivas de preprocesador se llevan a cabo, expansiones de macros y se eliminan los comentarios. Para conservar los comentarios en el resultado preprocesado, utilice la [/C (conservar los comentarios durante el preprocesamiento)](c-preserve-comments-during-preprocessing.md) también la opción del compilador.

**/E** agrega `#line` directivas a los resultados al principio y al final de cada archivo incluido y alrededor de las líneas eliminadas por las directivas de preprocesador para la compilación condicional. Estas directivas numeración las líneas del archivo preprocesado. Como resultado, los errores generados durante las fases finales del procesamiento hacen referencia a los números de línea del archivo de origen original en lugar de líneas en el archivo preprocesado.

El **/E** opción suprime la compilación. Debe volver a enviar el archivo preprocesado para la compilación. **/E** también suprime los archivos de salida desde el **/FA**, **/Fa**, y **/Fm** opciones. Para obtener más información, consulte [/FA, /Fa (archivo de lista)](fa-fa-listing-file.md) y [/Fm (nombre de archivo de asignaciones)](fm-name-mapfile.md).

Para suprimir `#line` directivas, utilice la [/EP (Preprocesar para stdout sin directivas #line)](ep-preprocess-to-stdout-without-hash-line-directives.md) opción en su lugar.

Para enviar el resultado preprocesado en un archivo en lugar de como `stdout`, utilice el [/P (Preprocesar para un archivo)](p-preprocess-to-a-file.md) opción en su lugar.

Para suprimir `#line` directivas y enviar el resultado preprocesado en un archivo, use **/P** y **/EP** juntos.

No se puede usar encabezados precompilados con la **/E** opción.

Tenga en cuenta que cuando se preprocesa en un archivo independiente, no se emiten espacios después de los tokens. Esto puede dar lugar a un programa no válido o tiene efectos secundarios no deseados. El siguiente programa se compila correctamente:

```
#define m(x) x
m(int)main( )
{
   return 0;
}
```

Sin embargo, si se compila con:

```
cl -E test.cpp > test2.cpp
```

`int main` en test2.cpp será incorrectamente `intmain`.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el **opciones adicionales**cuadro.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Ejemplo

La siguiente línea de comandos preprocesa `ADD.C`, conserva los comentarios, agrega `#line` directivas y muestra el resultado en el dispositivo de salida estándar:

```
CL /E /C ADD.C
```

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
