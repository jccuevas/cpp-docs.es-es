---
title: -std (especificar la versión estándar del lenguaje) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/16/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- /std
- -std
- VC.Project.VCCLCompilerTool.CppLanguageStandard
dev_langs:
- C++
ms.assetid: 0acb74ba-1aa8-4c05-b96c-682988dc19bd
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb248f4c7ce1d9520bc328ed59b75ff081659996
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="std-specify-language-standard-version"></a>/STD (especificar la versión estándar del lenguaje)

Habilitar admite características del lenguaje C++ de la versión especificada del lenguaje C++ estándar.

## <a name="syntax"></a>Sintaxis

> /std: [c ++ 14 | c ++ 17 | c/c ++ versión más reciente]

## <a name="remarks"></a>Comentarios

El **/std** opción se utiliza para controlar el específico de la versión ISO C++ habilitados durante la compilación del código de características estándar del lenguaje de programación. Esta opción permite deshabilitar la compatibilidad con ciertos nuevas características de lenguaje y la biblioteca que se puede interrumpir el código existente que se ajuste a una versión determinada del lenguaje estándar. De forma predeterminada, **/std:c ++ 14** se especifica, lo que deshabilita el idioma y las características de la biblioteca estándar se encuentran en las versiones posteriores del lenguaje C++ estándares. Use **/std:c ++ 17** para habilitar características C ++ 17 estándar específicos y el comportamiento. Para habilitar explícitamente la más reciente compatible compilador y características de la biblioteca estándar, use **/std:c ++ más reciente**.

El valor predeterminado **/std:c ++ 14** opción habilita el conjunto de características C ++ 14 implementada por el compilador de Visual C++. Esta opción deshabilita el compilador y el soporte técnico de la biblioteca estándar para las características que se cambian o nuevas en las versiones más recientes del lenguaje estándar, con la excepción de algunas características C ++ 17 ya implementados en las versiones anteriores del compilador de Visual C++. Para evitar la interrupción de cambios para los usuarios que ya se han tenido dependencias de las características disponibles a partir de Visual Studio 2015 Update 2, estas características permanecen habilitados cuando la **/std:c ++ 14** se especifica la opción:

- [Reglas para auto con listas de inicialización entre llaves](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)

- [TypeName en parámetros de plantilla](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)

- [Eliminación de trígrafos](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)

- [Atributos de espacios de nombres y enumeradores](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)

- [literales de caracteres de U8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)

Para obtener más información sobre qué características C ++ 14 y C ++ 17 se habilitan cuando **/std:c ++ 14** está especificado, vea las notas de [conformidad de lenguaje de Visual C++](../../visual-cpp-language-conformance.md).
  
El **/std:c ++ 17** opción permite que el conjunto completo de C ++ 17 características implementadas por el compilador de Visual C++. Esta opción deshabilita el compilador y el soporte técnico de la biblioteca estándar para las características que se cambian o nuevas en las versiones de las actualizaciones de borrador de trabajo y defectos del estándar de C++ después de C ++ 17.  
  
El **/std:c ++ más reciente** opción habilita el conjunto de características de lenguaje y la biblioteca de C++ implementada Visual C++ para realizar un seguimiento más C ++ 20 borrador de trabajo y defectos actualizaciones recientes del estándar de C++ que no están incluidas en C ++ 17. Utilice este modificador para obtener la entrada de blog-características de lenguaje C ++ 17 admitidas por el compilador y la biblioteca estándar. Para obtener una lista de idiomas admitidos y características de la biblioteca, consulte [What's New para Visual C++](../../what-s-new-for-visual-cpp-in-visual-studio.md). El **/std:c ++ más reciente** opción no habilita las características protegidas por la **/ experimental** cambiar.  
  
El **/std** opción en vigor durante una compilación de C++ se pueden detectar mediante el uso de la [ \_MSVC\_LANG](../../preprocessor/predefined-macros.md) macro de preprocesador. Para obtener más información, consulte [Macros de preprocesador](../../preprocessor/predefined-macros.md).

El **/std:c ++ 14** y **/std:c ++ más reciente** opciones están disponibles a partir de Visual C++ 2015 Update 3. El **/std:c ++ 17** opción está disponible a partir de Visual C++ 2017 versión 15.3. Como se mencionó anteriormente, algunos estándar C ++ 17 se habilita el comportamiento por el **/std:c ++ 14** opción, pero todas las demás características C ++ 17 están habilitadas de forma **/std:c ++ 17**.
  
> [!NOTE]
> Según el nivel de versión o una actualización de compilador de Visual C++, ciertas características C ++ 14 y C ++ 17 pueden no ser totalmente implementados o totalmente conforme al especificar el **/std:c ++ 14** o **/std:c ++ 17** opciones. Por ejemplo, el compilador de Visual C++ de 2017 RTM no admite totalmente C ++ 14-conforme `constexpr`, expresión SFINAE o búsqueda de nombre de la fase 2. Para obtener información general de la conformidad de lenguaje C++ en Visual C++ por número de versión, consulte [conformidad de lenguaje de Visual C++](../../visual-cpp-language-conformance.md). 
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione **propiedades de configuración**, **C/C++**, **lenguaje**.  
  
3.  En **lenguaje estándar de C++**, elija el estándar del lenguaje admite desde el control de lista desplegable y, después, elija **Aceptar** o **aplicar** para guardar los cambios.  
  
## <a name="see-also"></a>Vea también  
  
[Opciones del compilador](../../build/reference/compiler-options.md)   
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
