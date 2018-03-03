---
title: Error de las LNK2038 las herramientas del vinculador | Documentos de Microsoft
ms.custom: 
ms.date: 12/15/2017
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2038
dev_langs:
- C++
helpviewer_keywords:
- LNK2038
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 13f65f403cac43551b787abab15713fb9ffab618
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2038"></a>Error de las herramientas del vinculador LNK2038

> Error de coincidencia detectada para '*nombre*': valor '*value_1*'no coincide con valor'*value_2*' en *nombreDeArchivo.obj*

El vinculador ha detectado una diferencia de símbolos. Este error indica que distintas partes de una aplicación, incluidas las bibliotecas u otro objeto de código que los vínculos de la aplicación, utilizan definiciones en conflicto del símbolo. El [detect_mismatch](../../preprocessor/detect-mismatch.md) pragma se utiliza para definir estos símbolos y detectar los valores en conflicto.

## <a name="possible-causes-and-solutions"></a>Posibles causas y soluciones

Este error puede aparecer cuando un archivo objeto del proyecto no está actualizado. Antes de intentar otras soluciones a este error, realice una compilación limpia para garantizar que los archivos objeto están actualizados.

Visual Studio define los símbolos siguientes para evitar la vinculación de código incompatible, que puede producir errores en tiempo de ejecución u otro comportamiento inesperado.

- `_MSC_VER`  
   Indica los números de versión principal y secundaria del compilador de Visual C++ que se utiliza para compilar una aplicación o una biblioteca. El código compilado con una versión del compilador de Visual C++ es incompatible con el código compilado mediante una versión que tiene otros números de versión principal y secundaria. Para obtener más información, consulte `_MSC_VER` en [Macros predefinidas](../../preprocessor/predefined-macros.md).

   Si va a vincular a una biblioteca que no es compatible con la versión del compilador de Visual C++ que está usando y no se puede adquirir o compilar una versión compatible de la biblioteca, puede usar una versión anterior del compilador para compilar el proyecto: cambiar el <C1/>conjunto de herramientas de plataforma** propiedad del proyecto para el conjunto de herramientas anterior. Para obtener más información, consulte [Cómo: modificar plataforma de destino y el conjunto de herramientas de plataforma](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- `_ITERATOR_DEBUG_LEVEL`  
   Indica el nivel de características de seguridad y depuración que se permiten en la biblioteca estándar C++. Estas características pueden cambiar la representación de ciertos objetos de la biblioteca estándar C++ y, por tanto, hacerlos incompatibles con las que utilizan características de seguridad y depuración diferentes. Para obtener más información, vea [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md).

- `RuntimeLibrary`  
   Indica la versión de biblioteca estándar C++ y de runtime de C utilizada por una aplicación o biblioteca. El código que usa una versión de la biblioteca estándar C++ o del runtime de C es incompatible con el código que usa una versión diferente. Para obtener más información, consulte [/MD, / MT, /LD (Utilizar la biblioteca en tiempo de ejecución)](../../build/reference/md-mt-ld-use-run-time-library.md).

- `_PPLTASKS_WITH_WINRT`  
   Indica que el código que usa el [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) está vinculado a los objetos compilados mediante un valor diferente para la [/ZW](../../build/reference/zw-windows-runtime-compilation.md) opción del compilador. (**/ZW** admite C++ / CX.) Código que depende de la biblioteca PPL o la utiliza debe compilarse con la misma **/ZW** configuración que se utiliza en el resto de la aplicación.

Asegúrese de que los valores de estos símbolos sean coherentes en todos los proyectos de la solución de Visual Studio y también con el código y las bibliotecas a los que se vincula la aplicación.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemas de bibliotecas de terceros y Vcpkg

Si ve este error al tratar de configurar una biblioteca de terceros como parte de la compilación, considere la posibilidad de usar [Vcpkg](../../vcpkg.md), el Administrador de paquetes de Visual C++, para instalar y compile la biblioteca. Vcpkg admite un elevado y creciente [lista de bibliotecas de terceros](https://github.com/Microsoft/vcpkg/tree/master/ports)y establece todas las propiedades de configuración y las dependencias necesarias para las compilaciones correcta como parte de su proyecto. Para obtener más información, vea relacionado [Blog de Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) post.

## <a name="see-also"></a>Vea también

[Errores y advertencias de las herramientas del vinculador](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)