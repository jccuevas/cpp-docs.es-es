---
title: Error de las herramientas del vinculador LNK2038
ms.date: 12/15/2017
f1_keywords:
- LNK2038
helpviewer_keywords:
- LNK2038
ms.openlocfilehash: a22b31f1ac3226271ed7ff03b5be7dad7fff6b93
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594316"
---
# <a name="linker-tools-error-lnk2038"></a>Error de las herramientas del vinculador LNK2038

> Detectado error de coincidencia para '*nombre*': valor '*value_1*'no coincide con valor'*value_2*' en *nombreDeArchivo.obj*

El vinculador ha detectado una diferencia de símbolos. Este error indica que las distintas partes de una aplicación, incluidas las bibliotecas u otro objeto de código que los vínculos de la aplicación, use definiciones en conflicto del símbolo. El [detect_mismatch](../../preprocessor/detect-mismatch.md) pragma se usa para definir estos símbolos y detectar los valores en conflicto.

## <a name="possible-causes-and-solutions"></a>Las posibles causas y soluciones

Este error puede aparecer cuando un archivo objeto del proyecto no está actualizado. Antes de intentar otras soluciones a este error, realice una compilación limpia para garantizar que los archivos objeto están actualizados.

Visual Studio define los símbolos siguientes para evitar la vinculación de código incompatible, que puede producir errores en tiempo de ejecución u otro comportamiento inesperado.

- `_MSC_VER` Indica los números de versión principal y secundaria del compilador de Visual C++ que se usa para crear una aplicación o biblioteca. El código compilado con una versión del compilador de Visual C++ es incompatible con el código compilado mediante una versión que tiene otros números de versión principal y secundaria. Para obtener más información, consulte `_MSC_VER` en [Predefined Macros](../../preprocessor/predefined-macros.md).

   Si va a vincular a una biblioteca que no es compatible con la versión del compilador de Visual C++ que está usando y no se puede adquirir o compilar una versión compatible de la biblioteca, puede usar una versión anterior del compilador para compilar el proyecto: cambiar el <C1/>conjunto de herramientas de plataforma** propiedad del proyecto para el conjunto de herramientas anterior. Para obtener más información, consulte [Cómo: modificar plataforma de destino y el conjunto de herramientas de plataforma](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- `_ITERATOR_DEBUG_LEVEL` Indica el nivel de seguridad y las características que están habilitadas en la biblioteca estándar de C++ de depuración. Estas características pueden cambiar la representación de ciertos objetos de la biblioteca estándar C++ y, por tanto, hacerlos incompatibles con las que utilizan características de seguridad y depuración diferentes. Para obtener más información, vea [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md).

- `RuntimeLibrary` Indica la versión de la biblioteca estándar de C++ y C en tiempo de ejecución que utiliza una aplicación o biblioteca. El código que usa una versión de la biblioteca estándar C++ o del runtime de C es incompatible con el código que usa una versión diferente. Para obtener más información, consulte [/MD, / MT, /LD (Utilizar la biblioteca en tiempo de ejecución)](../../build/reference/md-mt-ld-use-run-time-library.md).

- `_PPLTASKS_WITH_WINRT` Indica que el código que usa el [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) está vinculado a los objetos compilados mediante el uso de un valor diferente para el [/ZW](../../build/reference/zw-windows-runtime-compilation.md) opción del compilador. (**/ZW** admite C++ / c++ / CX.) Código que depende de la biblioteca PPL o la utiliza debe compilarse con la misma **/ZW** configuración que se usa en el resto de la aplicación.

Asegúrese de que los valores de estos símbolos sean coherentes en todos los proyectos de la solución de Visual Studio y también con el código y las bibliotecas a los que se vincula la aplicación.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemas de la biblioteca de terceros y de Vcpkg

Si ve este error cuando intenta configurar una biblioteca de terceros como parte de la compilación, considere el uso de [Vcpkg](../../vcpkg.md), el Administrador de paquetes de Visual C++, para instalar y compile la biblioteca. Vcpkg admite un enorme y creciente [lista de bibliotecas de terceros](https://github.com/Microsoft/vcpkg/tree/master/ports)y establece todas las propiedades de configuración y las dependencias necesarias para compilaciones correctas como parte del proyecto. Para obtener más información, consulte relacionado [Blog de Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) registrar.

## <a name="see-also"></a>Vea también

[Errores y advertencias de las herramientas del vinculador](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)