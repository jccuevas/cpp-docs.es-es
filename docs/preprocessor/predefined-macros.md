---
title: "Macros predefinidas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_ATL_VER"
  - "__ATOM__"
  - "__AVX__"
  - "__AVX2__"
  - "_CHAR_UNSIGNED"
  - "__CLR_VER"
  - "_CONTROL_FLOW_GUARD"
  - "__COUNTER__"
  - "__cplusplus"
  - "__cplusplus_cli"
  - "__cplusplus_winrt"
  - "_CPPRTTI"
  - "_CPPUNWIND"
  - "__DATE__"
  - "_DEBUG"
  - "_DLL"
  - "__FILE__"
  - "__FUNCDNAME__"
  - "__FUNCSIG__"
  - "__FUNCTION__"
  - "_INTEGRAL_MAX_BITS"
  - "_ISO_VOLATILE"
  - "_KERNEL_MODE"
  - "__LINE__"
  - "_M_AMD64"
  - "_M_ARM"
  - "_M_ARM_ARMV7VE"
  - "_M_ARM_FP"
  - "_M_ARM64"
  - "_M_CEE"
  - "_M_CEE_PURE"
  - "_M_CEE_SAFE"
  - "_M_FP_EXCEPT"
  - "_M_FP_FAST"
  - "_M_FP_PRECISE"
  - "_M_FP_STRICT"
  - "_M_IX86"
  - "_M_IX86_FP"
  - "_M_X64"
  - "_MANAGED"
  - "_MFC_VER"
  - "_MSC_BUILD"
  - "_MSC_EXTENSIONS"
  - "_MSC_FULL_VER"
  - "_MSC_VER"
  - "_MSVC_LANG"
  - "__MSVC_RUNTIME_CHECKS"
  - "_MT"
  - "_NATIVE_WCHAR_T_DEFINED"
  - "_NO_SIZED_DEALLOCATION"
  - "_OPENMP"
  - "_PREFAST_"
  - "_RESUMABLE_FUNCTIONS_SUPPORTED"
  - "_RTC_CONVERSION_CHECKS_ENABLED"
  - "__STDC__"
  - "__STDC_HOSTED__"
  - "__STDCPP_THREADS__"
  - "__TIME__"
  - "__TIMESTAMP__"
  - "__VA_ARGS__"
  - "_VC_NODEFAULTLIB"
  - "_WCHAR_T_DEFINED"
  - "_WIN32"
  - "_WIN64"
  - "_WINRT_DLL"
  - "__func__"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "marcas de tiempo de macro de preprocesador"
  - "cl.exe (compilador), número de versión"
  - "números de versión, el compilador de C o C++ (cl.exe)"
  - "macros predefinidas de C++"
  - "macros de preprocesador,"
  - "macros predefinidas"
  - "_ATL_VER (macro)"
  - "Macro __ATOM__"
  - "__AVX__ macro"
  - "__AVX2__ macro"
  - "_CHAR_UNSIGNED (macro)"
  - "__CLR_VER (macro)"
  - "Macro _CONTROL_FLOW_GUARD"
  - "__COUNTER__ (macro)"
  - "__cplusplus (macro)"
  - "__cplusplus_cli macro"
  - "__cplusplus_winrt macro"
  - "_CPPRTTI (macro)"
  - "_CPPUNWIND (macro)"
  - "__DATE__ (macro)"
  - "_DEBUG (macro)"
  - "_DLL (macro)"
  - "__FILE__ (macro)"
  - "__FUNCDNAME__ (macro)"
  - "__FUNCSIG__ (macro)"
  - "__FUNCTION__ (macro)"
  - "_INTEGRAL_MAX_BITS (macro)"
  - "Macro _ISO_VOLATILE"
  - "Macro _KERNEL_MODE"
  - "__LINE__ (macro)"
  - "_M_AMD64 macro"
  - "_M_ARM macro"
  - "_M_ARM_ARMV7VE (macro)"
  - "_M_ARM_FP macro"
  - "_M_ARM64 (macro)"
  - "_M_CEE (macro)"
  - "_M_CEE_PURE (macro)"
  - "_M_CEE_SAFE (macro)"
  - "Macro _M_FP_EXCEPT"
  - "Macro _M_FP_FAST"
  - "Macro _M_FP_PRECISE"
  - "Macro _M_FP_STRICT"
  - "_M_IX86 (macro)"
  - "_M_IX86_FP (macro)"
  - "_M_X64 (macro)"
  - "_MANAGED (macro)"
  - "_MFC_VER (macro)"
  - "_MSC_BUILD (macro)"
  - "_MSC_EXTENSIONS (macro)"
  - "_MSC_FULL_VER (macro)"
  - "_MSC_VER (macro)"
  - "Macro _MSVC_LANG"
  - "__MSVC_RUNTIME_CHECKS (macro)"
  - "_MT (macro)"
  - "_NATIVE_WCHAR_T_DEFINED (macro)"
  - "Macro _NO_SIZED_DEALLOCATION"
  - "_OPENMP (macro)"
  - "Macro _PREFAST_"
  - "Macro _RESUMABLE_FUNCTIONS_SUPPORTED"
  - "Macro _RTC_CONVERSION_CHECKS_ENABLED"
  - "__STDC__ (macro)"
  - "Macro __STDC_HOSTED__"
  - "Macro __STDCPP_THREADS__"
  - "__TIME__ (macro)"
  - "__TIMESTAMP__ (macro)"
  - "Macro __VA_ARGS__"
  - "_VC_NODEFAULTLIB (macro)"
  - "_WCHAR_T_DEFINED (macro)"
  - "_WIN32 (macro)"
  - "_WIN64 (macro)"
  - "Macro _WINRT_DLL"
  - "identificador de __func__"
