---
title: Macros predefinidas
ms.custom: update_every_version
ms.date: 10/01/2019
f1_keywords:
- _ATL_VER
- __ATOM__
- __AVX__
- __AVX2__
- __AVX512BW__
- __AVX512CD__
- __AVX512DQ__
- __AVX512F__
- __AVX512VL__
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
- __AVX512BW__ macro
- __AVX512CD__ macro
- __AVX512DQ__ macro
- __AVX512F__ macro
- __AVX512VL__ macro
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
ms.openlocfilehash: 57982e32da75aa7f364c51146e50c3d75b4b7710
ms.sourcegitcommit: e805200eaef4fe7a65a00051bbd305273af94fe7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2019
ms.locfileid: "74163339"
---
# <a name="predefined-macros"></a>Macros predefinidas

El compiladorC++ de Microsoft C/(MSVC) predefine ciertas macros de preprocesador, dependiendo del lenguaje (C o C++), el destino de compilación y las opciones del compilador elegidas.

MSVC admite las macros de preprocesador predefinidas que requiere el estándar C99 de ANSI/ISO y los estándares ISO C++ 14 y C++ 17. La implementación también admite varias macros de preprocesador específicas de Microsoft. Algunas macros se definen solo para entornos de compilación específicos o opciones del compilador. Excepto donde se indique, las macros se definen en una unidad de traducción como si se hubieran especificado como argumentos de la opción de compilador **/d** . Cuando se define, el preprocesador expande las macros hasta los valores especificados antes de la compilación. Las macros predefinidas no toman ningún argumento y no se pueden redefinir.

## <a name="standard-predefined-identifier"></a>Identificador predefinido estándar

El compilador admite este identificador predefinido especificado por ISO C99 e ISO C++ 11.

- **&#95; FUNC &#95; &#95;** El nombre no completo y sin adornar de la función de inclusión como una matriz **const static** local de función de **Char**.

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>Macros predefinidas estándar

El compilador admite estas macros predefinidas especificadas por los estándares ISO C99 e ISO C++ 17.

- **&#95;CPlusPlus &#95;** Se define como un valor literal entero cuando la unidad de traducción se compila C++como. De lo contrario, sin definir.

- **&#95; Fecha &#95; &#95;** Fecha de compilación del archivo de código fuente actual. La fecha es un literal de cadena de longitud constante con el formato *MMM DD AAAA*. El nombre del mes *MMM* es el mismo que el nombre del mes abreviado generado por la función [Asctime](../c-runtime-library/reference/asctime-wasctime.md) de la biblioteca en tiempo de ejecución de C (CRT). El primer carácter de la fecha *DD* es un espacio si el valor es menor que 10. Esta macro siempre está definida.

- **&#95;Archivo de &#95;&#95;** Nombre del archivo de código fuente actual. El archivo se expande a un literal de cadena de caracteres. **&#95; &#95;&#95;** Para asegurarse de que se muestra la ruta de acceso completa al archivo, use [/FC (ruta de acceso completa del archivo de código fuente en diagnósticos)](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md). Esta macro siempre está definida.

- **&#95;Línea de &#95;&#95;** Definido como el número de línea entero en el archivo de código fuente actual. El valor de la  **&#95; &#95;macro&#95; line** se puede cambiar mediante una directiva de `#line`. Esta macro siempre está definida.

- **&#95; Stdc &#95; &#95;** Se define como 1 solo cuando se compila como C y si se especifica la opción del compilador [/za](../build/reference/za-ze-disable-language-extensions.md) . De lo contrario, sin definir.

- **&#95;&#95;STDC&#95;se&#95; ha hospedado** como 1 si la implementación es una *implementación hospedada*, una que admite la biblioteca estándar completa requerida. De lo contrario, se define como 0.

- **&#95;&#95;Los&#95;subprocesos&#95; de STDCPP** se definen como 1 si y solo si un programa puede tener más de un subproceso C++de ejecución y se compila como. De lo contrario, sin definir.

- **&#95;Hora de &#95;&#95;** La hora de traducción de la unidad de traducción preprocesada. La hora es un literal de cadena de caracteres con el formato *HH: mm: SS*, igual que la hora devuelta por la función [asctime](../c-runtime-library/reference/asctime-wasctime.md) de CRT. Esta macro siempre está definida.

## <a name="microsoft-specific-predefined-macros"></a>Macros predefinidas específicas de Microsoft

MSVC admite estas macros predefinidas adicionales.

