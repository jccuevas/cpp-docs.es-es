---
title: Operaciones básicas de CString
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
ms.openlocfilehash: 68947dc37e5398ac7caa4754e9af40223cec7bf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317958"
---
# <a name="basic-cstring-operations"></a>Operaciones básicas de CString

En este tema se explican las siguientes operaciones básicas de [CString:](../atl-mfc-shared/reference/cstringt-class.md)

- [Creación de objetos CString a partir de cadenas literales Estándar de C](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [Acceso a caracteres individuales en un CString](#_core_accessing_individual_characters_in_a_cstring)

- [Concatenación de dos CString objetos](#_core_concatenating_two_cstring_objects)

- [Comparación de CString objetos](#_core_comparing_cstring_objects)

- [Conversión de CString objetos](#_core_converting_cstring_objects)

`Class CString`se basa en la plantilla de clase [CStringT (clase).](../atl-mfc-shared/reference/cstringt-class.md) `CString`es un **typedef** de `CStringT`. Más `CString` exactamente, es una **definición** de tipo de una *especialización explícita* de `CStringT`, que es una forma común de usar una plantilla de clase para definir una clase. Las clases `CStringA` `CStringW`definidas de forma similar son y .

`CString`, `CStringA`, `CStringW` y se definen en atlstr.h. `CStringT`se define en cstringt.h.

`CString`, `CStringA`, `CStringW` y cada uno obtiene un `CStringT` conjunto de los métodos y operadores definidos por para su uso con los datos de cadena que admiten. Algunos de los métodos duplican y, en algunos casos, superan los servicios de cadena de las bibliotecas en tiempo de ejecución de C.

Nota: `CString` es una clase nativa. Para una clase de cadena que se va a utilizar `System.String`en un proyecto administrado de C++/CLI, utilice .

## <a name="creating-cstring-objects-from-standard-c-literal-strings"></a><a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a>Creación de objetos CString a partir de cadenas literales C estándar

Puede asignar cadenas literales de `CString` estilo C a `CString` un mismo como puede asignar un objeto a otro.

- Asigne el valor de una `CString` cadena literal de C a un objeto.

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- Asigne el valor `CString` de `CString` uno a otro objeto.

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   El contenido `CString` de un objeto `CString` se copia cuando se asigna un objeto a otro. Por lo tanto, las dos cadenas no comparten una referencia a los caracteres reales que componen la cadena. Para obtener más información `CString` sobre cómo utilizar objetos como valores, vea [CString Semantics](../atl-mfc-shared/cstring-semantics.md).

   > [!NOTE]
   > Para escribir la aplicación para que se pueda compilar para Unicode o para ANSI, cadenas literales de código mediante la macro _T. Para obtener más información, vea Compatibilidad con unicode y conjuntos de caracteres [multibyte (MBCS).](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

## <a name="accessing-individual-characters-in-a-cstring"></a><a name="_core_accessing_individual_characters_in_a_cstring"></a>Acceso a personajes individuales en un CString

Puede tener acceso a `CString` caracteres `GetAt` individuales en un objeto mediante los métodos y. `SetAt` También puede utilizar el elemento de matriz, o subíndice, operador ( [ ] ) en lugar de `GetAt` obtener caracteres individuales. (Esto se asemeja al acceso a los elementos de matriz por índice, como en las cadenas de estilo C estándar.) Los valores `CString` de índice de los caracteres se basan en cero.

## <a name="concatenating-two-cstring-objects"></a><a name="_core_concatenating_two_cstring_objects"></a>Concatenación de dos objetos CString

Para concatenar `CString` dos objetos, utilice los operadores de concatenación (+ o + ), como se indica a continuación.

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

Al menos un argumento para los operadores de concatenación (+ o + ) debe ser un `CString` objeto, pero puede usar una cadena de caracteres constantes (por ejemplo, `"big"`) o un **char** (por ejemplo, 'x') para el otro argumento.

## <a name="comparing-cstring-objects"></a><a name="_core_comparing_cstring_objects"></a>Comparación de objetos CString

El `Compare` método y el `CString` operador para el operador de la lista son equivalentes. `Compare`, **operador**, `CompareNoCase` y son compatibles con MBCS y Unicode; `CompareNoCase` también no distingue mayúsculas de minúsculas. El `Collate` método `CString` de es sensible a la `Compare`configuración regional y a menudo es más lento que . Utilice `Collate` solo cuando deba cumplir las reglas de ordenación especificadas por la configuración regional actual.

En la tabla siguiente se muestran las funciones de comparación [de CString](../atl-mfc-shared/reference/cstringt-class.md) disponibles y sus funciones portátiles Unicode/MBCS equivalentes en la biblioteca en tiempo de ejecución de C.

|Función CString|Función MBCS|Función Unicode|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

La `CStringT` plantilla de clase define \<los operadores relacionales (<, , >, >, `CString`, y !, que están disponibles para su uso por . Puede comparar `CStrings` dos utilizando estos operadores, como se muestra en el ejemplo siguiente.

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

## <a name="converting-cstring-objects"></a><a name="_core_converting_cstring_objects"></a>Conversión de objetos CString

Para obtener información acerca de cómo convertir CString objetos a otros tipos de cadena, vea [Cómo: convertir entre varios tipos](../text/how-to-convert-between-various-string-types.md)de cadena .

## <a name="using-cstring-with-wcout"></a>Uso de CString con wcout

Para usar un `wcout` CString con usted debe `const wchar_t*` convertir explícitamente el objeto a un como se muestra en el ejemplo siguiente:

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

Sin la `cs` conversión, `void*` `wcout` se trata como a e imprime la dirección del objeto. Este comportamiento es causado por interacciones sutiles entre la deducción de argumentos de plantilla y la resolución de sobrecarga que son en sí mismas correctas y conformes con el estándar C++.

## <a name="see-also"></a>Consulte también

[Cadenas (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Clase CStringT](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Especialización de plantillas](../cpp/template-specialization-cpp.md)<br/>
[Cómo: Convertir entre distintos tipos de cadenas](../text/how-to-convert-between-various-string-types.md)
