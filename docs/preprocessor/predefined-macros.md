---
title: Macros predefinidas | Documentos de Microsoft
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _ATL_VER
- __ATOM__
- __AVX__
- __AVX2__
- _CHAR_UNSIGNED
- __CLR_VER
- _CONTROL_FLOW_GUARD
- __COUNTER__
- __cplusplus
- __cplusplus_cli
- __cplusplus_winrt
- _CPPRTTI
- _CPPUNWIND
- __DATE__
- _DEBUG
- _DLL
- __FILE__
- __FUNCDNAME__
- __FUNCSIG__
- __FUNCTION__
- _INTEGRAL_MAX_BITS
- _ISO_VOLATILE
- _KERNEL_MODE
- __LINE__
- _M_AMD64
- _M_ARM
- _M_ARM_ARMV7VE
- _M_ARM_FP
- _M_ARM64
- _M_CEE
- _M_CEE_PURE
- _M_CEE_SAFE
- _M_FP_EXCEPT
- _M_FP_FAST
- _M_FP_PRECISE
- _M_FP_STRICT
- _M_IX86
- _M_IX86_FP
- _M_X64
- _MANAGED
- _MFC_VER
- _MSC_BUILD
- _MSC_EXTENSIONS
- _MSC_FULL_VER
- _MSC_VER
- _MSVC_LANG
- __MSVC_RUNTIME_CHECKS
- _MT
- _NATIVE_WCHAR_T_DEFINED
- _NO_SIZED_DEALLOCATION
- _OPENMP
- _PREFAST_
- _RESUMABLE_FUNCTIONS_SUPPORTED
- _RTC_CONVERSION_CHECKS_ENABLED
- __STDC__
- __STDC_HOSTED__
- __STDCPP_THREADS__
- __TIME__
- __TIMESTAMP__
- __VA_ARGS__
- _VC_NODEFAULTLIB
- _WCHAR_T_DEFINED
- _WIN32
- _WIN64
- _WINRT_DLL
- __func__
dev_langs: C++
helpviewer_keywords:
- timestamps, preprocessor macro
- cl.exe compiler, version number
- version numbers, C/C++ compiler (cl.exe)
- macros, predefined C++
- preprocessor, macros
- predefined macros
- _ATL_VER macro
- __ATOM__ macro
- __AVX__ macro
- __AVX2__ macro
- _CHAR_UNSIGNED macro
- __CLR_VER macro
- _CONTROL_FLOW_GUARD macro
- __COUNTER__ macro
- __cplusplus macro
- __cplusplus_cli macro
- __cplusplus_winrt macro
- _CPPRTTI macro
- _CPPUNWIND macro
- __DATE__ macro
- _DEBUG macro
- _DLL macro
- __FILE__ macro
- __FUNCDNAME__ macro
- __FUNCSIG__ macro
- __FUNCTION__ macro
- _INTEGRAL_MAX_BITS macro
- _ISO_VOLATILE macro
- _KERNEL_MODE macro
- __LINE__ macro
- _M_AMD64 macro
- _M_ARM macro
- _M_ARM_ARMV7VE macro
- _M_ARM_FP macro
- _M_ARM64 macro
- _M_CEE macro
- _M_CEE_PURE macro
- _M_CEE_SAFE macro
- _M_FP_EXCEPT macro
- _M_FP_FAST macro
- _M_FP_PRECISE macro
- _M_FP_STRICT macro
- _M_IX86 macro
- _M_IX86_FP macro
- _M_X64 macro
- _MANAGED macro
- _MFC_VER macro
- _MSC_BUILD macro
- _MSC_EXTENSIONS macro
- _MSC_FULL_VER macro
- _MSC_VER macro
- _MSVC_LANG macro
- __MSVC_RUNTIME_CHECKS macro
- _MT macro
- _NATIVE_WCHAR_T_DEFINED macro
- _NO_SIZED_DEALLOCATION macro
- _OPENMP macro
- _PREFAST_ macro
- _RESUMABLE_FUNCTIONS_SUPPORTED macro
- _RTC_CONVERSION_CHECKS_ENABLED macro
- __STDC__ macro
- __STDC_HOSTED__ macro
- __STDCPP_THREADS__ macro
- __TIME__ macro
- __TIMESTAMP__ macro
- __VA_ARGS__ macro
- _VC_NODEFAULTLIB macro
- _WCHAR_T_DEFINED macro
- _WIN32 macro
- _WIN64 macro
- _WINRT_DLL macro
- __func__ identifier
ms.assetid: 1cc5f70a-a225-469c-aed0-fe766238e23f
caps.latest.revision: "75"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86905a879abe9b81302a8f196e200c1d0c227bb7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="predefined-macros"></a>Macros predefinidas

