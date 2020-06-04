---
title: Operaciones de CString relacionadas con cadenas de estilo C
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, basic operations
- MFC [C++], string handling class
- string conversion [C++], C-style strings
- strings [C++], string operations
- standard run-time library string functions
- null values, Null-terminated string conversion
- string functions
- strings [C++], in C
- string arguments
- C-style strings
- strings [C++], class CString
- casting CString objects
ms.assetid: 5048de8a-5298-4891-b8a0-c554b5a3ac1b
ms.openlocfilehash: 406a934d3691c7787085cc319770074ac2ee5926
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317942"
---
# <a name="cstring-operations-relating-to-c-style-strings"></a>Operaciones de CString relacionadas con cadenas de estilo C

Un [CString](../atl-mfc-shared/using-cstring.md) objeto contiene datos de cadena de caracteres. `CString`hereda el conjunto de los [métodos y operadores](../atl-mfc-shared/reference/cstringt-class.md) que se definen en la plantilla de clase [CStringT](../atl-mfc-shared/reference/cstringt-class.md) para trabajar con datos de cadena. (`CString` es una **typedef** que se especializa para trabajar con el tipo de datos de caracteres `CStringT` que `CString` admite.)

`CString` no almacena datos de caracteres internamente como una cadena terminada en un valor nulo de estilo C. En su lugar, `CString` realiza un seguimiento de la longitud de los datos de caracteres para, así, poder vigilar los datos y el espacio que precisan de forma más segura.

Con todo, `CString` acepta cadenas de estilo C y ofrece formas de acceder a los datos de caracteres como una cadena de estilo C. Este tema está compuesto por las siguientes secciones, donde se explica cómo usar un objeto `CString` como si fuera una cadena terminada en un valor nulo de estilo C.

- [Conversión a cadenas terminadas en un valor nulo de estilo C](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)