ms.assetid: 1cc5f70a-a225-469c-aed0-fe766238e23f
caps.latest.revision: 75
caps.handback.revision: 75
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Macros predefinidas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El compilador de Visual C++ predefine ciertas macros de preprocesador, según el lenguaje (C o C++), el destino de compilación y las opciones del compilador elegido.  
  
 Visual C++ admite el necesarias macros predefinidas de preprocesador especificadas por el estándar ANSI/ISO C99 y ISO C ++ 14 estándar. La implementación también admite varias macros de preprocesador específicos de Microsoft más. Algunas macros se definen sólo para entornos de compilación concreta o las opciones del compilador. A menos que se indique lo contrario, las macros se definen en una unidad de traducción como si se especificaron como **/D** argumentos de la opción de compilador. Cuando se define, se expanden las macros en los valores especificados por el preprocesador antes de la compilación. Las macros predefinidas no toman ningún argumento y no se puede redefinir.  
  
## <a name="standard-predefined-identifier"></a>Identificador predefinido estándar  
 El compilador admite este identificador predefinido especificado por ISO C99 e ISO C ++ 11.  
  
-   **__func\_\_** el nombre de la función de inclusión como una función local no completo y sin adornar `static``const` matriz de `char`.  
  
    ```cpp  
    void example(){  
        printf("%s\n", __func__);  
    } // prints "example"  
    ```  
  
## <a name="standard-predefined-macros"></a>Macros predefinidas estándares  
 El compilador admite estas macros predefinidas especificadas por la ISO C99 y ISO C ++ 14 estándares.  
  
-   **__cplusplus** definido como un valor literal de entero, cuando la unidad de traducción se compila como C++. En caso contrario, es indefinido.  
  
-   **__DATE\_\_** la fecha de compilación del archivo de origen actual. La fecha es una cadena de longitud constante literal del formulario *Mmm dd aaaa*. El nombre del mes *Mmm* es igual que el nombre abreviado del mes en las fechas que genera la biblioteca de tiempo de ejecución de C [asctime](../c-runtime-library/reference/asctime-wasctime.md) (función). El primer carácter de fecha *dd* es un espacio si el valor es menor que 10. Siempre se define esta macro.  
  
-   **__Sistema\_\_** el nombre del archivo de origen actual. **__Sistema\_\_** se expande a un literal de cadena de caracteres. Para asegurarse de que se muestra la ruta de acceso completa al archivo, use [/FC (Full ruta de acceso del archivo de código fuente en diagnósticos)](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md). Siempre se define esta macro.  
  
-   **__LINE\_\_** definido como el número de línea de entero en el archivo de origen actual. El valor de la **__LINE\_\_** macro puede cambiarse mediante una `#line` Directiva. Siempre se define esta macro.  
  
-   **__STDC\_\_** se define como 1 sólo cuando se compila como C y si el [/Za](../build/reference/za-ze-disable-language-extensions.md) se especifica la opción del compilador. En caso contrario, es indefinido.  
  