El compilador de Visual C++ predefine ciertas macros de preprocesador, según el lenguaje (C o C++), el destino de compilación y las opciones del compilador elegido.

Visual C++ admite las macros de preprocesador predefinidas necesarias especificadas por el estándar ANSI/ISO C99 y C ++ 14 estándar ISO. La implementación también admite varias macros de preprocesador específicos de Microsoft más. Algunas macros se definen únicamente para entornos de compilación concreta o las opciones del compilador. A menos que se indique lo contrario, las macros se definen a lo largo de una unidad de traducción como si se especificaron como **/D** argumentos de la opción de compilador. Cuando se define, se expanden las macros en los valores especificados por el preprocesador antes de la compilación. Las macros predefinidas no toman ningún argumento y no se puede volver a definir.

## <a name="standard-predefined-identifier"></a>Identificador predefinido estándar

El compilador admite este identificador predefinido especificado por ISO C99 e ISO C ++ 11.

- **&#95; &#95; func &#95; &#95;**  El nombre completo y sin adornar de la función de inclusión como una función local `static const` matriz de `char`.

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>Macros predefinidas estándares

El compilador admite estas macros predefinidas especificadas por ISO C99 y ISO C ++ 17 estándares.

- **&#95; &#95; cplusplus** definido como un valor literal entero cuando la unidad de traducción se compila como C++. En caso contrario, es indefinido.

- **&#95; &#95; fecha &#95; &#95;**  La fecha de compilación del archivo de origen actual. La fecha es una cadena de longitud constante literal del formulario *Mmm dd aaaa*. El nombre del mes *Mmm* es el mismo que el nombre del mes abreviado en fechas generadas por la biblioteca en tiempo de ejecución de C [asctime](../c-runtime-library/reference/asctime-wasctime.md) (función). El primer carácter de fecha *dd* es un espacio si el valor es menor que 10. Siempre se define esta macro.

- **&#95; &#95; ARCHIVO de &#95; &#95;**  El nombre del archivo de origen actual. **&#95; &#95; ARCHIVO de &#95; &#95;**  se expande a un literal de cadena de caracteres. Para asegurarse de que se muestra la ruta de acceso completa al archivo, use [/FC (Full ruta de acceso del archivo de código fuente en diagnósticos)](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md). Siempre se define esta macro.

- **&#95; &#95; LÍNEA &#95; &#95;**  Definido como el número de línea de entero en el archivo de origen actual. El valor de la **&#95; &#95; LÍNEA &#95; &#95;**  macro puede cambiarse mediante una `#line` directiva. Siempre se define esta macro.

- **&#95; &#95; STDC &#95; &#95;**  Definido como 1 solamente cuando se compila como C y si la [/Za](../build/reference/za-ze-disable-language-extensions.md) se especifica la opción del compilador. En caso contrario, es indefinido.

- **&#95; &#95; STDC &#95; HOSPEDA &#95; &#95;**  Definido como 1 si la implementación es un *hospedado implementación*, que es compatible con la biblioteca estándar requiere completa. En caso contrario, se define como 0.

- **&#95; &#95; STDCPP &#95; SUBPROCESOS &#95; &#95;**  Definido como 1 si y solo si un programa puede tener más de un subproceso de ejecución y compilado como C++. En caso contrario, es indefinido.

- **&#95; &#95; TIEMPO &#95; &#95;**  El momento de la traducción de la unidad de traducción preprocesado. El tiempo es una cadena de caracteres literales del formulario *hh*, igual que la hora devuelta por la biblioteca en tiempo de ejecución de C [asctime](../c-runtime-library/reference/asctime-wasctime.md) (función). Siempre se define esta macro.

## <a name="microsoft-specific-predefined-macros"></a>Macros predefinidas específicas de Microsoft

Microsoft Visual C++ admite estas macros predefinidas adicionales.

- **&#95; &#95; ATOM &#95; &#95;**  Definido como 1 cuando la [/favor:ATOM](../build/reference/favor-optimize-for-architecture-specifics.md) se establece la opción del compilador y el destino de compilador es x86 o x x64. En caso contrario, es indefinido.