- [Uso de funciones de cadena de biblioteca en tiempo de ejecución estándar](#_core_working_with_standard_run.2d.time_library_string_functions)

- [Modificación directa del contenido de CString](#_core_modifying_cstring_contents_directly)

- [Uso de objetos CString con funciones de argumento variable](#_core_using_cstring_objects_with_variable_argument_functions)

- [Especificación de parámetros formales de CString](#_core_specifying_cstring_formal_parameters)

## <a name="using-cstring-as-a-c-style-null-terminated-string"></a><a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a>Uso de CString como una cadena terminada en null de estilo C

Para utilizar `CString` un objeto como una cadena de estilo C, convierta el objeto en LPCTSTR. En el siguiente ejemplo, `CString` devuelve un puntero a una cadena terminada en un valor nulo de estilo C de solo lectura. La función `strcpy` coloca una copia de esa cadena de estilo C en la variable `myString`.

```cpp
CString aCString = "A string";
char myString[256];
strcpy(myString, (LPCTSTR)aCString);
```

Puede usar métodos de `CString` (`SetAt`, por ejemplo) para modificar caracteres concretos del objeto de cadena. Sin embargo, el puntero LPCTSTR es temporal y `CString`deja de ser válido cuando se realiza cualquier cambio en . `CString` también puede quedar fuera de su ámbito y eliminarse automáticamente. Se recomienda obtener un nuevo puntero LPCTSTR de un `CString` objeto cada vez que utilice uno.

Habrá veces en las que necesite una copia de los datos de `CString` para modificarlos directamente. Use la función más protegida `strcpy_s` (o la función portable de Unicode/MBCS `_tcscpy_s`) para copiar el objeto `CString` en otro búfer. Ahí, los caracteres se podrán modificar con menor riesgo, como verá en este ejemplo.

[!code-cpp[NVC_ATLMFC_Utilities#189](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_1.cpp)]

> [!NOTE]
> El tercer `strcpy_s` argumento (o Unicode/MBCS-portable) `_tcscpy_s` `const wchar_t*` es un (Unicode) o un `const char*` (ANSI). En el ejemplo anterior se pasa un `CString` para este argumento. El compilador de C++ emplea automáticamente la función de conversión definida para la clase `CString`, que convierte un `CString` en un `LPCTSTR`. La posibilidad de definir operaciones de conversión de un tipo a otro es una de las características más útiles de C++.

## <a name="working-with-standard-run-time-library-string-functions"></a><a name="_core_working_with_standard_run.2d.time_library_string_functions"></a>Trabajar con funciones de cadena de biblioteca en tiempo de ejecución estándar

Debe poder encontrar un método de `CString` para realizar cualquier operación de cadena en la que puedan usarse funciones de cadena de biblioteca en tiempo de ejecución estándar, como `strcmp` (o la función portable de Unicode/MBCS `_tcscmp`).

Si debe utilizar las funciones de cadena en tiempo de ejecución de C, puede utilizar las técnicas descritas en _core_using_cstring_as_a_c.2d.style_null.2d.terminated_string. Puede copiar el objeto `CString` en un búfer de cadena de estilo C equivalente, llevar a cabo las operaciones que correspondan en dicho búfer y, luego, asignar la cadena de estilo C resultante de vuelta a un objeto `CString`.

## <a name="modifying-cstring-contents-directly"></a><a name="_core_modifying_cstring_contents_directly"></a>Modificación directa del contenido de CString

La mayoría de las veces, conviene usar las funciones miembro de `CString` para modificar el contenido de un objeto `CString` o para convertir `CString` en una cadena de caracteres de estilo C.

Existen algunas situaciones en las que sí tiene sentido modificar el contenido de `CString` directamente (por ejemplo, al trabajar con funciones de sistema operativo que requieren un búfer de caracteres).

Los métodos `GetBuffer` y `ReleaseBuffer` dan acceso al búfer de caracteres interno de un objeto `CString`, donde podrá modificarlo directamente. En los siguientes pasos se explica cómo usar estas funciones con este fin.

### <a name="to-use-getbuffer-and-releasebuffer-to-access-the-internal-character-buffer-of-a-cstring-object"></a>Para usar GetBuffer y ReleaseBuffer para acceder al búfer de caracteres interno de un objeto CString

1. Llame a `GetBuffer` en relación con un objeto `CString` e indique la longitud de búfer que necesita.

1. Use el puntero que `GetBuffer` devuelve para escribir caracteres directamente en el objeto `CString`.

1. Llame a `ReleaseBuffer` en relación con el objeto `CString` para actualizar toda la información de estado de `CString` interna (por ejemplo, la longitud de la cadena). Tras modificar el contenido de un objeto `CString` directamente, debe llamar a `ReleaseBuffer` antes de llamar a cualquier otra función miembro de `CString`.

## <a name="using-cstring-objects-with-variable-argument-functions"></a><a name="_core_using_cstring_objects_with_variable_argument_functions"></a>Uso de objetos CString con funciones de argumento variable

Algunas funciones de C toman un número variable de argumentos. Un ejemplo significativo de esto es `printf_s`. Debido al modo en que esta función se declara, el compilador no puede saber con seguridad de qué tipo son los argumentos ni distinguir qué operación de conversión debe realizar en cada argumento. Por lo tanto, es fundamental usar una conversión de tipo explícita al pasar un objeto `CString` a una función que toma un número variable de argumentos.

Para utilizar `CString` un objeto en una función `CString` de argumento de variable, convierta explícitamente la cadena LPCTSTR, como se muestra en el ejemplo siguiente.

[!code-cpp[NVC_ATLMFC_Utilities#190](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_2.cpp)]

## <a name="specifying-cstring-formal-parameters"></a><a name="_core_specifying_cstring_formal_parameters"></a>Especificación de parámetros formales de CString

En la mayoría de las funciones que necesitan un argumento de cadena, lo mejor es especificar el parámetro formal en el prototipo de la función como un puntero `const` a un carácter (`LPCTSTR`), y no un `CString`. Cuando se especifica un parámetro `const` formal como un puntero a un carácter, puede pasar`"hi there"`un puntero `CString` a una matriz TCHAR, una cadena literal [ ] o un objeto. El `CString` objeto se convertirá automáticamente en un LPCTSTR. En cualquier lugar en el que pueda utilizar `CString` un LPCTSTR, también puede utilizar un objeto.

También puede especificar un parámetro formal como una `const CString&`referencia de cadena constante (es decir, ) si el argumento no se modificará. Suelte el modificador **const** si la función modificará la cadena. Si se pretende obtener un valor nulo predeterminado, inicialícelo en la cadena null [`""`], como se muestra aquí:

[!code-cpp[NVC_ATLMFC_Utilities#191](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_3.cpp)]

Para la mayoría de los resultados de función, se puede devolver simplemente un objeto `CString` por valor.

## <a name="see-also"></a>Consulte también

[Cadenas (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CString Argument Passing](../atl-mfc-shared/cstring-argument-passing.md)
