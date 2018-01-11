---
title: -Yu (utilizar el archivo de encabezado precompilado) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /yu
dev_langs: C++
helpviewer_keywords:
- Yu compiler option [C++]
- /Yu compiler option [C++]
- -Yu compiler option [C++]
- PCH files, use existing
- .pch files, use existing
- precompiled header files, use existing
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c83f159882b9ed6fcfe5557c150413303c401dda
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="yu-use-precompiled-header-file"></a>/Yu (Utilizar el archivo de encabezado precompilado)
Indica al compilador que utilice un archivo de encabezado precompilado (.pch) existente en la compilación actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/Yu[filename]  
```  
  
## <a name="arguments"></a>Argumentos  
 *filename*  
 El nombre de un archivo de encabezado que se incluye en el archivo de código fuente mediante una **#include** directiva de preprocesador.  
  
## <a name="remarks"></a>Comentarios  
 El nombre del archivo de inclusión debe ser el mismo para ambos el **/Yc** opción que crea el encabezado precompilado y los posteriores **/Yu** opción que indique el uso del encabezado precompilado.  
  
 Para **/Yc**, `filename` especifica el punto en que precompilación se detiene; el compilador precompila todo el código aunque `filename` y nombres de encabezado precompilado resultante con el nombre base del archivo de inclusión y una extensión pch.  
  
 El archivo .pch debe haberse creado con **/Yc**.  
  
 El compilador trata todo el código que se producen antes del archivo .h como precompilado. Salta hasta justo después del **#include** directiva asociada con el archivo. h, usa el código incluido en el archivo .pch y, a continuación, compila todo el código después de `filename`.  
  
 En la línea de comandos, no se permiten espacios entre **/Yu** y `filename`.  
  
 Cuando se especifica la **/Yu** opción sin un nombre de archivo, el programa de origen debe contener un [#pragma hdrstop](../../preprocessor/hdrstop.md) pragma que especifica el nombre de archivo del encabezado precompilado, archivo .pch. En este caso, el compilador utilizará el encabezado precompilado (archivo .pch) especificado mediante  [ /fp (nombre. Archivo de encabezado precompilado)](../../build/reference/fp-name-dot-pch-file.md). El compilador salta hasta la ubicación del pragma, restaura el estado compilado del archivo de encabezado precompilado especificado por la directiva pragma y, a continuación, compila solamente el código que sigue a la directiva pragma. Si **#pragma hdrstop** no especifica un nombre de archivo, el compilador busca un archivo con un nombre derivado del nombre base del archivo de origen con una extensión .pch. También puede usar el **/FP** opción para especificar un archivo PCH diferentes.  
  
 Si especifica la **/Yu** opción sin un nombre de archivo y no especifica un **hdrstop** pragma, se genera un mensaje de error y la compilación se realiza correctamente.  
  
 Si el **/Yc** `filename` y **/Yu** `filename` opciones se producen en la misma línea de comandos y ambas hacen referencia el mismo nombre de archivo, **/Yc** `filename` toma prioridad, precompila todo el código hasta e incluyendo el archivo con nombre. Esta característica simplifica la escritura de archivos MAKE.  
  
 Dado que los archivos .pch contienen información sobre el entorno del equipo, así como información de dirección de memoria acerca del programa, solo se debe utilizar un archivo de encabezado precompilado en el equipo donde se creó.  
  
 Para obtener más información sobre encabezados precompilados, vea:  
  
-   [/Y (encabezados precompilados)](../../build/reference/y-precompiled-headers.md)  
  
-   [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Especifique [/Yc (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md) en un archivo .cpp del proyecto.  
  
2.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
3.  Haga clic en la carpeta **C/C++** .  
  
4.  Haga clic en el **encabezados precompilados** página de propiedades.  
  
5.  Modificar el **crear o utilizar encabezado Precompilado a través del archivo** propiedad o el **crear o utilizar encabezado precompilado** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.  
  
## <a name="examples"></a>Ejemplos  
 Si el código siguiente:  
  
```  
#include <afxwin.h>   // Include header for class library  
#include "resource.h" // Include resource definitions  
#include "myapp.h"    // Include information specific to this app  
...  
```  
  
 se compila con la línea de comandos `CL /YuMYAPP.H PROG.CPP`, el compilador no procesa las tres incluir instrucciones pero código usa precompilado de MYAPP.pch, lo que ahorra el tiempo invertido en el preprocesamiento de los tres de los archivos (y cualquier archivo que puedan incluir).  
  
 Puede usar el  [ /fp (nombre. Archivo de encabezado precompilado)](../../build/reference/fp-name-dot-pch-file.md) opción con la **/Yu** opción para especificar el nombre del archivo .pch si el nombre es distinto del argumento de nombre de archivo para **/Yc** o el nombre base del archivo de origen, como en el Después de:  
  
```  
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP  
```  
  
 Este comando especifica un archivo de encabezado precompilado denominado MYPCH.pch. El compilador utiliza su contenido para restaurar el estado precompilado de todos los archivos de encabezado hasta MyApp.h, incluido. El compilador compila entonces el código que se produce después de la MYAPP.h **incluyen** instrucción.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)