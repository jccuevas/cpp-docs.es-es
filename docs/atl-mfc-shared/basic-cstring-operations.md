---
title: Operaciones básicas de CString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 156191d09c88d8f19b3fe73108bcbca390b23f6e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760208"
---
# <a name="basic-cstring-operations"></a>Operaciones básicas de CString

Este tema explica en el siguiente basic [CString](../atl-mfc-shared/reference/cstringt-class.md) operaciones:

- [Creación de objetos CString de cadenas literales de C estándares](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [Obtener acceso a caracteres individuales en un objeto CString](#_core_accessing_individual_characters_in_a_cstring)

- [Cómo concatenar dos objetos CString](#_core_concatenating_two_cstring_objects)

- [Comparar objetos CString](#_core_comparing_cstring_objects)

- [Convertir objetos CString](#_core_converting_cstring_objects)

`Class CString` se basa en la plantilla de clase [clase CStringT](../atl-mfc-shared/reference/cstringt-class.md). `CString` es un **typedef** de `CStringT`. Más exactamente, `CString` es un **typedef** de un *especialización explícita* de `CStringT`, que es una forma habitual para usar una plantilla de clase para definir una clase. Son clases definidas de forma similar `CStringA` y `CStringW`.

`CString`, `CStringA`, y `CStringW` se definen en atlstr.h. `CStringT` se define en cstringt.h.

`CString`, `CStringA`, y `CStringW` cada obtener un conjunto de los métodos y operadores definidos por `CStringT` para su uso con los datos de cadena que admiten. Algunos de los métodos duplicados y, en algunos casos, superan los servicios de la cadena de las bibliotecas de tiempo de ejecución de C.

Nota: `CString` es una clase nativa. Para una clase de cadena que es para su uso en C / c++ / CLI administrado proyecto, use `System.String`.

##  <a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a> Creación de objetos CString de cadenas literales de C estándar

Puede asignar las cadenas literales de estilo C a un `CString` tal como se puede asignar uno `CString` objeto a otro.

- Asigne el valor de una cadena literal C a un `CString` objeto.

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- Asigne el valor de uno `CString` a otro `CString` objeto.

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   El contenido de un `CString` objeto se copian cuando uno `CString` objeto está asignado a otro. Por lo tanto, las dos cadenas no comparten una referencia a los caracteres reales que componen la cadena. Para obtener más información sobre cómo usar `CString` objetos como valores, vea [semántica de CString](../atl-mfc-shared/cstring-semantics.md).

   > [!NOTE]
   > Para escribir la aplicación para que pueda compilarse para Unicode o ANSI, las cadenas literales de código mediante el uso de la macro _T. Para obtener más información, consulte [juego de caracteres Multibyte (MBCS) compatibilidad con Unicode y](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

##  <a name="_core_accessing_individual_characters_in_a_cstring"></a> Obtener acceso a caracteres individuales en un objeto CString

Puede tener acceso a caracteres individuales de un `CString` objeto utilizando el `GetAt` y `SetAt` métodos. También puede usar el elemento o subíndice, operador de matriz ([]) en lugar de `GetAt` para obtener caracteres individuales. (Esto es similar a tener acceso a elementos de matriz por índice, como se muestra en las cadenas de estilo C estándares.) Para los valores de índice `CString` caracteres son de base cero.

##  <a name="_core_concatenating_two_cstring_objects"></a> Cómo concatenar dos objetos CString

Para concatenar dos `CString` objetos, utilice los operadores de concatenación (+ o +=), como sigue.

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

Al menos un argumento a los operadores de concatenación (+ o +=) debe ser un `CString` objeto, pero puede usar una cadena de constante de caracteres (por ejemplo, `"big"`) o un **char** (por ejemplo, ' x') para el otro argumento.

##  <a name="_core_comparing_cstring_objects"></a> Comparar objetos CString

El `Compare` método y el operador para == `CString` son equivalentes. `Compare`, **operador ==**, y `CompareNoCase` reconocen MBCS y Unicode; `CompareNoCase` también distingue mayúsculas de minúsculas. El `Collate` método `CString` es sensible a la configuración regional y a menudo es más lento que `Compare`. Use `Collate` sólo donde debe atenerse a la ordenación reglas especificadas por la configuración regional actual.

La siguiente tabla muestra los contadores [CString](../atl-mfc-shared/reference/cstringt-class.md) las funciones de comparación y sus funciones equivalentes en la biblioteca de tiempo de ejecución de C en portable de Unicode/MBCS.

|Función de CString|Función MBCS|Función de Unicode|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

El `CStringT` plantilla de clase define los operadores relacionales (<, \<=, > =, >, ==, y! =), que están disponibles para su uso por `CString`. Puede comparar dos `CStrings` mediante estos operadores, como se muestra en el ejemplo siguiente.

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

##  <a name="_core_converting_cstring_objects"></a> Convertir objetos CString

Para obtener información sobre cómo convertir objetos CString a otros tipos de cadena, vea [Cómo: convertir entre distintos tipos de cadenas](../text/how-to-convert-between-various-string-types.md).

## <a name="using-cstring-with-wcout"></a>Uso de CString con wcout

Para usar un objeto CString con `wcout` debe convertir explícitamente el objeto a un `const wchar_t*` tal como se muestra en el ejemplo siguiente:

```
CString cs("meow");

    wcout <<(const wchar_t*) cs <<endl;

```

Sin la conversión, `cs` se trata como un `void*` y `wcout` imprime la dirección del objeto. Este comportamiento se debe a sutiles interacciones entre argumento deducción y sobrecarga de resolución de plantilla que son por sí mismos correcta y compatible con el estándar de C++.

## <a name="see-also"></a>Vea también

[Cadenas (ATL y MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
[CStringT (clase)](../atl-mfc-shared/reference/cstringt-class.md)   
[Especialización de plantilla](../cpp/template-specialization-cpp.md)   
[Procedimiento para convertir entre distintos tipos de cadenas](../text/how-to-convert-between-various-string-types.md)