- **&#95; Atom &#95; &#95;** Se define como 1 cuando se establece la opción del compilador [/favor: Atom](../build/reference/favor-optimize-for-architecture-specifics.md) y el destino del compilador es x86 o x64. De lo contrario, sin definir.

- **&#95; AVX &#95; &#95;** Se define como 1 cuando se establecen las opciones del compilador [/Arch: AVX](../build/reference/arch-x86.md), [/Arch: AVX2](../build/reference/arch-x86.md) o [/Arch: AVX512](../build/reference/arch-x86.md) y el destino del compilador es x86 o x64. De lo contrario, sin definir.

- **&#95; AVX2 &#95; &#95;** Se define como 1 cuando se establece la opción del compilador [/Arch: AVX2](../build/reference/arch-x86.md) o [/Arch: AVX512](../build/reference/arch-x86.md) y el destino del compilador es x86 o x64. De lo contrario, sin definir.

- **&#95; AVX512BW &#95; &#95;** Se define como 1 cuando se establece la opción del compilador [/Arch: AVX512](../build/reference/arch-x86.md) y el destino del compilador es x86 o x64. De lo contrario, sin definir.

- **&#95; AVX512CD &#95; &#95;** Se define como 1 cuando se establece la opción del compilador [/Arch: AVX512](../build/reference/arch-x86.md) y el destino del compilador es x86 o x64. De lo contrario, sin definir.

- **&#95; AVX512DQ &#95; &#95;** Se define como 1 cuando se establece la opción del compilador [/Arch: AVX512](../build/reference/arch-x86.md) y el destino del compilador es x86 o x64. De lo contrario, sin definir.

- **&#95; AVX512F &#95; &#95;** Se define como 1 cuando se establece la opción del compilador [/Arch: AVX512](../build/reference/arch-x86.md) y el destino del compilador es x86 o x64. De lo contrario, sin definir.

- **&#95; AVX512VL &#95; &#95;** Se define como 1 cuando se establece la opción del compilador [/Arch: AVX512](../build/reference/arch-x86.md) y el destino del compilador es x86 o x64. De lo contrario, sin definir.

- **&#95;CARÁCTER&#95;sin signo** definido como 1 si el tipo de **carácter** predeterminado es sin signo. Este valor se define cuando se establece la opción del compilador [/j (el tipo de carácter predeterminado es sin signo)](../build/reference/j-default-char-type-is-unsigned.md) . De lo contrario, sin definir.

- **versión de&#95;CLR &#95; &#95;** Se define como un literal entero que representa la versión de Common Language Runtime (CLR) utilizada para compilar la aplicación. El valor se codifica con la forma `Mmmbbbbb`, donde `M` es la versión principal del motor en tiempo de ejecución, `mm` es la versión secundaria del tiempo de ejecución y `bbbbb` es el número de compilación. **&#95;&#95;Se&#95;define CLR ver** si se establece la opción del compilador [/CLR](../build/reference/clr-common-language-runtime-compilation.md) . De lo contrario, sin definir.

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- **&#95;La&#95;protección&#95;de flujo de control** se define como 1 cuando se establece la opción del compilador [/Guard: CF (habilitar protección de flujo de control)](../build/reference/guard-enable-control-flow-guard.md) . De lo contrario, sin definir.

- **&#95;Contador de &#95;&#95;** Se expande a un literal entero que comienza en 0. El valor se incrementa en 1 cada vez que se usa en un archivo de código fuente o en encabezados incluidos del archivo de código fuente. Counter recuerda su estado cuando se utilizan encabezados precompilados. **&#95; &#95;&#95;** Esta macro siempre está definida.

  En este ejemplo se usa `__COUNTER__` para asignar identificadores únicos a tres objetos diferentes del mismo tipo. El constructor `exampleClass` toma un entero como parámetro. En `main`, la aplicación declara tres objetos de tipo `exampleClass`, utilizando `__COUNTER__` como parámetro de identificador único:

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

- **&#95;&#95;la&#95;CLI de CPlusPlus** se define como el valor literal entero 200406 cuando C++ se compila como y se establece una opción del compilador [/CLR](../build/reference/clr-common-language-runtime-compilation.md) . De lo contrario, sin definir. Cuando se define  **&#95; &#95;,&#95;la CLI de CPlusPlus** está en vigor en toda la unidad de traducción.

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

- **&#95;&#95;CPlusPlus&#95;winrt** definido como el valor literal entero 201009 cuando se compila como C++ y se establece la opción del compilador [/ZW (Windows Runtime](../build/reference/zw-windows-runtime-compilation.md) Compilation). De lo contrario, sin definir.