- **&#95; &#95; AVX &#95; &#95;**  Definido como 1 cuando la [/arch: AVX](../build/reference/arch-x86.md) o [/arch:AVX2](../build/reference/arch-x86.md) se establecen opciones del compilador y el destino de compilador es x86 o x x64. En caso contrario, es indefinido.

- **&#95; &#95; AVX2 &#95; &#95;**  Definido como 1 cuando la [/arch:AVX2](../build/reference/arch-x86.md) se establece la opción del compilador y el destino de compilador es x86 o x x64. En caso contrario, es indefinido.

- **&#95; CHAR &#95; Sin signo** definido como 1 si el valor predeterminado `char` tipo es sin signo. Esto se establece cuando el [/j (carácter predeterminado es de tipo sin signo)](../build/reference/j-default-char-type-is-unsigned.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; &#95; CLR &#95; VER** definido como un literal de entero que representa la versión de common language runtime utilizado cuando se compila la aplicación. El valor está codificado en el formulario `Mmmbbbbb`, donde `M` es la versión principal del runtime, `mm` es la versión secundaria del runtime, y `bbbbb` es el número de compilación. **&#95; &#95; CLR &#95; VER** se define si la [/CLR](../build/reference/clr-common-language-runtime-compilation.md) se establece la opción del compilador. En caso contrario, es indefinido.

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- **&#95; CONTROL &#95; FLUJO &#95; PROTECCIÓN** definido como 1 cuando la [/Guard: CF (habilitar Control de flujo de protección)](../build/reference/guard-enable-control-flow-guard.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; &#95; CONTADOR &#95; &#95;**  Se expande a un literal entero que comienza en 0 y se incrementa en 1 cada vez que se utiliza en un archivo de código fuente o incluir los encabezados del archivo de origen. **&#95; &#95; CONTADOR &#95; &#95;**  recuerda a su estado cuando se utilizan encabezados precompilados. Siempre se define esta macro.

  Este ejemplo se utiliza `__COUNTER__` para asignar identificadores únicos a tres objetos diferentes del mismo tipo. El `exampleClass` constructor toma un entero como un parámetro. En `main`, la aplicación declara tres objetos de tipo `exampleClass`con `__COUNTER__` como el parámetro de identificador único:

    ```cpp
    // macro__COUNTER__.cpp
    // Demonstration of __COUNTER__, assigns unique identifiers to
    // different objects of the same type.
    // Compile by using: cl /EHsc /W4 macro__COUNTER__.cpp
    #include <stdio.h>

    class exampleClass {
        int m_nID;
    public:
        // initialize object with a read-only unique ID
        exampleClass(int nID) : m_nID(nID) {}
        int GetID(void) { return m_nID; }
    };

    int main()
    {
        // __COUNTER__ is initially defined as 0
        exampleClass e1(__COUNTER__);

        // On the second reference, __COUNTER__ is now defined as 1
        exampleClass e2(__COUNTER__);

        // __COUNTER__ is now defined as 2
        exampleClass e3(__COUNTER__);

        printf("e1 ID: %i\n", e1.GetID());
        printf("e2 ID: %i\n", e2.GetID());
        printf("e3 ID: %i\n", e3.GetID());

        // Output
        // ------------------------------
        // e1 ID: 0
        // e2 ID: 1
        // e3 ID: 2

        return 0;
    }
    ```

- **&#95; &#95; cplusplus &#95; cli** definido como el valor literal entero 200406 cuando se compila como C++ y un [/CLR](../build/reference/clr-common-language-runtime-compilation.md) se establece la opción del compilador. En caso contrario, es indefinido. Cuando se define, **&#95; &#95; cplusplus &#95; cli** está activo en la unidad de traducción.

    ```cpp
    // cplusplus_cli.cpp
    // compile by using /clr
    #include "stdio.h"
    int main() {
       #ifdef __cplusplus_cli
          printf("%d\n", __cplusplus_cli);
       #else
          printf("not defined\n");
       #endif
    }
    ```

- **&#95; &#95; cplusplus &#95; winrt** definido como el valor literal entero 201009 cuando se compila como C++ y la [/ZW (compilación de Windows en tiempo de ejecución)](../build/reference/zw-windows-runtime-compilation.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; CPPRTTI** definido como 1 si la [/GR (habilitar información de tipo en tiempo de ejecución)](../build/reference/gr-enable-run-time-type-information.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; CPPUNWIND** definido como 1 si uno o varios de los [/GX (habilitar el control de excepciones)](../build/reference/gx-enable-exception-handling.md), [/clr (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), o [/EH (modelo de control de excepciones) ](../build/reference/eh-exception-handling-model.md) se establecen opciones del compilador. En caso contrario, es indefinido.

