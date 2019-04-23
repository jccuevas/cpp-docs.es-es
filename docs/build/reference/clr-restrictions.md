---
title: Restricciones de /clr
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
ms.openlocfilehash: 21b7ead553871854c73021756eb2086f9e6e7393
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58777823"
---
# <a name="clr-restrictions"></a>Restricciones de /clr

Tenga en cuenta las siguientes restricciones sobre el uso de **/CLR**:

- En un controlador de excepciones estructurado, hay restricciones sobre el uso de `_alloca` cuando se compila con **/CLR**. Para obtener más información, consulte [_alloca](../../c-runtime-library/reference/alloca.md).

- El uso de comprobaciones de errores en tiempo de ejecución no es válido con **/CLR**. Para obtener más información, vea [Cómo: Uso de comprobaciones nativas en tiempo de ejecución](/visualstudio/debugger/how-to-use-native-run-time-checks).

- Cuando **/CLR** es utilizada para compilar un programa que solo utiliza sintaxis estándar de C++, las siguientes directrices se aplican al uso de un ensamblado alineado:

  - Código de ensamblado alineado que supone un conocimiento del diseño de pila nativo, convenciones de llamada fuera de la función actual u otra información de bajo nivel sobre el equipo pueden fallar si se aplica el conocimiento en el marco de pila para una función administrada. Las funciones que contienen código ensamblador en línea se generan como funciones no administradas, como si se encontraran en un módulo independiente que se compiló sin **/CLR**.

  - No se admite el código de ensamblado alineado en las funciones que pasan los parámetros de función construidos de copia.

- El [vprintf (funciones)](../../c-runtime-library/vprintf-functions.md) no pueden llamarse desde un programa compilado con **/CLR**.

- El [naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) se omite el modificador en/CLR.

- Establece la función de traductor [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) afectará solo las capturas en código no administrado. Consulte [Exception Handling](../../extensions/exception-handling-cpp-component-extensions.md) para obtener más información.

- No se permite la comparación de punteros a función **/CLR**.

- No se permite el uso de funciones que no se ajusten completamente al prototipo **/CLR**.

- No se admiten las siguientes opciones del compilador con **/CLR**:

  - **/ EHsc** y **/EHs** (**/CLR** implica **/EHa** (consulte [/EH (modelo de control de excepciones)](eh-exception-handling-model.md))

  - **/ fp: strict** y **/fp: excepto** (consulte [/fp (Especificar comportamiento de punto flotante)](fp-specify-floating-point-behavior.md))

  - [/Zd](z7-zi-zi-debug-information-format.md)

  - [/Gm](gm-enable-minimal-rebuild.md)

  - [/MT](md-mt-ld-use-run-time-library.md)

  - [/RTC](rtc-run-time-error-checks.md)

  - [/ZI](z7-zi-zi-debug-information-format.md)

- La combinación de la `_STATIC_CPPLIB` definición del preprocesador (`/D_STATIC_CPPLIB`) y el **/CLR** no se admite la opción del compilador. Esto es porque la definición haría que la aplicación para vincular con estática multiproceso biblioteca estándar de C++, que no se admite. Para obtener más información, consulte el [/MD, / MT, /LD (utilizar la biblioteca de tiempo de ejecución)](md-mt-ld-use-run-time-library.md) tema.

- Cuando se usa **/Zi** con **/CLR**, hay implicaciones de rendimiento. Para obtener más información, consulte [/Zi](z7-zi-zi-debug-information-format.md).

- Pasa un carácter ancho a .NET Framework de rutina de salida sin también especificar [/Zc:](zc-wchar-t-wchar-t-is-native-type.md) o sin convertir el carácter a `__wchar_t` hará que la salida aparezca como un `unsigned short int`. Por ejemplo:

    ```cpp
    Console::WriteLine(L' ')              // Will output 32.
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.
    ```

- [/GS](gs-buffer-security-check.md) se omite cuando se compila con **/CLR**, a menos que una función se encuentra en `#pragma` [no administrado](../../preprocessor/managed-unmanaged.md) o si la función se debe compilar en código nativo, en cuyo caso el compilador generará advertencia C4793, que está desactivada de forma predeterminada.

- Consulte [/Entry](entry-entry-point-symbol.md) para conocer los requisitos de firma de función de una aplicación administrada.

- Las aplicaciones compiladas con **/OpenMP** y **/CLR** solo se pueden ejecutar en un proceso simple de appdomain.  Consulte [/openmp (habilitar la compatibilidad con OpenMP 2.0)](openmp-enable-openmp-2-0-support.md) para obtener más información.

- Las funciones que toman un número variable de argumentos (varargs) se generarán como funciones nativas. Para tipos nativos se calculan las referencias de los tipos de datos administrados en la posición del argumento variable. Tenga en cuenta que <xref:System.String?displayProperty=fullName> tipos son cadenas de caracteres anchos realmente, pero que se serializan las cadenas de caracteres de byte único. Por lo que si un especificador de printf es %S (wchar_t *), calcula las referencias a una cadena %s en su lugar.

- Cuando se usa la macro va_arg, puede obtener resultados inesperados cuando se compila con **/CLR: pure**. Para obtener más información, consulte [va_arg, va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017. Código que debe ser "pura" o "segura" se debe pasar a C#.

- No debe llamar, desde el código administrado, todas las funciones que recorrer la pila para obtener información de parámetros (argumentos de función;) la capa de P/Invoke hace que la información sea más abajo en la pila.  Por ejemplo, no se compilan proxy/código auxiliar con **/CLR**.

- Las funciones se compilarán a código administrado siempre que sea posible, pero no todas las construcciones de C++ se pueden traducir a código administrado.  Esta determinación se realiza en la función por función. Si no se puede convertir cualquier parte de una función a código administrado, toda la función se convertirán en código nativo. Los siguientes casos, evitar que el compilador genere código administrado.

  - Fragmentos de código thunk generado por el compilador o funciones auxiliares. Thunks nativos se generan para cualquier llamada de función a través de un puntero a función, incluidas las llamadas de función virtual.

  - Funciones que llaman a `setjmp` o `longjmp`.

  - Funciones que utilizan ciertas rutinas intrínsecas para manipular directamente los recursos del equipo. Por ejemplo, el uso de `__enable` y `__disable`, `_ReturnAddress` y `_AddressOfReturnAddress`, o intrínsecas multimedia que todos los resultados en código nativo.

  - Las funciones que sigue el `#pragma unmanaged` directiva. (Tenga en cuenta que el inverso, `#pragma managed`, también es compatible.)

  - Una función que contiene referencias a alineado tipos, es decir, los tipos se declaran mediante `__declspec(align(...))`.

## <a name="see-also"></a>Vea también

- [/clr (Compilación de Common Language Runtime)](clr-common-language-runtime-compilation.md)
