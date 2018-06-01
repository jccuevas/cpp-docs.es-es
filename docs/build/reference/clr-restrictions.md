---
title: restricciones de /CLR | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34d21939f51fc3d4800d5cdd887b283b7e690db6
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704274"
---
# <a name="clr-restrictions"></a>Restricciones de /clr

Tenga en cuenta las siguientes restricciones en el uso de **/CLR**:

- En un controlador de excepciones estructurado, hay restricciones sobre el uso de `_alloca` cuando se compila con **/CLR**. Para obtener más información, consulte [_alloca](../../c-runtime-library/reference/alloca.md).

- El uso de comprobaciones de errores en tiempo de ejecución no es válido con **/CLR**. Para más información, vea [Cómo: Utilizar comprobaciones nativas en tiempo de ejecución](/visualstudio/debugger/how-to-use-native-run-time-checks).

- Cuando **/CLR** es utilizar para compilar un programa que solo utiliza sintaxis estándar de C++, las siguientes directrices se aplican al uso de ensamblado en línea:

  - Código de ensamblado alineado que supone un conocimiento del diseño de pila nativo, convenciones de llamada fuera de la función actual u otra información de bajo nivel sobre el equipo pueden fallar si dichos conocimientos se aplican al marco de pila para una función administrada. Las funciones que contienen código ensamblador en línea se generan como funciones no administradas, como si se encontraran en un módulo independiente que se compiló sin **/CLR**.

  - No se admite el código de ensamblado alineado en funciones que pasan parámetros de función construidos de copia.

- El [vprintf (funciones)](../../c-runtime-library/vprintf-functions.md) no se puede llamar desde un programa compilado con **/CLR**.

- El [naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) modificador se omite en/CLR.

- Establece la función de traductor [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) afectará solo capturas en código no administrado. Vea [Exception Handling](../../windows/exception-handling-cpp-component-extensions.md) para obtener más información.

- La comparación de punteros a función no está permitida en **/CLR**.

- No se permite el uso de funciones que no se ajusten completamente al prototipo en **/CLR**.

- Las opciones del compilador siguientes no son compatibles con **/CLR**:

  - **/ /EHsc** y **/EHs** (**/CLR** implica **/EHa** (consulte [/EH (modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md))

  - **/ fp: strict** y **/fp: excepto** (consulte [/fp (Especificar comportamiento de punto flotante)](../../build/reference/fp-specify-floating-point-behavior.md))

  - [/Zd](../../build/reference/z7-zi-zi-debug-information-format.md)

  - [/Gm](../../build/reference/gm-enable-minimal-rebuild.md)

  - [/MT](../../build/reference/md-mt-ld-use-run-time-library.md)

  - [/RTC](../../build/reference/rtc-run-time-error-checks.md)

  - [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)

- La combinación de la `_STATIC_CPPLIB` definición del preprocesador (`/D_STATIC_CPPLIB`) y la **/CLR** no se admite la opción del compilador. Esto es así porque la definición haría que su aplicación vincular con la estática multiproceso biblioteca estándar de C++, que no es compatible. Para obtener más información, consulte el [/MD, / MT, /LD (utilizar la biblioteca en tiempo de ejecución)](../../build/reference/md-mt-ld-use-run-time-library.md) tema.

- Cuando se usa **/Zi** con **/CLR**, hay implicaciones de rendimiento. Para obtener más información, consulte [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).

- Pasa un carácter ancho a un marco .NET de salida rutina sin también especificar [/Zc: wchar_t](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) o sin convertir el carácter a `__wchar_t` hará que la salida para que aparezca como un `unsigned short int`. Por ejemplo:

    ```cpp
    Console::WriteLine(L' ')              // Will output 32.
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.
    ```

- [/GS](../../build/reference/gs-buffer-security-check.md) se omite cuando se compila con **/CLR**, a menos que una función está por debajo del `#pragma` [no administrado](../../preprocessor/managed-unmanaged.md) o si la función se debe compilar en código nativo, en cuyo caso el compilador generará advertencia C4793, que está desactivada de forma predeterminada.

- Vea [/Entry](../../build/reference/entry-entry-point-symbol.md) para los requisitos de firma de función de una aplicación administrada.

- Las aplicaciones compiladas con **/OpenMP** y **/CLR** sólo se puede ejecutar en un proceso simple de appdomain.  Vea [/openmp (habilitar la compatibilidad con OpenMP 2.0)](../../build/reference/openmp-enable-openmp-2-0-support.md) para obtener más información.

- Las funciones que toman un número variable de argumentos (varargs) se generará como funciones nativas. Los tipos de datos administrados en la posición del argumento variable se pueden calcular las referencias a tipos nativos. Tenga en cuenta que <xref:System.String?displayProperty=fullName> tipos son cadenas de caracteres anchos realmente, pero se calculan las referencias a cadenas de caracteres de un solo byte. Por lo que si un especificador de printf es %S (wchar_t *), calculará las referencias a una cadena %s en su lugar.

- Cuando se utiliza la macro va_arg, puede obtener resultados inesperados cuando se compila con **/CLR: pure**. Para obtener más información, consulte [va_arg, va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017. El código que debe ser "pura" o "segura" se debe pasar a C#.

- No debe llamar, desde el código administrado, las funciones que recorrer la pila para obtener información sobre los parámetros (argumentos de función;) la capa de P/Invoke hace que la información sea más abajo en la pila.  Por ejemplo, no compile proxy/código auxiliar con **/CLR**.

- Las funciones se compilarán a código administrado siempre que sea posible, pero no todas las construcciones de C++ se pueden traducir a código administrado.  Esta determinación se realiza según una función por función. Si no se puede convertir cualquier parte de una función a código administrado, toda la función se convertirá a código nativo. Los casos siguientes evitan que el compilador genere código administrado.

  - Fragmentos de código thunk generado por el compilador o funciones auxiliares. Thunks nativos se generan para cualquier llamada de función a través de un puntero a función, incluidas las llamadas de función virtual.

  - Funciones que llaman a `setjmp` o `longjmp`.

  - Funciones que utilizan ciertas rutinas intrínsecas para manipular directamente los recursos del equipo. Por ejemplo, el uso de `__enable` y `__disable`, `_ReturnAddress` y `_AddressOfReturnAddress`, o intrínsecas multimedia que todos los resultados en código nativo.

  - Las funciones que sigue el `#pragma unmanaged` directiva. (Tenga en cuenta que el inverso, `#pragma managed`, también es compatible.)

  - Una función que contenga referencias a alineado tipos, es decir, tipos declaran mediante `__declspec(align(...))`.

## <a name="see-also"></a>Vea también

- [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)