- **&#95; depuración** definido como 1 cuando la [/LDd](../build/reference/md-mt-ld-use-run-time-library.md), [MDd](../build/reference/md-mt-ld-use-run-time-library.md), o [/MTd](../build/reference/md-mt-ld-use-run-time-library.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; DLL** definido como 1 cuando la [/MD](../build/reference/md-mt-ld-use-run-time-library.md) o [MDd](../build/reference/md-mt-ld-use-run-time-library.md) se establece la opción del compilador (DLL multiproceso). En caso contrario, es indefinido.

- **&#95; &#95; FUNCDNAME &#95; &#95;**  Definido como un literal de cadena que contiene el [nombre representativo](../build/reference/decorated-names.md) de la función de inclusión. La macro se define solo dentro de una función. El **&#95; &#95; FUNCDNAME &#95; &#95;**  macro no se expande si usa el [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) o [/P](../build/reference/p-preprocess-to-a-file.md) opción del compilador.

   Este ejemplo se utiliza la `__FUNCDNAME__`, `__FUNCSIG__`, y `__FUNCTION__` macros para mostrar información de la función.

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- **&#95; &#95; FUNCSIG &#95; &#95;**  Definido como un literal de cadena que contiene la firma de la función de inclusión. La macro se define solo dentro de una función. El **&#95; &#95; FUNCSIG &#95; &#95;**  macro no se expande si usa el [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) o [/P](../build/reference/p-preprocess-to-a-file.md) opción del compilador. Cuando se compila para un destino de 64 bits, la convención de llamada es `__cdecl` de forma predeterminada. Para obtener un ejemplo de uso, consulte el `__FUNCDNAME__` macro.

- **&#95; &#95; FUNCIÓN &#95; &#95;**  Definido como un literal de cadena que contiene el nombre no representativo de la función de inclusión. La macro se define solo dentro de una función. El **&#95; &#95; FUNCIÓN &#95; &#95;**  macro no se expande si usa el [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) o [/P](../build/reference/p-preprocess-to-a-file.md) opción del compilador. Para obtener un ejemplo de uso, consulte el `__FUNCDNAME__` macro.

- **&#95; entero &#95; MAX &#95; BITS** definidos como el valor literal entero 64, el tamaño máximo (en bits) para un tipo entero no vector. Siempre se define esta macro.

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- **&#95; &#95; INTELLISENSE &#95; &#95;**  Define como pasar 1 durante un compilador de IntelliSense en el IDE de Visual Studio. En caso contrario, es indefinido. Puede utilizar esta macro para proteger el código el compilador de IntelliSense no comprender o utilizarlo para alternar entre la compilación y el compilador de IntelliSense. Para obtener más información, consulte [sugerencias de solución de problemas para IntelliSense lentitud](https://blogs.msdn.microsoft.com/vcblog/2011/03/29/troubleshooting-tips-for-intellisense-slowness/).

- **&#95; ISO &#95; VOLATILE** definido como 1 si la [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; KERNEL &#95; MODO** definido como 1 si la [/kernel (crear binario en modo Kernel)](../build/reference/kernel-create-kernel-mode-binary.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; M &#95; AMD64** define como el literal entero valor 100 para las compilaciones que procesadores de destino x64. En caso contrario, es indefinido.

- **&#95; M &#95; ARM** definido como el valor literal entero 7 para las compilaciones que tienen como destino procesadores ARM. En caso contrario, es indefinido.

- **&#95; M &#95; ARM &#95; ARMV7VE** definido como 1 cuando la [armv7ve](../build/reference/arch-arm.md) se establece la opción del compilador para las compilaciones que tienen como destino procesadores ARM. En caso contrario, es indefinido.

- **&#95; M &#95; ARM &#95; FP** definido como un valor literal entero que indica que [/arch](../build/reference/arch-arm.md) se estableció la opción del compilador, si el destino de compilación es un procesador ARM. En caso contrario, es indefinido.

  - En el intervalo 30-39 si no hay ningún **/arch** se especificó la opción de ARM, que indica la arquitectura predeterminada de ARM se estableció (`VFPv3`).

  - En el intervalo 40-49 si **vfpv4** se estableció.

  - Vea [/arch (ARM)](../build/reference/arch-arm.md) para obtener más información.