- **&#95;CPPRTTI** Se define como 1 si se establece la opción de compilación [/gr (habilitar información de tipo en tiempo de ejecución)](../build/reference/gr-enable-run-time-type-information.md) . De lo contrario, sin definir.

- **&#95;CPPUNWIND** Definido como 1 si se han establecido una o varias de las opciones [/GX (habilitar control de excepciones)](../build/reference/gx-enable-exception-handling.md), [/CLR (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)o [/EH (modelo de control de excepciones)](../build/reference/eh-exception-handling-model.md) . De lo contrario, sin definir.

- **&#95;Depuración** Se define como 1 cuando se establece la opción del compilador [/LDd](../build/reference/md-mt-ld-use-run-time-library.md), [/mdd](../build/reference/md-mt-ld-use-run-time-library.md)o [/MTD](../build/reference/md-mt-ld-use-run-time-library.md) . De lo contrario, sin definir.

- DLL se define como 1 cuando se establece la opción del compilador [/MD](../build/reference/md-mt-ld-use-run-time-library.md) o [/mdd](../build/reference/md-mt-ld-use-run-time-library.md) (DLL multiproceso).  **&#95;** De lo contrario, sin definir.

- **&#95; FUNCDNAME &#95; &#95;** Se define como un literal de cadena que contiene el [nombre representativo](../build/reference/decorated-names.md) de la función de inclusión. La macro solo se define dentro de una función. **&#95;La &#95;macro&#95; FUNCDNAME** no se expande si usa la opción del compilador [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) o [/p](../build/reference/p-preprocess-to-a-file.md) .

   En este ejemplo se usan las macros `__FUNCDNAME__`, `__FUNCSIG__`y `__FUNCTION__` para mostrar la información de la función.

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- **&#95; FUNCSIG &#95; &#95;** Definido como un literal de cadena que contiene la firma de la función de inclusión. La macro solo se define dentro de una función. **&#95;La &#95;macro&#95; FUNCSIG** no se expande si usa la opción del compilador [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) o [/p](../build/reference/p-preprocess-to-a-file.md) . Cuando se compila para un destino de 64 bits, la Convención de llamada se `__cdecl` de forma predeterminada. Para obtener un ejemplo de uso, vea la macro `__FUNCDNAME__`.

- **&#95; Función &#95; &#95;** Definido como un literal de cadena que contiene el nombre no representativo de la función de inclusión. La macro solo se define dentro de una función. La macro de  **&#95; &#95;&#95; función** no se expande si usa la opción del compilador [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) o [/p](../build/reference/p-preprocess-to-a-file.md) . Para obtener un ejemplo de uso, vea la macro `__FUNCDNAME__`.

- **bits máximos&#95;enteros&#95; &#95;** Definido como el valor literal entero 64, el tamaño máximo (en bits) para un tipo entero no vector. Esta macro siempre está definida.

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- **&#95; IntelliSense &#95; &#95;** Se define como 1 durante un paso del compilador de IntelliSense en el IDE de Visual Studio. De lo contrario, sin definir. Puede usar esta macro para proteger el código que el compilador de IntelliSense no entiende o usarlo para alternar entre el compilador de compilación e IntelliSense. Para obtener más información, vea [sugerencias para la solución de problemas de la lentitud de IntelliSense](https://devblogs.microsoft.com/cppblog/troubleshooting-tips-for-intellisense-slowness/).

- **&#95;ISO&#95;volatile** se define como 1 si se establece la opción de compilador [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) . De lo contrario, sin definir.

- **&#95;Modo&#95;kernel** definido como 1 si se establece la opción del compilador [/kernel (crear binario en modo kernel)](../build/reference/kernel-create-kernel-mode-binary.md) . De lo contrario, sin definir.

- **&#95;AMD64&#95;** Definido como el valor literal entero 100 para las compilaciones que tienen como destino procesadores x64. De lo contrario, sin definir.

- **&#95;ARM&#95;M** Definido como el valor literal entero 7 para las compilaciones que tienen como destino Procesadores ARM. De lo contrario, sin definir.

- **&#95;M&#95;ARM&#95;ARMV7VE** se define como 1 cuando se establece la opción del compilador [/Arch: ARMV7VE](../build/reference/arch-arm.md) para compilaciones que tienen como destino Procesadores ARM. De lo contrario, sin definir.

