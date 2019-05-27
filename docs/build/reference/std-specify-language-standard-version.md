---
title: /std (Especificar la versión estándar del lenguaje)
ms.date: 05/16/2019
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
ms.openlocfilehash: 0f45727c61d55ff57befc7ff23a3d434e86673bc
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837530"
---
# <a name="std-specify-language-standard-version"></a>/std (Especificar la versión estándar del lenguaje)

Habilite características admitidas del lenguaje C++ desde la versión especificada del estándar del lenguaje C++.

## <a name="syntax"></a>Sintaxis

> /std:\[c++14\|c++17\|c++latest]

## <a name="remarks"></a>Comentarios

La opción **/std** está disponible en Visual Studio 2017 y versiones posteriores. Se usa para controlar características estándar del lenguaje de programación ISO C++ específicas de la versión habilitadas durante la compilación del código. Esta opción permite deshabilitar la compatibilidad con ciertas características nuevas de biblioteca y del lenguaje que pueden interrumpir el código existente que se ajusta a una versión determinada del estándar del lenguaje. De forma predeterminada se especifica **/std:c++14**, que deshabilita características de la biblioteca estándar y del lenguaje de versiones posteriores del estándar del lenguaje C++. Use **/std:c++17** para habilitar características y comportamientos específicos del estándar C++17. Para habilitar de forma explícita el compilador implementado actualmente y las características de la biblioteca estándar propuestas para el siguiente borrador del estándar, use **/std:c++latest**. Todas las características de C++20 requieren **/std:latest**; una vez completada la implementación, se habilitará una nueva opción **/std:c++20**.

La opción **/std:c++14** predeterminada habilita el conjunto de características de C++14 que implementa el compilador MSVC. Esta opción deshabilita la compatibilidad del compilador y la biblioteca estándar con las características que se han cambiado o agregado en las versiones más recientes del estándar del lenguaje, a excepción de algunas características de C++17 ya implementadas en versiones anteriores del compilador MSVC. Para evitar cambios importantes para los usuarios que ya han tomado dependencias de las características disponibles a partir de Visual Studio 2015 Update 2, estas características permanecerán habilitadas cuando se especifica la opción **/std:c++14**:

- [Reglas para auto con listas de inicialización entre llaves](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [typename en parámetros de plantilla de la plantilla](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [Eliminación de trígrafos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [Atributos de espacios de nombres y enumeradores](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [Literales de caracteres de u8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

Para obtener más información sobre qué características de C++14 y C++17 se habilitan al especificar **/std:c++14**, vea las notas de [Conformidad del lenguaje Visual C++](../../overview/visual-cpp-language-conformance.md).

La opción **/std:c++17** habilita el conjunto completo de características de C++17 que implementa el compilador MSVC. Esta opción deshabilita la compatibilidad del compilador y la biblioteca estándar con las características nuevas o que se han modificado en las versiones del borrador de trabajo y las actualizaciones de defectos de C++ Standard posteriores a C++17.

La opción **/std:c++latest** habilita las características de la biblioteca y el lenguaje posteriores a C++17 implementadas actualmente en el compilador y las bibliotecas. Pueden ser características del borrador de trabajo de C++20 y actualizaciones de defectos del estándar C++ que no están incluidas en C++17, así como propuestas experimentales del borrador del estándar. Para obtener una lista de las características admitidos de la biblioteca y el lenguaje, vea [Novedades de Visual C++](../../overview/what-s-new-for-visual-cpp-in-visual-studio.md). La opción **/std:c++latest** no habilita las características protegidas por el modificador **/experimental**, pero es posible que deba habilitarlas.

> [!IMPORTANT]
> Las características del compilador y la biblioteca habilitadas por **/std:c++latest** representan características que pueden aparecer en un futuro estándar C++, así como características aprobadas de C++20. Las características que no se han aprobado están sujetas a cambios importantes o a eliminación sin previo aviso, y se proporcionan como estén. 

La opción **/std** vigente durante una compilación de C++ se puede detectar mediante la macro de preprocesador [\_MSVC\_LANG](../../preprocessor/predefined-macros.md). Para más información, vea [Macros de preprocesador](../../preprocessor/predefined-macros.md).

Las opciones **/std:c++14** y **/std:c++latest** están disponibles a partir de Visual Studio 2015 Update 3. La opción **/std:c++17** está disponible a partir de Visual Studio 2017 versión 15.3. Como se ha mencionado antes, parte del comportamiento estándar de C++17 se habilita mediante la opción **/std:c++14**, pero todas las demás características de C++17 se habilitan mediante **/std:c++17**. Las características de C++20 se habilitan mediante **/std:latest** hasta que se complete la implementación.

> [!NOTE]
> Según el nivel de actualización o la versión del compilador MSVC, es posible que las características de C++17 no se implementen de forma completa o no sean totalmente conformes al especificar las opciones **/std:c++17**. Para obtener información general de la conformidad del lenguaje C++ en Visual C++ por número de versión, vea [Conformidad del lenguaje Visual C++](../../overview/visual-cpp-language-conformance.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione **Propiedades de configuración**, **C/C++**, **Lenguaje**.

1. En **Estándar de lenguaje C++**, elija el estándar del lenguaje que se va a admitir en el control desplegable y, después, seleccione **Aceptar** o **Aplicar** para guardar los cambios.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
