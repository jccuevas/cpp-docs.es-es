---
title: -E (Preprocesar para stdout) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /e
dev_langs:
- C++
helpviewer_keywords:
- -E compiler option [C++]
- /E compiler option [C++]
- preprocessor output, copy to stdout
- preprocessor output
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f9105c5c75bc4695d0b00debdff49acf78690b1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="e-preprocess-to-stdout"></a>/E (Preprocesar para stdout)
Preprocesa archivos de código fuente de C y C++ y copia los archivos preprocesados en el dispositivo de salida estándar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/E  
```  
  
## <a name="remarks"></a>Comentarios  
 En este proceso, se realizan todas las directivas de preprocesador, expansiones de macros y se eliminan los comentarios. Para conservar los comentarios en el resultado preprocesado, utilice la [/C (conservar los comentarios durante el preprocesamiento)](../../build/reference/c-preserve-comments-during-preprocessing.md) opción del compilador.  
  
 **/E** agrega `#line` directivas a la salida al principio y al final de cada archivo incluido y alrededor de las líneas eliminadas por las directivas de preprocesador para la compilación condicional. Estas directivas rehacer la numeración de las líneas del archivo preprocesado. Como resultado, los errores generados durante las fases finales del procesamiento hacen referencia a los números de línea del archivo de origen original en lugar de líneas en el archivo preprocesado.  
  
 El **/E** opción suprime la compilación. Debe volver a enviar el archivo preprocesado para la compilación. **/E** se suprimen los archivos de salida de la **/FA**, **/Fa**, y **/Fm** opciones. Para obtener más información, consulte [/FA, /Fa (Listing File)](../../build/reference/fa-fa-listing-file.md) y [/Fm (Name Mapfile)](../../build/reference/fm-name-mapfile.md).  
  
 Suprimir `#line` directivas, utilice la [/EP (Preprocesar para stdout sin directivas #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) opción en su lugar.  
  
 Para enviar el resultado preprocesado a un archivo en lugar de a `stdout`, use la [/P (Preprocesar para un archivo)](../../build/reference/p-preprocess-to-a-file.md) opción en su lugar.  
  
 Suprimir `#line` directivas y enviar el resultado preprocesado a un archivo, use **/P** y **/EP** juntos.  
  
 No puede usar encabezados precompilados con la **/E** opción.  
  
 Tenga en cuenta que, cuando se preprocesa en un archivo independiente, no se emiten espacios después de símbolos (tokens). Esto puede dar lugar a un programa no válido o tiene efectos secundarios imprevistos. El programa siguiente compila correctamente:  
  
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
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción del compilador en el **opciones adicionales**cuadro.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.  
  
## <a name="example"></a>Ejemplo  
 La línea de comandos siguiente preprocesa `ADD.C`, conserva los comentarios, agrega `#line` directivas y se muestra el resultado en el dispositivo de salida estándar:  
  
```  
CL /E /C ADD.C  
```  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)