- **&#95;M&#95;ARM&#95;FP** definido como un valor literal entero que indica qué opción del compilador [/Arch](../build/reference/arch-arm.md) se estableció para los destinos de procesador ARM. De lo contrario, sin definir.

  - Un valor en el intervalo 30-39 si no se especificó ninguna opción de ARM `/arch`, lo que indica que se ha establecido la arquitectura predeterminada para ARM (`VFPv3`).

  - Un valor en el intervalo 40-49 si se estableció `/arch:VFPv4`.

  - Para obtener más información, consulte [/Arch (ARM)](../build/reference/arch-arm.md).

- **&#95;M&#95;ARM64** Definido como 1 para las compilaciones que tienen como destino Procesadores ARM de 64 bits. De lo contrario, sin definir.

- **&#95;M&#95;CEE** se define como 001 si se establece una opción del compilador [/CLR (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) . De lo contrario, sin definir.

- **M&#95;CEE&#95;puro &#95;** En desuso a partir de Visual Studio 2015. Definido como 001 si se establece la opción del compilador [/clr: Pure](../build/reference/clr-common-language-runtime-compilation.md) . De lo contrario, sin definir.

- **&#95;M.&#95;seguro &#95;** En desuso a partir de Visual Studio 2015. Definido como 001 si se establece la opción del compilador [/clr: Safe](../build/reference/clr-common-language-runtime-compilation.md) . De lo contrario, sin definir.

- **&#95;M&#95;FP&#95;excepto** definido como 1 si se establece la opción de compilador [/FP: Except](../build/reference/fp-specify-floating-point-behavior.md) o [/FP: STRICT](../build/reference/fp-specify-floating-point-behavior.md) . De lo contrario, sin definir.

- **&#95;M&#95;FP&#95;Fast** definido como 1 si se establece la opción del compilador [/FP: Fast](../build/reference/fp-specify-floating-point-behavior.md) . De lo contrario, sin definir.

- **&#95;M&#95;FP&#95;precise** definido como 1 si se establece la opción de compilador [/FP: precise](../build/reference/fp-specify-floating-point-behavior.md) . De lo contrario, sin definir.

- **&#95;M&#95;FP&#95;STRICT** definido como 1 si se establece la opción del compilador [/FP: STRICT](../build/reference/fp-specify-floating-point-behavior.md) . De lo contrario, sin definir.

- **&#95;M&#95;IX86** Definido como el valor literal entero 600 para las compilaciones que tienen como destino procesadores x86. Esta macro no está definida para los destinos de compilación x64 o ARM.

- **&#95;M&#95;IX86&#95;FP** definido como un valor literal entero que indica la opción del compilador [/Arch](../build/reference/arch-arm.md) establecida, o el valor predeterminado. Esta macro siempre se define cuando el destino de compilación es un procesador x86. De lo contrario, sin definir. Cuando se define, el valor es:

  - 0 si se estableció la opción del compilador `/arch:IA32`.

  - 1 si se ha establecido la opción del compilador `/arch:SSE`.

  - 2 si se estableció la opción del compilador `/arch:SSE2`, `/arch:AVX`, `/arch:AVX2`o `/arch:AVX512`. Este valor es el predeterminado si no se especificó una opción del compilador `/arch`. Cuando se especifica `/arch:AVX`, también se define la macro **&#95; &#95;AVX&#95;** . Cuando se especifica `/arch:AVX2`, **&#95; &#95;&#95;** también se definen AVX y **&#95; &#95;AVX2&#95;** . Cuando se especifica `/arch:AVX512`,  **&#95; &#95;&#95;** se definen también AVX,  **&#95; &#95;AVX2&#95;** ,  **&#95; &#95;AVX512BW&#95;** ,  **&#95; &#95;AVX512CD&#95;** , **&#95;AVX512DQ, &#95; &#95;** **AVX512F &#95;y&#95; AVX512VL. &#95;** **&#95; &#95;&#95;**

  - Para obtener más información, consulte [/arch (x86)](../build/reference/arch-x86.md).

- **&#95;M&#95;x64** Definido como el valor literal entero 100 para las compilaciones que tienen como destino procesadores x64. De lo contrario, sin definir.

- **&#95;Administrados** Se define como 1 cuando se establece la opción del compilador [/CLR](../build/reference/clr-common-language-runtime-compilation.md) . De lo contrario, sin definir.

- MSC (compilación)  **&#95;&#95;** Se define como un literal entero que contiene el elemento de número de revisión del número de versión del compilador. El número de revisión es el cuarto elemento del número de versión delimitado por puntos. Por ejemplo, si el número de versión del compiladorC++ de Microsoft C/es 15.00.20706.01, la  **&#95;macro de compilación MSC&#95;** se evalúa como 1. Esta macro siempre está definida.

