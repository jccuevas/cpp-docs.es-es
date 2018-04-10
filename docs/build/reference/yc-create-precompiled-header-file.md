---
title: -Yc (crear archivo de encabezado precompilado) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
dev_langs:
- C++
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 865b5e0fa7039a0b60f524c2f13a367569757d92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (Crear archivo de encabezado precompilado)
Indica al compilador que cree un archivo de encabezado precompilado (.pch) que representa el estado de compilación en un momento determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
> __/ Yc__
> __/Yc__*nombre de archivo*  
  
  
## <a name="arguments"></a>Argumentos  
*filename*  
 Especifica un archivo de encabezado (. h). Cuando se usa este argumento, el compilador compila todo el código hasta e incluyendo el archivo .h.  
  
## <a name="remarks"></a>Comentarios  
 Cuando **/Yc** se especifica sin un argumento, el compilador compila todo el código hasta el final del archivo de base de código fuente o hasta el punto en el archivo de base donde un [hdrstop](../../preprocessor/hdrstop.md) directiva se produce. El archivo .pch resultante tiene el mismo nombre base que el archivo de base de código fuente a menos que especifique un nombre de archivo diferente mediante la **hdrstop** pragma o **/FP** opción.  
  
 El código precompilado se guarda en un archivo con un nombre creado a partir del nombre base del archivo especificado con el **/Yc** opción y una extensión .pch. También puede usar el  [ /fp (nombre. Archivo de encabezado precompilado)](../../build/reference/fp-name-dot-pch-file.md) opción para especificar un nombre para el archivo de encabezado precompilado.  
  
 Si usa __/Yc__*filename*, el compilador compila todo el código hasta e incluyendo el archivo especificado para su uso posterior con el [/Yu (utilizar el archivo de encabezado precompilado)](../../build/reference/yu-use-precompiled-header-file.md) opción.  
  
 Si las opciones de __/Yc__*filename* y __/Yu__*filename* aparecen en la misma línea de comandos y ambas hacen referencia o implican el mismo nombre de archivo, __/Yc__*filename* tiene prioridad. Esta característica simplifica la escritura de archivos MAKE.  
  
 Para obtener más información sobre encabezados precompilados, vea:  
  
-   [/Y (Encabezados precompilados)](../../build/reference/y-precompiled-headers.md)  
  
-   [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Seleccione un archivo. cpp. El archivo .cpp debe #include el archivo .h que contiene información de encabezado precompilado. El proyecto **/Yc** puede invalidar la configuración en el nivel de archivo.  
  
2.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
3.  Abra la **propiedades de configuración**, **C/C++**, **encabezados precompilados** página de propiedades.  
  
4.  Modificar el **encabezado precompilado** propiedad.  
  
5.  Para establecer el nombre de archivo, modifique la **archivo de encabezado precompilado** propiedad.
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.  
  
## <a name="example"></a>Ejemplo  
 Observe el código siguiente:  
  
```cpp  
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library  
#include "resource.h" // Include resource definitions  
#include "myapp.h"    // Include information specific to this app  
// ...  
```  
  
Cuando se compila este código con el comando `CL /YcMYAPP.H PROG.CPP`, el compilador guarda todo el preprocesamiento de AFXWIN.h, RESOURCE.h y MYAPP.h en un archivo de encabezado precompilado denominado MYAPP.pch.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones de compilador](../../build/reference/setting-compiler-options.md) [crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)