- **&#95; M &#95; ARM64** definido como 1 para las compilaciones que tienen como destino procesadores ARM de 64 bits. En caso contrario, es indefinido.

- **&#95; M &#95; CEE** definida como 001 si cualquiera [/clr (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; M &#95; CEE &#95; PURO** en desuso a partir de Visual Studio 2015. Definida como 001 si la [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; M &#95; CEE &#95; SEGURO** en desuso a partir de Visual Studio 2015. Definida como 001 si la [/CLR: safe](../build/reference/clr-common-language-runtime-compilation.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; M &#95; FP &#95; EXCEPTO** definido como 1 si la [/fp: excepto](../build/reference/fp-specify-floating-point-behavior.md) o [/fp: strict](../build/reference/fp-specify-floating-point-behavior.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; M &#95; FP &#95; RÁPIDO** definido como 1 si la [/fp: Fast](../build/reference/fp-specify-floating-point-behavior.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; M &#95; FP &#95; PRECISA** definido como 1 si la [/fp: precisa](../build/reference/fp-specify-floating-point-behavior.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; M &#95; FP &#95; STRICT** definido como 1 si la [/fp: strict](../build/reference/fp-specify-floating-point-behavior.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; M &#95; IX86** define como el literal entero valor 600 para las compilaciones que procesadores de destino x86. Esta macro no está definida para x64 o destinos de compilación de ARM.

- **&#95; M &#95; IX86 &#95; FP** definido como un valor literal entero que indica la [/arch](../build/reference/arch-arm.md) opción del compilador que se estableció o el valor predeterminado. Esta macro siempre se define cuando el destino de compilación es un x86 procesador. En caso contrario, es indefinido. Cuando se define, el valor es:

  - 0 si el **/arch:IA32** se estableció la opción del compilador.

  - 1 si la **/arch: SSE** se estableció la opción del compilador.

  - 2 si el **/arch: SSE2**, **/arch: AVX** o **/arch:AVX2** se estableció la opción del compilador. Este valor es el valor predeterminado si un **/arch** no se especificó la opción del compilador. Cuando **/arch: AVX** se especifica, la macro **&#95; &#95; AVX &#95; &#95;**  también se define. Cuando **/arch:AVX2** se especifica, ambos **&#95; &#95; AVX &#95; &#95;**  y **&#95; &#95; AVX2 &#95; &#95;**  también se definen.

  - Vea [/arch (x86)](../build/reference/arch-x86.md) para obtener más información.

- **&#95; M &#95; X64** define como el literal entero valor 100 para las compilaciones que procesadores de destino x64. En caso contrario, es indefinido.

- **&#95; ADMINISTRAR** definido como 1 cuando la [/CLR](../build/reference/clr-common-language-runtime-compilation.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; MSC &#95; GENERAR** definido como un literal entero que contiene el elemento de número de revisión del número de versión del compilador. El número de revisión es el cuarto elemento el número de versión delimitado por puntos. Por ejemplo, si el número de versión del compilador de Visual C++ es 15.00.20706.01, la **&#95; MSC &#95; GENERAR** macro se evalúa como 1. Siempre se define esta macro.

- **&#95; MSC &#95; Las extensiones de** definido como 1 si la [/Ze (habilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) se establece la opción de compilador, que es el valor predeterminado. En caso contrario, es indefinido.

- **&#95; MSC &#95; COMPLETO &#95; VER** definido como un literal entero que codifica el principal, secundaria y generar el número de elementos de número de versión del compilador. El número principal es el primer elemento del número de versión delimitado por puntos, el número secundario es el segundo elemento y el número de compilación es el tercer elemento. Por ejemplo, si el número de versión del compilador de Visual C++ es 15.00.20706.01, la **&#95; MSC &#95; COMPLETO &#95; VER** macro se evalúa como 150020706. ¿Escriba **cl /?** en la línea de comandos para ver el número de versión del compilador. Siempre se define esta macro.

- **&#95; MSC &#95; VER** definido como un literal entero que codifica el número de elementos principal y secundario del número de versión del compilador. El número principal es el primer elemento del número de versión delimitado por puntos y el número secundario es el segundo elemento. Por ejemplo, si el número de versión del compilador de Visual C++ es 17.00.51106.1, la **&#95; MSC &#95; VER** macro se evalúa como 1700. ¿Escriba **cl /?** en la línea de comandos para ver el número de versión del compilador. Siempre se define esta macro.

