---
title: "Error de las herramientas del vinculador LNK2038 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2038"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2038"
ms.assetid: b8d0fb35-eee6-4f52-b3c4-239cb4f65656
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# Error de las herramientas del vinculador LNK2038
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se detectaron diferencias para '\<nombre\>': el valor '\>valor 1\<' no coincide con el '\<valor 2\>' en \<nombreDeArchivo.obj\>  
  
 El vinculador ha detectado una diferencia de símbolos.  Este error indica que distintas partes de una aplicación, entre las que se incluyen las bibliotecas u otro código objeto al que se vincula la aplicación, utilizan definiciones del símbolo en conflicto.  La directiva pragma [detect\_mismatch](../../preprocessor/detect-mismatch.md) se utiliza para definir estos símbolos y detectar los valores en conflicto.  
  
### Para corregir este error  
  
-   Este error puede aparecer cuando un archivo objeto del proyecto no está actualizado.  Antes de intentar otras soluciones a este error, realice una compilación limpia para garantizar que los archivos objeto están actualizados.  
  
-   Visual Studio define los símbolos siguientes para evitar la vinculación de código incompatible, que puede producir errores en tiempo de ejecución u otro comportamiento inesperado.  
  
     `_MSC_VER`  
     Indica los números de versión principal y secundaria del compilador de Visual C\+\+ que se utiliza para compilar una aplicación o una biblioteca.  El código compilado con una versión del compilador de Visual C\+\+ es incompatible con el código compilado mediante una versión que tiene otros números de versión principal y secundaria.  Para obtener más información, vea `_MSC_VER` en [Macros predefinidas](../../preprocessor/predefined-macros.md).  
  
     Si está vinculando a una biblioteca que no es compatible con la versión del compilador de Visual C\+\+ que usa y no puede adquirir o compilar una versión compatible de la biblioteca, puede utilizar una versión anterior del compilador para compilar el proyecto y cambiar únicamente la propiedad **Conjunto de herramientas de la plataforma** del proyecto.  Para obtener más información, vea [Cómo: Modificar versión de .NET Framework de destino y el conjunto de herramientas de la plataforma](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).  
  
     `_ITERATOR_DEBUG_LEVEL`  
     Indica el nivel de características de seguridad y depuración que se permiten en la biblioteca estándar C\+\+.  Estas características pueden cambiar la representación de ciertos objetos de la biblioteca estándar C\+\+ y, por tanto, hacerlos incompatibles con las que utilizan características de seguridad y depuración diferentes.  Para obtener más información, vea [\_ITERATOR\_DEBUG\_LEVEL](../../standard-library/iterator-debug-level.md).  
  
     `RuntimeLibrary`  
     Indica la versión de biblioteca estándar C\+\+ y de runtime de C utilizada por una aplicación o biblioteca.  El código que usa una versión de la biblioteca estándar C\+\+ o del runtime de C es incompatible con el código que usa una versión diferente.  Para obtener más información, vea [\/MD, \/MT, \/LD \(Utilizar la biblioteca en tiempo de ejecución\)](../../build/reference/md-mt-ld-use-run-time-library.md).  
  
     `_PPLTASKS_WITH_WINRT`  
     Indica que el código que usa la [Biblioteca de patrones de procesamiento paralelo \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) está vinculado a los objetos compilados mediante un valor diferente para la opción del compilador [\/ZW](../../build/reference/zw-windows-runtime-compilation.md). \(**\/ZW** admite C\+\+\/CX\). El código que depende de la biblioteca PPL o la utiliza debe compilarse con la misma configuración de **\/ZW** que se usa en el resto de la aplicación.  
  
     Asegúrese de que los valores de estos símbolos sean coherentes en todos los proyectos de la solución de Visual Studio y también con el código y las bibliotecas a los que se vincula la aplicación.  
  
## Vea también  
 [Errores y advertencias de las herramientas del vinculador](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)