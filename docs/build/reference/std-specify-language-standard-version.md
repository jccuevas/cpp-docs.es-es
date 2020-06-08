---
title: /std (Especificar la versión estándar del lenguaje)
ms.date: 06/04/2020
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: ddb0fc9ad4880ed317a28d7aec5eba1669eabbc5
ms.sourcegitcommit: fe146adb3a02872538637196bb3c45aeeeaaf5c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84507071"
---
# <a name="std-specify-language-standard-version"></a>/std (Especificar la versión estándar del lenguaje)

Habilite características admitidas del lenguaje C++ desde la versión especificada del estándar del lenguaje C++.

## <a name="syntax"></a>Sintaxis

> **`/std:c++14`**\
> **`/std:c++17`**\
> **`/std:c++latest`**]

## <a name="remarks"></a>Comentarios

La **`/std`** opción está disponible en Visual Studio 2017 y versiones posteriores. Se usa para controlar las características estándar de lenguaje de programación ISO C++ específicas de la versión habilitadas durante la compilación del código. Esta opción permite deshabilitar la compatibilidad con ciertas características nuevas de lenguaje y biblioteca: aquellas que pueden interrumpir el código existente que se ajusta a una versión concreta del estándar del lenguaje. De forma predeterminada, **`/std:c++14`** se especifica, lo que deshabilita las características de lenguaje y biblioteca estándar que se encuentran en versiones posteriores del estándar del lenguaje C++. **`/std:c++17`** Se usa para habilitar el comportamiento y las características específicas del estándar de c++ 17. Para habilitar explícitamente el compilador implementado actualmente y las características de la biblioteca estándar propuestas para el siguiente borrador estándar, use **`/std:c++latest`** . Todas las características de C++ 20 requieren **`/std:c++latest`** ; una vez completada la implementación, se **`/std:c++20`** habilitará una nueva opción.

La **`/std:c++14`** opción predeterminada habilita el conjunto de características de c++ 14 implementadas por el compilador MSVC. Esta opción deshabilita la compatibilidad del compilador y la biblioteca estándar con las características que se han cambiado o son nuevas en versiones más recientes del estándar del lenguaje. No deshabilita algunas características de C++ 17 ya implementadas en versiones anteriores del compilador MSVC. Para evitar cambios importantes en los usuarios que ya han tomado dependencias de las características disponibles en o antes de Visual Studio 2015 Update 2, estas características permanecen habilitadas cuando **`/std:c++14`** se especifica la opción:

- [Reglas para auto con listas de inicialización entre llaves](https://wg21.link/n3922)

- [typename en parámetros de plantilla de la plantilla](https://wg21.link/n4051)

- [Eliminación de trígrafos](https://wg21.link/n4086)

- [Atributos de espacios de nombres y enumeradores](https://wg21.link/n4266)

- [Literales de caracteres de u8](https://wg21.link/n4267)

Una lista de las características de C++ 14 y C++ 17 está habilitada cuando se especifica **`/std:c++14`** está disponible. Para obtener más información, vea las notas en la [tabla de conformidad del lenguaje de Microsoft C++](../../overview/visual-cpp-language-conformance.md).

La **`/std:c++17`** opción habilita el conjunto completo de características de c++ 17 implementadas por el compilador MSVC. Esta opción deshabilita la compatibilidad del compilador y la biblioteca estándar con las características nuevas o modificadas después de C++ 17. Esto incluye los cambios posteriores a C + + 17 en las versiones del borrador de trabajo y las actualizaciones de defectos del estándar de C++.

La **`/std:c++latest`** opción habilita las características de la biblioteca y el lenguaje posterior a C + + 17 implementados actualmente en el compilador y las bibliotecas. Estas características pueden incluir cambios del borrador de trabajo de C++ 20, actualizaciones de defectos que no están incluidas en C++ 17 y propuestas experimentales para el estándar de borrador. Para obtener una lista de las características admitidos de la biblioteca y el lenguaje, vea [Novedades de Visual C++](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md). La **`/std:c++latest`** opción no habilita las características protegidas por el **`/experimental`** modificador, pero puede que sea necesario habilitarlas.

> [!IMPORTANT]
> Las características del compilador y la biblioteca habilitadas por **`/std:c++latest`** representan características que pueden aparecer en un futuro estándar de c++, así como en las características de c++ 20 que están aprobadas. Las características que no se han aprobado están sujetas a cambios importantes o a eliminación sin previo aviso, y se proporcionan como estén.

La **`/std`** opción en vigor durante una compilación de C++ se puede detectar mediante el uso de la macro de preprocesador [ \_ MSVC \_ lang](../../preprocessor/predefined-macros.md) . Para más información, vea [Macros de preprocesador](../../preprocessor/predefined-macros.md).

Las **`/std:c++14`** **`/std:c++latest`** Opciones y están disponibles a partir de Visual Studio 2015 Update 3. La **`/std:c++17`** opción está disponible a partir de la versión 15,3 de Visual Studio 2017. Como se indicó anteriormente, el comportamiento estándar de C++ 17 se habilita mediante la **`/std:c++14`** opción, pero todas las demás características de c++ 17 están habilitadas por **`/std:c++17`** . Las características de c++ 20 las habilita **`/std:c++latest`** hasta que se completa la implementación.

> [!NOTE]
> Dependiendo de la versión del compilador de MSVC o del nivel de actualización, es posible que las características de C++ 17 no estén totalmente implementadas o se ajusten totalmente al especificar las **`/std:c++17`** Opciones. Para obtener información general sobre la conformidad del lenguaje C++ en Visual C++ por versión de lanzamiento, vea [tabla de conformidad del lenguaje Microsoft C++](../../overview/visual-cpp-language-conformance.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione **Propiedades de configuración**, **C/C++**, **Lenguaje**.

1. En **Estándar de lenguaje C++**, elija el estándar del lenguaje que se va a admitir en el control desplegable y, después, seleccione **Aceptar** o **Aplicar** para guardar los cambios.

## <a name="see-also"></a>Consulte también:

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
