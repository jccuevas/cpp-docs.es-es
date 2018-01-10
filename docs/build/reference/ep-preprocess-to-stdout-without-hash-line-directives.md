---
title: '-EP (Preprocesar para stdout sin directivas #line) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /ep
- VC.Project.VCCLCompilerTool.GeneratePreprocessedFileNoLines
dev_langs: C++
helpviewer_keywords:
- copy preprocessor output to stdout
- preprocessor output, copy to stdout
- -EP compiler option [C++]
- EP compiler option [C++]
- /EP compiler option [C++]
ms.assetid: 6ec411ae-e33d-4ef5-956e-0054635eabea
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9d7b2a64ec8fa7565d17ab04683fec07c48aea3f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ep-preprocess-to-stdout-without-line-directives"></a>/EP (Preprocesar para stdout sin directivas #line)
Preprocesa archivos de código fuente de C y C++ y copia los archivos preprocesados en el dispositivo de salida estándar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/EP  
```  
  
## <a name="remarks"></a>Comentarios  
 En el proceso, todas las directivas de preprocesador se llevan a cabo, expansiones de macros y se eliminan los comentarios. Para conservar los comentarios en el resultado preprocesado, utilice la [/C (conservar los comentarios durante el preprocesamiento)](../../build/reference/c-preserve-comments-during-preprocessing.md) opción con **/EP**.  
  
 El **/EP** opción suprime la compilación. Debe volver a enviar el archivo preprocesado para la compilación. **/EP** se suprimen los archivos de salida de la **/FA**, **/Fa**, y **/Fm** opciones. Para obtener más información, consulte [/FA, /Fa (Listing File)](../../build/reference/fa-fa-listing-file.md) y [/Fm (Name Mapfile)](../../build/reference/fm-name-mapfile.md).  
  
 Errores generados durante las fases finales del procesamiento hacen referencia a los números de línea del archivo preprocesado en lugar de en el archivo de origen original. Si desea que los números de línea para hacer referencia al archivo de origen original, utilice [/E (Preprocesar para stdout)](../../build/reference/e-preprocess-to-stdout.md) en su lugar. El **/E** opción agrega `#line` directivas a la salida para este propósito.  
  
 Para enviar el resultado preprocesado, con `#line` directivas, en un archivo, use la [/P (Preprocesar para un archivo)](../../build/reference/p-preprocess-to-a-file.md) opción en su lugar.  
  
 Para enviar el resultado preprocesado a stdout, con `#line` directivas, utilice **/P** y **/EP** juntos.  
  
 No puede usar encabezados precompilados con la **/EP** opción.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en el **preprocesador** página de propiedades.  
  
4.  Modificar el **generar archivo preprocesado** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.  
  
## <a name="example"></a>Ejemplo  
 La línea de comandos siguiente preprocesa el archivo `ADD.C`, conserva los comentarios y se muestra el resultado en el dispositivo de salida estándar:  
  
```  
CL /EP /C ADD.C  
```  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)