---
title: Restricciones de /clr
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], restrictions
ms.assetid: 385f6462-2c68-46d6-810e-469553ead447
ms.openlocfilehash: d0318ce2e23f92600d5a78d6472646ec91492152
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837374"
---
# <a name="clr-restrictions"></a>Restricciones de /clr

Tenga en cuenta las siguientes restricciones sobre el uso de **/clr**:

- En un controlador de excepciones estructurado, hay restricciones sobre el uso de `_alloca` cuando se compila con **/clr**. Para más información, vea [_alloca](../../c-runtime-library/reference/alloca.md).

- El uso de comprobaciones de errores en tiempo de ejecución no es válido con **/clr**. Para obtener más información, vea [Cómo: Uso de comprobaciones nativas en tiempo de ejecución](/visualstudio/debugger/how-to-use-native-run-time-checks).

- Cuando se usa **/clr** para compilar un programa que solo utiliza sintaxis de C++ estándar, se aplican estas directrices al uso de un ensamblado alineado:

  - Puede producirse un error en el código de ensamblado alineado que presupone conocer el diseño de pila nativo, las convenciones de llamada fuera de la función actual u otra información detallada sobre el equipo, si ese conocimiento se aplica al marco de pila para una función administrada. Las funciones que contienen código de ensamblado alineado se generan como funciones no administradas, como si se encontraran en un módulo independiente que se compiló sin **/clr**.

  - No se admite el código de ensamblado alineado en las funciones que pasan los parámetros de función construidos con copia.

- No se puede llamar a las [funciones vprintf](../../c-runtime-library/vprintf-functions.md) desde un programa compilado con **/clr**.

- El modificador [naked](../../cpp/naked-cpp.md) [__declspec](../../cpp/declspec.md) se omite en /clr.

- La función de traductor establecida por [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) afectará solo las capturas en código no administrado. Para más información, vea [Control de excepciones](../../extensions/exception-handling-cpp-component-extensions.md).

- No se permite la comparación de punteros de función en **/clr**.

- No se permite el uso de funciones que no se ajusten completamente al prototipo **/clr**.

- No se admiten en **/clr** las siguientes opciones del compilador:

  - **/EHsc** y **/EHs** ( **/clr** implica **/EHa** (vea [/EH (Modelo de control de excepciones)](eh-exception-handling-model.md))

  - **/fp:strict** y **/fp:except** (vea [/fp (Especificar comportamiento de punto flotante)](fp-specify-floating-point-behavior.md))

  - [/Zd](z7-zi-zi-debug-information-format.md)

  - [/Gm](gm-enable-minimal-rebuild.md)

  - [/MT](md-mt-ld-use-run-time-library.md)

  - [/RTC](rtc-run-time-error-checks.md)

  - [/ZI](z7-zi-zi-debug-information-format.md)

- No se admite la combinación de la definición del preprocesador `_STATIC_CPPLIB` (`/D_STATIC_CPPLIB`) y la opción del compilador **/clr**. Esto es así porque la definición haría que la aplicación se vinculara con la biblioteca de C++ Standard multiproceso, lo cual no se admite. Para más información, vea el tema [/MD, /MT, /LD (Utilizar la biblioteca en tiempo de ejecución)](md-mt-ld-use-run-time-library.md).

- Cuando se usa **/Zi** con **/clr**, hay implicaciones de rendimiento. Para más información, vea [/Zi](z7-zi-zi-debug-information-format.md).

- Si se pasa un carácter ancho a una rutina de salida de .NET Framework sin especificar también [/Zc:wchar_t](zc-wchar-t-wchar-t-is-native-type.md) o sin convertir el carácter a `__wchar_t`, hará que la salida aparezca como `unsigned short int`. Por ejemplo:

    ```cpp
    Console::WriteLine(L' ')              // Will output 32.
    Console::WriteLine((__wchar_t)L' ')   // Will output a space.
    ```

- [/GS](gs-buffer-security-check.md) se omite cuando se compila con **/clr**, a menos que una función se encuentre en `#pragma` [sin administrar](../../preprocessor/managed-unmanaged.md) o si la función se debe compilar en código nativo, en cuyo caso el compilador generará la advertencia C4793, que está desactivada de forma predeterminada.

- Vea [/ENTRY](entry-entry-point-symbol.md) para conocer los requisitos de firma de función de una aplicación administrada.

- Las aplicaciones compiladas con **/openmp** y **/clr** solo se pueden ejecutar en un único proceso de appdomain.  Para más información, vea [/openmp (Habilitar la compatibilidad con OpenMP 2.0)](openmp-enable-openmp-2-0-support.md).

- Las funciones que toman un número variable de argumentos (varargs) se generarán como funciones nativas. Cualquier tipo de datos administrados en la posición de argumento variable se serializará a tipos nativos. Tenga en cuenta que los tipos <xref:System.String?displayProperty=fullName> son realmente cadenas de caracteres anchos, pero se serializan a cadenas de caracteres de un solo byte. Por lo que si un especificador de printf es %S (wchar_t *), se serializará a una cadena %s en su lugar.

- Cuando se usa la macro va_arg, se pueden obtener resultados inesperados al compilar con **/clr:pure**. Para más información, vea [va_arg, va_copy, va_end, va_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). Las opciones del compilador **/clr:pure** y **/clr:safe** han quedado en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017 y versiones posteriores. El código que tenga que ser "puro" o "seguro" deberá portarse a C#.

- No debe llamar, desde el código administrado, a ninguna función que recorra la pila para obtener información de parámetros (argumentos de función); la capa de P/Invoke hace que la información se encuentre más abajo en la pila.  Por ejemplo, no compile proxy/código auxiliar con **/clr**.

- Las funciones se compilarán en código administrado siempre que sea posible, pero no todos los constructos de C++ se pueden traducir a código administrado.  Esta determinación se realiza función por función. Si no se puede convertir cualquier parte de una función a código administrado, la función completa se convertirá a código nativo. En los siguientes casos se impide que el compilador genere código administrado:

  - Códigos thunk generados por el compilador o funciones auxiliares. Los códigos thunk nativos se generan para cualquier llamada de función a través de un puntero de función, incluidas las llamadas de función virtuales.

  - Funciones que llaman a `setjmp` o `longjmp`.

  - Funciones que usan ciertas rutinas intrínsecas para manipular directamente los recursos del equipo. Por ejemplo, si se usa `__enable` y `__disable`, `_ReturnAddress` y `_AddressOfReturnAddress`, o elementos intrínsecos multimedia, todos darán como resultado código nativo.

  - Funciones que siguen la directiva `#pragma unmanaged`. (Tenga en cuenta que también se admite lo contrario, `#pragma managed`).

  - Una función que contiene referencias a tipos alineados, es decir, tipos declarados usando `__declspec(align(...))`.

## <a name="see-also"></a>Vea también

- [/clr (Compilación de Common Language Runtime)](clr-common-language-runtime-compilation.md)
