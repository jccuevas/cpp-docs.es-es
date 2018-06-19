---
title: -P (Preprocesar y escribir en un archivo) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFile
- /p
- VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile
dev_langs:
- C++
helpviewer_keywords:
- /P compiler option [C++]
- -P compiler option [C++]
- P compiler option [C++]
- output files, preprocessor
- preprocessing output files
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26e9d2d63c7244990a047749f15273b45229c7bd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377149"
---
# <a name="p-preprocess-to-a-file"></a>/P (Preprocesar y escribir en un archivo)
Preprocesa archivos de código fuente de C y C++ y escribe el resultado preprocesado en un archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/P  
```  
  
## <a name="remarks"></a>Comentarios  
 El archivo tiene el mismo nombre base que el archivo de origen y una extensión i. En el proceso, todas las directivas de preprocesador se llevan a cabo, expansiones de macros y se eliminan los comentarios. Para conservar los comentarios en el resultado preprocesado, utilice la [/C (conservar los comentarios durante el preprocesamiento)](../../build/reference/c-preserve-comments-during-preprocessing.md) opción junto con **/P**.  
  
 **/P** agrega `#line` directivas a los resultados, al principio y al final de cada archivo incluido y alrededor de las líneas eliminadas por las directivas de preprocesador para la compilación condicional. Estas directivas rehacer la numeración de las líneas del archivo preprocesado. Como resultado, los errores generados durante las fases finales del procesamiento hacen referencia a los números de línea del archivo de origen original en lugar de líneas en el archivo preprocesado. Para suprimir la generación de `#line` directivas, utilice [/EP (Preprocesar para stdout sin directivas #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) como **/P**.  
  
 El **/P** opción suprime la compilación. No genera un archivo .obj, aunque se use [/Fo (nombre del archivo objeto)](../../build/reference/fo-object-file-name.md). Debe volver a enviar el archivo preprocesado para la compilación. **/P** se suprimen los archivos de salida de la **/FA**, **/Fa**, y **/Fm** opciones. Para obtener más información, consulte [/FA, /Fa (Listing File)](../../build/reference/fa-fa-listing-file.md) y [/Fm (Name Mapfile)](../../build/reference/fm-name-mapfile.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **preprocesador** página de propiedades.  
  
4.  Modificar el **generar archivo preprocesado** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.  
  
## <a name="example"></a>Ejemplo  
 La línea de comandos siguiente preprocesa `ADD.C`, conserva los comentarios, agrega `#line` directivas y escribe el resultado en un archivo, `ADD.I`:  
  
```  
CL /P /C ADD.C  
```  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [/Fi (Preprocesar el nombre del archivo de salida)](../../build/reference/fi-preprocess-output-file-name.md)