-   **__STDC_HOSTED\_\_** definido como 1 si la implementación es un *hospedado implementación*, que es compatible con la biblioteca estándar requiere completa. De lo contrario, se define como 0.  
  
-   **__STDCPP_THREADS\_\_** se define como 1 si y solo si un programa puede tener más de un subproceso de ejecución y compila como C++. En caso contrario, es indefinido.  
  
-   **__TIME\_\_** el momento de la traducción de la unidad de traducción preprocesada. El tiempo es una cadena de caracteres literales del formulario *hh: mm:*, igual que el tiempo devuelto por la biblioteca de tiempo de ejecución de C [asctime](../c-runtime-library/reference/asctime-wasctime.md) (función). Siempre se define esta macro.  
  
## <a name="microsoft-specific-predefined-macros"></a>Macros predefinidas específicas de Microsoft  
 Microsoft Visual C++ admite estas macros predefinidas adicionales.  
  
-   **__ATOM\_\_** definido como 1 cuando la [/favor:ATOM](../build/reference/favor-optimize-for-architecture-specifics.md) se establece la opción del compilador y el destino del compilador es x86 o x64. En caso contrario, es indefinido.  
  
-   **__AVX\_\_** definido como 1 cuando el [/arch: AVX](../build/reference/arch-x86.md) o [/arch:AVX2](../build/reference/arch-x86.md) se establecen opciones del compilador y el destino del compilador es x86 o x64. En caso contrario, es indefinido.  
  
-   **__AVX2\_\_** definido como 1 cuando la [/arch:AVX2](../build/reference/arch-x86.md) se establece la opción del compilador y el destino del compilador es x86 o x64. En caso contrario, es indefinido.  
  
