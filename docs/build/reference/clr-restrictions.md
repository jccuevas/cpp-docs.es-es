---
title: "Restricciones de /clr | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr (opción del compilador) [C++], restricciones"
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
caps.latest.revision: 27
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Restricciones de /clr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Deben tenerse en cuenta las siguientes restricciones de uso de **\/clr**:  
  
-   En un controlador de excepciones estructurado, hay restricciones en el uso de `_alloca` al compilar con **\/clr**.  Para obtener más información, vea [\_alloca](../../c-runtime-library/reference/alloca.md).  
  
-   El uso de comprobaciones de errores en tiempo de ejecución no es válido con **\/clr**.  Para obtener más información, vea [Comprobaciones de errores en tiempo de ejecución](../Topic/How%20to:%20Use%20Native%20Run-Time%20Checks.md).  
  
-   Cuando se utiliza **\/clr** para compilar un programa que sólo utiliza la sintaxis de C\+\+ estándar, son de aplicación las instrucciones siguientes para el uso de ensamblado en línea:  
  
    -   El código de ensamblado en línea que asuma conocimientos del diseño de pila nativo, convenciones de llamada externas a la función actual u otra información de bajo nivel acerca del equipo, puede fallar si dichos conocimientos se aplican al marco de pila de una función administrada.  Las funciones que contienen código de ensamblado en línea se generan como funciones no administradas, como si se encontraran en un módulo independiente compilado sin **\/clr**.  
  
    -   No se admite el código de ensamblado en línea en las funciones que pasan parámetros de función construidos en copias.  
  
-   No se puede llamar a [funciones vprintf](../../c-runtime-library/vprintf-functions.md) desde un programa compilado con **\/clr**.  
  
-   El modificador [naked](../../cpp/naked-cpp.md) [\_\_declspec](../../cpp/declspec.md) no se tiene en cuenta bajo \/clr.  
  
-   La función de traductor definida por [\_set\_se\_translator](../../c-runtime-library/reference/set-se-translator.md) sólo afecta a capturas del código no administrado.  Para obtener más información, vea [Control de excepciones](../../windows/exception-handling-cpp-component-extensions.md).  
  
-   La comparación de punteros a función no está permitida bajo **\/clr**.  
  
-   El uso de funciones sin prototipos bien definidos no está permitido bajo **\/clr**.  
  
-   Las opciones del compilador siguientes no se admiten con **\/clr**:  
  
    -   **\/EHsc** y **\/EHs** \(**\/clr** implica **\/EHa** \(vea [\/EH \(Modelo de control de excepciones\)](../../build/reference/eh-exception-handling-model.md)\)\)  
  
    -   **\/fp:strict** y **\/fp:except** \(vea [\/fp \(Especificar comportamiento de punto flotante\)](../../build/reference/fp-specify-floating-point-behavior.md)\)  
  
    -   [\/Zd](../../build/reference/z7-zi-zi-debug-information-format.md)  
  
    -   [\/Gm](../../build/reference/gm-enable-minimal-rebuild.md)  
  
    -   [\/MT](../../build/reference/md-mt-ld-use-run-time-library.md)  
  
    -   [\/RTC](../../build/reference/rtc-run-time-error-checks.md)  
  
    -   **\/ZI**  
  
-   No se admite la combinación de la definición del preprocesador `_STATIC_CPPLIB` \(`/D_STATIC_CPPLIB`\) y la opción del compilador **\/clr** o **\/clr:pure**.  Esto es así porque la definición haría que su aplicación se vinculara con la Biblioteca estándar de C\+\+ de multiproceso estático, lo cual no se admite.  Para obtener más información, vea el tema [\/MD, \/MT, \/LD \(Utilizar la biblioteca en tiempo de ejecución\)](../../build/reference/md-mt-ld-use-run-time-library.md).  
  
-   [\/J](../../build/reference/j-default-char-type-is-unsigned.md) no se admite con **\/clr:safe** o **\/clr:pure**.  
  
-   Las bibliotecas ATL y MFC no son compatibles con la compilación en modo puro \(**\/clr:pure**\).  Puede utilizar **\/clr:pure** con la Biblioteca estándar de C\+\+ y el CRT si también compila con **\/MD** o **\/MDd**.  
  