- **&#95; MSVC &#95; LANG** definido como un literal de entero que especifica el estándar del lenguaje C++ dirigido por el compilador. Cuando se compila como C++, la macro es el valor literal entero 201402 si la [/std:c ++ 14](../build/reference/std-specify-language-standard-version.md) se establece la opción del compilador, o de forma predeterminada; se establece a 201703 si el [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md) se establece la opción del compilador; y se establece en un valor más alto, sin especificar cuando el [/std:c ++ más reciente](../build/reference/std-specify-language-standard-version.md). En caso contrario, la macro es indefinida. El **&#95; MSVC &#95; LANG** macro y [/std (versión estándar lenguaje especificar)](../build/reference/std-specify-language-standard-version.md) opciones del compilador están disponibles a partir de Visual Studio 2015 Update 3.

- **&#95; &#95; MSVC &#95; En tiempo de ejecución &#95; COMPRUEBA** definido como 1 cuando uno de los [/RTC](../build/reference/rtc-run-time-error-checks.md) se establece opciones del compilador. En caso contrario, es indefinido.

- **&#95; MT** definido como 1 cuando [/MD o /MDd](../build/reference/md-mt-ld-use-run-time-library.md) (DLL multiproceso) o [/MT o /MTd](../build/reference/md-mt-ld-use-run-time-library.md) (multiproceso) se especifica. En caso contrario, es indefinido.

- **&#95; NATIVO &#95; WCHAR &#95; T &#95; DEFINED** definido como 1 cuando la [/Zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; OPENMP** definido como entero literal 200203, que representa la fecha de la especificación OpenMP implementada por Visual C++, si la [/openmp (habilitar la compatibilidad con OpenMP 2.0)](../build/reference/openmp-enable-openmp-2-0-support.md) se establece la opción del compilador. En caso contrario, es indefinido.

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- **&#95; PREFAST &#95;**  Definido como 1 cuando la [/ analyze](../build/reference/analyze-code-analysis.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; &#95; Marca de tiempo &#95; &#95;**  Definido como un literal de cadena que contiene la fecha y hora de la última modificación del archivo de origen actual, en forma abreviada, constante longitud devuelta por la biblioteca en tiempo de ejecución de C [asctime](../c-runtime-library/reference/asctime-wasctime.md) funcione, por ejemplo, `Fri 19 Aug 13:32:58 2016`. Siempre se define esta macro.

- **&#95; VC &#95; NODEFAULTLIB** definido como 1 cuando la [/Zl (omitir nombre de biblioteca predeterminado)](../build/reference/zl-omit-default-library-name.md) se establece la opción del compilador. En caso contrario, es indefinido.

- **&#95; WCHAR &#95; T &#95; DEFINED** definido como 1 cuando el valor predeterminado [/Zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) se establece la opción del compilador. El **&#95; WCHAR &#95; T &#95; DEFINED** macro está definida pero no tiene ningún valor si el **/Zc:wchar_t-** se establece la opción del compilador, y `wchar_t` se define en un archivo de encabezado del sistema incluido en el proyecto. En caso contrario, es indefinido.

- **&#95; Win32** definido como 1 cuando el destino de compilación es ARM de 32 bits, 64 bits ARM, x86, o x 64. En caso contrario, es indefinido.

- **&#95; Win64** definido como 1 cuando el destino de compilación es x64 o ARM de 64 bits. En caso contrario, es indefinido.

- **&#95; WINRT &#95; DLL** definido como 1 cuando se compila como C++ y ambos [/ZW (compilación de Windows en tiempo de ejecución)](../build/reference/zw-windows-runtime-compilation.md) y [/LD o /LDd](../build/reference/md-mt-ld-use-run-time-library.md) se establecen opciones del compilador. En caso contrario, es indefinido.

 Macros de preprocesador se utilizan para determinar la versión de la biblioteca ATL o MFC no están predefinidas por el compilador. Estas macros están definidas en los encabezados para la biblioteca, por lo que no están definidos en las directivas de preprocesador antes de que se incluye el encabezado necesario.

- **&#95; ATL &#95; VER** definido en \<atldef.h > como un literal entero que codifica el número de versión ATL.

- **&#95; MFC &#95; VER** definido en \<afxver_.h > como un literal entero que codifica el número de versión MFC.

## <a name="see-also"></a>Vea también

[Macros) (C/C ++)](../preprocessor/macros-c-cpp.md)   
[Operadores de preprocesador](../preprocessor/preprocessor-operators.md)   
[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)