-   **_CHAR_UNSIGNED** definido como 1 si el valor predeterminado `char` tipo es sin signo. Esto se establece cuando el [/J (el carácter predeterminado es de tipo sin signo)](../build/reference/j-default-char-type-is-unsigned.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **__CLR_VER** definido como un literal entero que representa la versión de common language runtime usada cuando se compiló la aplicación. El valor está codificado en forma `Mmmbbbbb`, donde `M` es la versión principal del tiempo de ejecución, `mm` es la versión secundaria del tiempo de ejecución, y `bbbbb` es el número de compilación. **__CLR_VER** se define si la [/CLR](../build/reference/clr-common-language-runtime-compilation.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
    ```cpp  
    // clr_ver.cpp  
    // compile with: /clr  
    using namespace System;  
    int main() {  
       Console::WriteLine(__CLR_VER);  
    }  
    ```  
  
-   **_CONTROL_FLOW_GUARD** definido como 1 cuando el [/guard:cf (habilitar Control de flujo de protegerse)](../build/reference/guard-enable-control-flow-guard.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **__COUNTER\_\_** amplía a un literal entero que comienza en 0 y se incrementa en 1 cada vez que se utiliza en un archivo de origen o incluir los encabezados del archivo de origen. **__COUNTER\_\_** recuerda a su estado cuando se utilizan encabezados precompilados. Siempre se define esta macro.  
  
     Este ejemplo utiliza `__COUNTER__` para asignar identificadores únicos a tres objetos diferentes del mismo tipo. El `exampleClass` constructor toma un entero como parámetro. En `main`, la aplicación declara tres objetos de tipo `exampleClass`, con `__COUNTER__` como parámetro de identificador único:  
  
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
  
-   **__cplusplus_cli** definido como el valor literal entero 200406 cuando se compila como C++ y [/CLR](../build/reference/clr-common-language-runtime-compilation.md), [/clr: pure](../build/reference/clr-common-language-runtime-compilation.md), o [/clr: safe](../build/reference/clr-common-language-runtime-compilation.md) se establece la opción del compilador. En caso contrario, es indefinido. Cuando se define, **__cplusplus_cli** está activo en la unidad de traducción.  
  
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
  
-   **__cplusplus_winrt** definido como el valor literal entero 201009 cuando se compila como C++ y [/ZW (compilación en tiempo de ejecución de Windows)](../build/reference/zw-windows-runtime-compilation.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **_CPPRTTI** definido como 1 si la [/GR (habilitar información de tipo en tiempo de ejecución)](../build/reference/gr-enable-run-time-type-information.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **_CPPUNWIND** se define como 1 si uno o varios de los [/GX (habilitar el control de excepciones)](../build/reference/gx-enable-exception-handling.md), [/clr (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), o [/EH (Exception Handling Model)](../build/reference/eh-exception-handling-model.md) se establecen opciones del compilador. En caso contrario, es indefinido.  
  
-   **_DEBUG** definido como 1 cuando la [/LDd](../build/reference/md-mt-ld-use-run-time-library.md), [MDd](../build/reference/md-mt-ld-use-run-time-library.md), o [/MTd](../build/reference/md-mt-ld-use-run-time-library.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **_DLL** definido como 1 cuando la [/MD](../build/reference/md-mt-ld-use-run-time-library.md) o [MDd](../build/reference/md-mt-ld-use-run-time-library.md) se establece la opción del compilador (DLL multiproceso). En caso contrario, es indefinido.  
  
-   **__FUNCDNAME\_\_** definido como un literal de cadena que contiene el [nombre representativo](../build/reference/decorated-names.md) de la función de inclusión. La macro se define únicamente dentro de una función. El **__FUNCDNAME\_\_** macro no se expande si usa el [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) o [/P](../build/reference/p-preprocess-to-a-file.md) opción del compilador.  
  
     Este ejemplo se utiliza la `__FUNCDNAME__`, `__FUNCSIG__`, y `__FUNCTION__` macros para mostrar información de la función.  
  
     [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]  
  
-   **__FUNCSIG\_\_** definido como un literal de cadena que contiene la firma de la función de inclusión. La macro se define únicamente dentro de una función. El **__FUNCSIG\_\_** macro no se expande si usa el [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) o [/P](../build/reference/p-preprocess-to-a-file.md) opción del compilador. Cuando se compila para un destino de 64 bits, la convención de llamada es `__cdecl` de forma predeterminada. Para obtener un ejemplo de uso, consulte el `__FUNCDNAME__` (macro).  
  
-   **__FUNCTION\_\_** definido como un literal de cadena que contiene el nombre no representativo de la función de inclusión. La macro se define únicamente dentro de una función. El **__FUNCTION\_\_** macro no se expande si usa el [/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md) o [/P](../build/reference/p-preprocess-to-a-file.md) opción del compilador. Para obtener un ejemplo de uso, consulte el `__FUNCDNAME__` (macro).  
  
-   **_INTEGRAL_MAX_BITS** definido como el valor literal entero 64, el tamaño máximo (en bits) para un tipo entero no vectorial. Siempre se define esta macro.  
  
    ```cpp  
    // integral_max_bits.cpp  
    #include <stdio.h>  
    int main() {  
       printf("%d\n", _INTEGRAL_MAX_BITS);  
    }  
    ```  
  
-   **__INTELLISENSE\_\_** definido como paso 1 durante un compilador de IntelliSense en el IDE de Visual Studio. En caso contrario, es indefinido. Puede usar esta macro para proteger el código el compilador IntelliSense no entender o usar para alternar entre la compilación y el compilador de IntelliSense. Para obtener más información, consulte [sugerencias de solución de problemas de IntelliSense lentitud](https://blogs.msdn.microsoft.com/vcblog/2011/03/29/troubleshooting-tips-for-intellisense-slowness/).  
  
-   **_ISO_VOLATILE** definido como 1 si el [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **_KERNEL_MODE** definido como 1 si la [/kernel (crear binario en modo Kernel)](../build/reference/kernel-create-kernel-mode-binary.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **_M_AMD64** definido como el literal entero valor 100 para las compilaciones que procesadores x64 de destino. En caso contrario, es indefinido.  
  
-   **_M_ARM** definido como el valor literal entero 7 para las compilaciones que tienen como destino procesadores ARM. En caso contrario, es indefinido.  
  
-   **_M_ARM_ARMV7VE** definido como 1 cuando la [armv7ve](../build/reference/arch-arm.md) se establece la opción del compilador para las compilaciones que tienen como destino procesadores ARM. En caso contrario, es indefinido.  
  
-   **_M_ARM_FP** definido como un valor literal entero que indica qué [/arch](../build/reference/arch-arm.md) se estableció la opción del compilador, si el destino de compilación es un procesador ARM. En caso contrario, es indefinido.  
  
    -   En el intervalo 30-39 si no hay ningún **/arch** se especificó la opción de ARM, que indica la arquitectura predeterminada de ARM se estableció (`VFPv3`).  
  
    -   En el intervalo 40-49 si **vfpv4** se estableció.  
  
    -   Consulte [/arch (ARM)](../build/reference/arch-arm.md) para obtener más información.  
  
-   **_M_ARM64** definido como 1 para las compilaciones que tienen como destino procesadores ARM de 64 bits. En caso contrario, es indefinido.  
  
-   **_M_CEE** definido como 001 si cualquier [/clr (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **_M_CEE_PURE** definida como 001 si el [/clr: pure](../build/reference/clr-common-language-runtime-compilation.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **_M_CEE_SAFE** definida como 001 si el [/clr: safe](../build/reference/clr-common-language-runtime-compilation.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **_M_FP_EXCEPT** definido como 1 si el [/fp: excepto](../build/reference/fp-specify-floating-point-behavior.md) o [/fp: strict](../build/reference/fp-specify-floating-point-behavior.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **_M_FP_FAST** definido como 1 si el [/fp: Fast](../build/reference/fp-specify-floating-point-behavior.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **_M_FP_PRECISE** definido como 1 si el [/fp: precisa](../build/reference/fp-specify-floating-point-behavior.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **_M_FP_STRICT** definido como 1 si el [/fp: strict](../build/reference/fp-specify-floating-point-behavior.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **_M_IX86** definido como valor de literal entero 600 para las compilaciones que procesadores x86 de destino. Esta macro no está definida para x64 o destinos de compilación de ARM.  
  
-   **_M_IX86_FP** definido como un valor literal entero que indica la [/arch](../build/reference/arch-arm.md) opción del compilador que se estableció o el valor predeterminado. Esta macro siempre se define cuando el destino de compilación es un x86 procesador. En caso contrario, es indefinido. Cuando se define, el valor es:  
  
    -   0 si el **/arch:IA32** se ha establecido la opción del compilador.  
  
    -   1 si la **/arch: SSE** se ha establecido la opción del compilador.  
  
    -   2 si el **/arch: SSE2**, **/arch: AVX** o **/arch:AVX2** se ha establecido la opción del compilador. Este valor es el valor predeterminado si un **/arch** no se especificó la opción del compilador. Cuando **/arch: AVX** se especifica, la macro **__AVX\_\_** también está definido. Cuando **/arch:AVX2** se especifica, ambos **__AVX\_\_** y **__AVX2\_\_** también se definen.  
  
    -   Vea [/arch (x86)](../build/reference/arch-x86.md) para obtener más información.  
  
-   **_M_X64** definido como el literal entero valor 100 para las compilaciones que procesadores x64 de destino. En caso contrario, es indefinido.  
  
-   **_MANAGED** definido como 1 cuando el [/CLR](../build/reference/clr-common-language-runtime-compilation.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **_MSC_BUILD** definido como un literal entero que contiene el elemento de número de revisión del número de versión del compilador. El número de revisión es el cuarto elemento el número de versión delimitado. Por ejemplo, si el número de versión del compilador de Visual C++ es 15.00.20706.01, la **_MSC_BUILD** (macro) se evalúa como 1. Siempre se define esta macro.  
  
-   **_MSC_EXTENSIONS** definido como 1 si el [/Ze (habilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) se establece la opción de compilador, que es el valor predeterminado. En caso contrario, es indefinido.  
  
-   **_MSC_FULL_VER** se define como un literal entero que codifica el principal, secundaria y generar el número de elementos del número de versión del compilador. El número principal es el primer elemento del número de versión delimitado, el número secundario es el segundo elemento y el número de compilación es el tercer elemento. Por ejemplo, si el número de versión del compilador de Visual C++ es 15.00.20706.01, la **_MSC_FULL_VER** (macro) se evalúa como 150020706. ¿Escriba **cl /?** en la línea de comandos para ver el número de versión del compilador. Siempre se define esta macro.  
  
-   **_MSC_VER** definido como un literal entero que codifica el número de elementos principal y secundario del número de versión del compilador. El número principal es el primer elemento del número de versión delimitado y el número secundario es el segundo elemento. Por ejemplo, si el número de versión del compilador de Visual C++ es 17.00.51106.1, la **_MSC_VER** (macro) se evalúa como 1700. ¿Escriba **cl /?** en la línea de comandos para ver el número de versión del compilador. Siempre se define esta macro.  
  
-   **_MSVC_LANG** definido como un literal de entero que especifica el estándar del lenguaje C++ dirigido por el compilador. Cuando se compila como C++, la macro es el valor literal de entero 201402 si la [/std:c ++ 14](../Topic/-std%20\(Specify%20Language%20Standard%20Version\).md) opción del compilador está establecido, o de forma predeterminada y es una mayor, no se especifica valor cuando la [/std:c ++ más reciente](../Topic/-std%20\(Specify%20Language%20Standard%20Version\).md) se establece la opción del compilador. De lo contrario, la macro es indefinida. El **_MSVC_LANG** macro y [/std (versión estándar lenguaje especificar)](../Topic/-std%20\(Specify%20Language%20Standard%20Version\).md) Opciones del compilador están disponibles a partir de Visual Studio 2015 Update 3.  
  
-   **__MSVC_RUNTIME_CHECKS** definido como 1 cuando uno de los [/RTC](../build/reference/rtc-run-time-error-checks.md) se establece opciones del compilador. En caso contrario, es indefinido.  
  
-   **_MT** definido como 1 cuando [/MD o /MDd](../build/reference/md-mt-ld-use-run-time-library.md) (DLL multiproceso) o [/MT o /MTd](../build/reference/md-mt-ld-use-run-time-library.md) especificado (multiproceso). En caso contrario, es indefinido.  
  
-   **_NATIVE_WCHAR_T_DEFINED** definido como 1 cuando el [/Zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **_OPENMP** definido como entero literal 200203, que representa la fecha de la especificación OpenMP implementada por Visual C++, si la [/openmp (habilitar la compatibilidad con OpenMP 2.0)](../build/reference/openmp-enable-openmp-2-0-support.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
    ```cpp  
    // _OPENMP_dir.cpp  
    // compile with: /openmp   
    #include <stdio.h>   
    int main() {  
       printf("%d\n", _OPENMP);  
    }  
    ```  
  
-   **_PREFAST\_** definido como 1 cuando el [/ analyze](../build/reference/analyze-code-analysis.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **__TIMESTAMP\_\_** definido como un literal de cadena que contiene la fecha y hora de la última modificación del archivo de origen actual, en forma abreviada, constante la longitud devuelta por la biblioteca de tiempo de ejecución de C [asctime](../c-runtime-library/reference/asctime-wasctime.md) funcione, por ejemplo, `Fri 19 Aug 13:32:58 2016`. Siempre se define esta macro.  
  
-   **_VC_NODEFAULTLIB** definido como 1 cuando la [/Zl (omitir nombre de biblioteca predeterminado)](../build/reference/zl-omit-default-library-name.md) se establece la opción del compilador. En caso contrario, es indefinido.  
  
-   **_WCHAR_T_DEFINED** definido como 1 cuando el valor predeterminado [/Zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) se establece la opción del compilador. El **_WCHAR_T_DEFINED** macro está definida, pero no tiene ningún valor si el **/Zc:wchar_t-** se establece la opción del compilador, y `wchar_t` se define en un archivo de encabezado del sistema incluido en el proyecto. En caso contrario, es indefinido.  
  
-   **_WIN32** definido como 1 cuando el destino de compilación es ARM de 32 bits, 64 bits ARM, x86, o x 64. En caso contrario, es indefinido.  
  
-   **_WIN64** se define como 1 cuando el destino de compilación es x64 o ARM de 64 bits. En caso contrario, es indefinido.  
  
-   **_WINRT_DLL** definido como 1 cuando se compila como C++ y ambos [/ZW (compilación en tiempo de ejecución de Windows)](../build/reference/zw-windows-runtime-compilation.md) y [/LD o /LDd](../build/reference/md-mt-ld-use-run-time-library.md) se establecen opciones del compilador. En caso contrario, es indefinido.  
  
 Macros de preprocesador que usa para determinar la versión de la biblioteca ATL o MFC no predefinidas por el compilador. Estas macros se definen en los encabezados de la biblioteca, por lo que no están definidos en las directivas de preprocesador antes de que se incluye el encabezado necesario.  
  
-   **_ATL_VER** definido en \< atldef.h > como un literal entero que codifica el número de versión ATL.  
  
-   **_MFC_VER** definido en \< afxver_.h > como un literal entero que codifica el número de versión MFC.  
  
## <a name="see-also"></a>Vea también  
 [Macros (C/C ++)](../preprocessor/macros-c-cpp.md)   
 [Operadores de preprocesador](../preprocessor/preprocessor-operators.md)   
 [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)