-   Si se utiliza **\/Zi** con **\/clr**, afecta al rendimiento.  Para obtener más información, vea [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
-   Si se pasa un carácter ancho a una rutina de resultados de .NET Framework sin especificar [\/Zc:wchar\_t](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) o sin convertir el carácter a `__wchar_t`, el resultado será un `unsigned short int`.  Por ejemplo:  
  
    ```  
    Console::WriteLine(L' ')              // Will output 32.  
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.  
    ```  
  
-   [\/GS](../../build/reference/gs-buffer-security-check.md) no se tiene en cuenta si se compila con **\/clr**, salvo que exista una función bajo `#pragma` [unmanaged](../../preprocessor/managed-unmanaged.md) o que la función deba compilarse en versión nativa, en cuyo caso el compilador genera la advertencia C4793, que de forma predeterminada está desactivada.  
  
-   Vea [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) para conocer los requisitos para firmas de funciones de una aplicación administrada.  
  
-   Las aplicaciones compiladas con **\/openmp** y **\/clr** sólo se pueden ejecutar en un proceso simple de AppDomain.  Para obtener más información, vea [\/openmp \(Habilitar la compatibilidad con OpenMP 2.0\)](../../build/reference/openmp-enable-openmp-2-0-support.md).  
  
-   Las funciones que utilizan un número variable de argumentos \(varargs\) se generarán como funciones nativas.  Se calcularán las referencias de cualesquiera tipos de datos administrados situados en la posición de argumento variable como tipos nativos.  Observe que los tipos <xref:System.String?displayProperty=fullName> son en realidad cadenas de caracteres anchos, pero se calculan las referencias a cadenas de caracteres de un solo byte.  Por tanto, si un especificador de printf es %S \(wchar\_t\*\), se calculará las referencias a una cadena %s.  
  
-   Si se utiliza la macro va\_arg, podrían obtenerse resultados inesperados al compilar con **\/clr:pure**.  Para obtener más información, vea [va\_arg, va\_copy, va\_end, va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md).  
  
-   Si la aplicación pasa un argumento de tipo [va\_list](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) a una función declarada para aceptar un [número variable de argumentos](../../misc/variable-argument-lists.md), y la aplicación se ha compilado con **\/clr:pure**, CLR produce una excepción <xref:System.NotSupportedException>.  Si se utiliza **\/clr**  en su lugar, las características afectadas se compilan en código nativo y se ejecutan correctamente.  Si se utiliza **\/clr:safe**, se emite un diagnóstico del error.  
  
-   Desde código administrado, no se deben efectuar llamadas a funciones que recorren la pila para obtener información de parámetros \(argumentos de funciones\). La capa P\/Invoke hace que la información esté más abajo en la pila.  Por ejemplo, no compile proxy\/stub con **\/clr**.  
  
-   Las funciones se compilarán a código administrado siempre que sea posible, pero no todas las construcciones de C\+\+ se pueden traducir a código administrado.  Esta determinación se realiza para cada función independientemente.  Si alguna parte de una función no se puede convertir a código administrado, entonces toda la función se convertirá a código nativo.  Los casos siguientes evitan que el compilador genere código administrado.  
  
    -   Thunks generados por el compilador o funciones auxiliares.  Los thunks nativos se generan para cualquier llamada a función a través de un puntero a función, incluso las llamadas a funciones virtuales.  
  
    -   Funciones que llaman a `setjmp` o `longjmp`.  
  
    -   Funciones que utilizan ciertas rutinas intrínsecas para manipular directamente recursos del equipo.  Por ejemplo, el uso de `__enable` y `__disable`, `_ReturnAddress` y `_AddressOfReturnAddress` o intrínsecas multimedia producirá código nativo.  
  
    -   Funciones que siguen la directiva `#pragma unmanaged`. \(Observe que también se admite la inversa, `#pragma managed`\).  
  
    -   Una función que contiene referencias a tipos alineados, es decir, tipos declarados mediante `__declspec(align(...))`.  
  
-   No se pueden utilizar las clases [Compatibilidad con COM del compilador](../../cpp/compiler-com-support.md) con **\/clr:pure** o **\/clr:safe**.  
  
## Vea también  
 [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md)