---
title: /P (Preprocesar y escribir en un archivo)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFile
- /p
- VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile
helpviewer_keywords:
- /P compiler option [C++]
- -P compiler option [C++]
- P compiler option [C++]
- output files, preprocessor
- preprocessing output files
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
ms.openlocfilehash: 5e1280b404668cebb64afa5a810d769a97bdbf85
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418066"
---
# <a name="p-preprocess-to-a-file"></a>/P (Preprocesar y escribir en un archivo)

Preprocesa archivos de código fuente de C y C++ y escribe el resultado preprocesado en un archivo.

## <a name="syntax"></a>Sintaxis

```
/P
```

## <a name="remarks"></a>Comentarios

El archivo tiene el mismo nombre base que el archivo de origen y una extensión i. En el proceso, las directivas de preprocesador se llevan a cabo, expansiones de macros y se eliminan los comentarios. Para conservar los comentarios en el resultado preprocesado, utilice la [/C (conservar los comentarios durante el preprocesamiento)](../../build/reference/c-preserve-comments-during-preprocessing.md) junto con la opción **/P**.

**/P** agrega `#line` directivas a la salida, al principio y al final de cada archivo incluido y alrededor de las líneas eliminadas por las directivas de preprocesador para la compilación condicional. Estas directivas numeración las líneas del archivo preprocesado. Como resultado, los errores generados durante las fases finales del procesamiento hacen referencia a los números de línea del archivo de origen original en lugar de líneas en el archivo preprocesado. Para suprimir la generación de `#line` directivas, utilice [/EP (Preprocesar para stdout sin directivas #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) como **/P**.

El **/P** opción suprime la compilación. No genera un archivo .obj, incluso si usa [/Fo (nombre del archivo objeto)](../../build/reference/fo-object-file-name.md). Debe volver a enviar el archivo preprocesado para la compilación. **/P** también suprime los archivos de salida desde el **/FA**, **/Fa**, y **/Fm** opciones. Para obtener más información, consulte [/FA, /Fa (archivo de lista)](../../build/reference/fa-fa-listing-file.md) y [/Fm (nombre de archivo de asignaciones)](../../build/reference/fm-name-mapfile.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **preprocesador** página de propiedades.

1. Modificar el **generar archivo preprocesado** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Ejemplo

La siguiente línea de comandos preprocesa `ADD.C`, conserva los comentarios, agrega `#line` directivas y escribe el resultado en un archivo, `ADD.I`:

```
CL /P /C ADD.C
```

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[/Fi (Preprocesar el nombre del archivo de salida)](../../build/reference/fi-preprocess-output-file-name.md)
