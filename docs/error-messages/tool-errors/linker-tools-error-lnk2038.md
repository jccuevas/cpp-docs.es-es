---
title: Error de las herramientas del vinculador LNK2038
ms.date: 12/15/2017
f1_keywords:
- LNK2038
helpviewer_keywords:
- LNK2038
ms.openlocfilehash: 45078d8e1bdbeb23dd311d915ba2cf47e42b2663
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194517"
---
# <a name="linker-tools-error-lnk2038"></a>Error de las herramientas del vinculador LNK2038

> se detectó una falta de coincidencia para '*Name*': el valor '*value_1*' no coincide con el valor '*value_2*' en *filename. obj*

El vinculador ha detectado una diferencia de símbolos. Este error indica que diferentes partes de una aplicación, incluidas las bibliotecas u otro código objeto al que se vincula la aplicación, usan definiciones en conflicto del símbolo. La pragma [detectar no coincidentes](../../preprocessor/detect-mismatch.md) se usa para definir dichos símbolos y detectar los valores en conflicto.

## <a name="possible-causes-and-solutions"></a>Posibles causas y soluciones

Este error puede aparecer cuando un archivo objeto del proyecto no está actualizado. Antes de intentar otras soluciones a este error, realice una compilación limpia para garantizar que los archivos objeto están actualizados.

Visual Studio define los símbolos siguientes para evitar la vinculación de código incompatible, que puede producir errores en tiempo de ejecución u otro comportamiento inesperado.

- `_MSC_VER` indica los números de versión principal y secundaria del compilador de Microsoft C++ (MSVC) que se usa para compilar una aplicación o biblioteca. El código compilado mediante una versión de MSVC es incompatible con el código compilado mediante una versión que tiene números de versión principal y secundaria diferentes. Para obtener más información, vea `_MSC_VER` en [macros predefinidas](../../preprocessor/predefined-macros.md).

   Si va a vincular a una biblioteca que no es compatible con la versión de MSVC que está usando y no puede adquirir o compilar una versión compatible de la biblioteca, puede utilizar una versión anterior del compilador para compilar el proyecto: cambie la propiedad **conjunto de herramientas** de la plataforma del proyecto al conjunto de herramientas anterior. Para obtener más información, vea [Cómo: modificar la plataforma de destino y el conjunto de herramientas de la plataforma](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- `_ITERATOR_DEBUG_LEVEL` indica el nivel de características de seguridad y depuración que están habilitadas en la C++ biblioteca estándar. Estas características pueden cambiar la representación de ciertos objetos de la biblioteca estándar C++ y, por tanto, hacerlos incompatibles con las que utilizan características de seguridad y depuración diferentes. Para obtener más información, vea [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md).

- `RuntimeLibrary` indica la versión de la C++ biblioteca estándar y el tiempo de ejecución de C que usa una aplicación o biblioteca. El código que usa una versión de la biblioteca estándar C++ o del runtime de C es incompatible con el código que usa una versión diferente. Para obtener más información, consulte [/MD, / MT, /LD (Utilizar la biblioteca en tiempo de ejecución)](../../build/reference/md-mt-ld-use-run-time-library.md).

- `_PPLTASKS_WITH_WINRT` indica que el código que usa la [biblioteca de patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) está vinculado a los objetos compilados con una configuración diferente para la opción del compilador [/ZW](../../build/reference/zw-windows-runtime-compilation.md) . ( **/ZW** admite C++/CX.) El código que usa o depende de la biblioteca PPL se debe compilar con la misma configuración de **/ZW** que se usa en el resto de la aplicación.

Asegúrese de que los valores de estos símbolos sean coherentes en todos los proyectos de la solución de Visual Studio y también con el código y las bibliotecas a los que se vincula la aplicación.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemas de la biblioteca de terceros y Vcpkg

Si ve este error al intentar configurar una biblioteca de terceros como parte de la compilación, considere la posibilidad de usar [Vcpkg](../../vcpkg.md), el administrador de paquetes C++ visuales, para instalar y compilar la biblioteca. Vcpkg admite una lista grande y creciente [de bibliotecas de terceros](https://github.com/Microsoft/vcpkg/tree/master/ports), y establece todas las propiedades de configuración y las dependencias necesarias para compilaciones correctas como parte del proyecto. Para obtener más información, consulte la entrada de [blog visual C++ ](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) relacionada.

## <a name="see-also"></a>Consulte también

[Errores y advertencias de las herramientas del vinculador](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