- **&#95;Extensiones&#95;MSC** definidas como 1 si se establece la opción de compilador habilitado de forma predeterminada [(habilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) . De lo contrario, sin definir.

- **MSC&#95;&#95;completa &#95;** Se define como un literal entero que codifica los elementos de número principal, secundario y de compilación del número de versión del compilador. El número principal es el primer elemento del número de versión delimitado por puntos, el número secundario es el segundo elemento y el número de compilación es el tercer elemento. Por ejemplo, si el número de versión del compiladorC++ de Microsoft C/es 15.00.20706.01, la macro de  **&#95;la versión&#95;completa&#95;de MSC** se evalúa como 150020706. Escriba `cl /?` en la línea de comandos para ver el número de versión del compilador. Esta macro siempre está definida.

- **&#95;MSC&#95;ver** Se define como un literal entero que codifica los elementos de número principal y secundario del número de versión del compilador. El número principal es el primer elemento del número de versión delimitado por puntos y el número secundario es el segundo elemento. Por ejemplo, si el número de versión del compiladorC++ de Microsoft C/es 17.00.51106.1, la  **&#95;macro MSC&#95;ver** se evalúa como 1700. Escriba `cl /?` en la línea de comandos para ver el número de versión del compilador. Esta macro siempre está definida.

   |Versión de Visual Studio|**&#95;MSC&#95;ver**|
   |-|-|
   |Visual Studio 6.0|1200|
   |Visual Studio .NET 2002 (7,0)|1300|
   |Visual Studio .NET 2003 (7,1)|1310|
   |Visual Studio 2005 (8,0)|1400|
   |Visual Studio 2008 (9,0)|1500|
   |Visual Studio 2010 (10,0)|1600|
   |Visual Studio 2012 (11,0)|1700|
   |Visual Studio 2013 (12,0)|1800|
   |Visual Studio 2015 (14,0)|1900|
   |Visual Studio 2017 RTW (15,0)|1910|
   |Visual Studio 2017 versión 15.3|1911|
   |Versión 15.5 de Visual Studio 2017|1912|
   |Visual Studio 2017, versión 15.6|1913|
   |Visual Studio 2017 versión 15.7|1914|
   |Visual Studio 2017, versión 15.8|1915|
   |Visual Studio 2017 versión 15,9|1916|
   |Visual Studio 2019 RTW (16,0)|1920|
   |Visual Studio 2019, versión 16.1|1921|
   |Visual Studio 2019, versión 16.2|1922|
   |Visual Studio 2019 versión 16,3|1923|

   Para probar las versiones del compilador o las actualizaciones en una versión determinada de Visual Studio o después, utilice el operador **>=** . Puede utilizarlo en una directiva condicional para comparar  **&#95;MSC&#95;ver** con esa versión conocida. Si tiene varias versiones mutuamente excluyentes para compararlas, ordene las comparaciones en orden descendente de número de versión. Por ejemplo, este código comprueba los compiladores publicados en Visual Studio 2017 y versiones posteriores. A continuación, comprueba los compiladores publicados en o después de Visual Studio 2015. Después, comprueba todos los compiladores publicados antes de Visual Studio 2015:

   ```cpp
   #if _MSC_VER >= 1910
   // . . .
   #elif _MSC_VER >= 1900
   // . . .
   #else
   // . . .
   #endif
   ```

   Para obtener más información, [vea C++ versión del compilador visual](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/) en el blog del equipo de Microsoft. C++

- **&#95;MSVC&#95;lang** definido como un literal entero que especifica el C++ lenguaje estándar de destino del compilador. Se establece solo en código compilado como C++. La macro es el valor literal entero 201402L de forma predeterminada o cuando se especifica la opción del compilador [/STD: c++ 14](../build/reference/std-specify-language-standard-version.md) . La macro se establece en 201703L si se especifica la opción del compilador [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md) . Se establece en un valor mayor que no se especifica cuando se especifica la opción [/STD: c + + latest](../build/reference/std-specify-language-standard-version.md) . De lo contrario, la macro no está definida. La  **&#95;macro&#95;MSVC lang** y las opciones de compilador [/STD (especificar la versión estándar del lenguaje)](../build/reference/std-specify-language-standard-version.md) están disponibles a partir de Visual Studio 2015 Update 3.

- **&#95;&#95;Las&#95;comprobaciones en tiempo de&#95;ejecución de MSVC** se definen como 1 cuando se establece una de las opciones del compilador [/RTC](../build/reference/rtc-run-time-error-checks.md) . De lo contrario, sin definir.

- **&#95;MSVC&#95;Traditional** se define como 0 cuando se establece la opción del compilador [/experimental: preprocesador](../build/reference/experimental-preprocessor.md) . Se define como 1 de forma predeterminada, o cuando se establece la opción del compilador [/experimental: preprocesador](../build/reference/experimental-preprocessor.md) , para indicar que el preprocesador tradicional está en uso. La opción del compilador  **&#95;MSVC&#95;tradicional** macro y [/experimental: preprocesador (Habilitar modo de conformidad del preprocesador)](../build/reference/experimental-preprocessor.md) está disponible a partir de la versión 15,8 de Visual Studio 2017.

   ```cpp
   #if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
   // Logic using the traditional preprocessor
   #else
   // Logic using cross-platform compatible preprocessor
   #endif
   ```

- **&#95;MT** Se define como 1 cuando se especifican [/MD o/mdd](../build/reference/md-mt-ld-use-run-time-library.md) (DLL multiproceso) o [/MT o/MTD](../build/reference/md-mt-ld-use-run-time-library.md) (multiproceso). De lo contrario, sin definir.

- **&#95;El&#95;valor&#95;de&#95;WCHAR nativo se define** como 1 cuando se establece la opción del compilador [/Zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) . De lo contrario, sin definir.

- **&#95;OpenMP** Definido como literal entero 200203, si se establece la opción del compilador [/OpenMP (Habilitar compatibilidad con openmp 2,0)](../build/reference/openmp-enable-openmp-2-0-support.md) . Este valor representa la fecha de la especificación de OpenMP implementada por MSVC. De lo contrario, sin definir.

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- **&#95;PREfast&#95;** Se define como 1 cuando se establece la opción del compilador [/Analyze](../build/reference/analyze-code-analysis.md) . De lo contrario, sin definir.

- Marca de tiempo **&#95; &#95;&#95;** Se define como un literal de cadena que contiene la fecha y hora de la última modificación del archivo de código fuente actual, en el formato de longitud constante abreviado devuelto por la función [asctime](../c-runtime-library/reference/asctime-wasctime.md) de CRT, por ejemplo, `Fri 19 Aug 13:32:58 2016`. Esta macro siempre está definida.

- **&#95;VC&#95;NODEFAULTLIB** se define como 1 cuando se establece la opción del compilador [/ZL (omitir nombre de biblioteca predeterminada)](../build/reference/zl-omit-default-library-name.md) . De lo contrario, sin definir.

- **&#95;WCHAR&#95;T&#95;definido** se define como 1 cuando se establece la opción del compilador [/Zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) predeterminada. La  **&#95;macro&#95;definida&#95;WCHAR T** está definida pero no tiene ningún valor si se establece la opción del compilador `/Zc:wchar_t-` y **wchar_t** se define en un archivo de encabezado del sistema incluido en el proyecto. De lo contrario, sin definir.

- **&#95;Win32** Se define como 1 cuando el destino de compilación es ARM de 32 bits, ARM de 64 bits, x86 o x64. De lo contrario, sin definir.

- **&#95;WIN64** para Se define como 1 cuando el destino de compilación es de 64 bits ARM o x64. De lo contrario, sin definir.

- **&#95;La&#95;dll de WINRT** se define como 1 C++ cuando se compila como y se establecen las opciones del compilador [/ZW (Windows Runtime compilación)](../build/reference/zw-windows-runtime-compilation.md) y [/LD o/LDd](../build/reference/md-mt-ld-use-run-time-library.md) . De lo contrario, sin definir.

No hay macros de preprocesador que identifiquen la versión de la biblioteca ATL o MFC predefinidas por el compilador. Los encabezados de la biblioteca ATL y MFC definen internamente estas macros de versión. No están definidas en las directivas de preprocesador realizadas antes de incluir el encabezado necesario.

- **&#95;ver&#95;ATL** Se define en \<atldef. h > como un literal entero que codifica el número de versión de ATL.

- **&#95;ver&#95;MFC** Se define en \<afxver_. h > como un literal entero que codifica el número de versión de MFC.

## <a name="see-also"></a>Vea también

[Macros (C/C++)](../preprocessor/macros-c-cpp.md)<br/>
[Operadores de preprocesador](../preprocessor/preprocessor-operators.md)<br/>
[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)
