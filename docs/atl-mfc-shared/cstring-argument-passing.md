---
title: Paso de argumentos de CString
ms.date: 11/04/2016
helpviewer_keywords:
- strings [C++], as function input/output
- argument passing [C++]
- arguments [C++], passing
- functions [C++], strings as input/output
- argument passing [C++], C strings
- passing arguments, C strings
- CString objects, passing arguments
- string arguments
ms.assetid: a67bebff-edf1-4cf4-bbff-d1cc6a901099
ms.openlocfilehash: 53977eb47520a20571a2d5ba8aa105c567ff40d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317930"
---
# <a name="cstring-argument-passing"></a>Paso de argumentos de CString

En este artículo se explica cómo pasar [CString](../atl-mfc-shared/reference/cstringt-class.md) objetos a funciones y cómo devolver `CString` objetos de funciones.

## <a name="cstring-argument-passing-conventions"></a><a name="_core_cstring_argument.2d.passing_conventions"></a>Convenciones CString Argument-Passing

Al definir una interfaz de clase, debe determinar la convención de paso de argumentos para las funciones miembro. Hay algunas reglas estándar para `CString` pasar y devolver objetos. Si sigue las reglas descritas en Cadenas como entradas de [función](#_core_strings_as_function_inputs) y cadenas como salidas de [función,](#_core_strings_as_function_outputs)tendrá código eficaz y correcto.

## <a name="strings-as-function-inputs"></a><a name="_core_strings_as_function_inputs"></a>Cadenas como entradas de función

La forma más eficaz y `CString` segura de utilizar un `CString` objeto en funciones llamadas es pasar un objeto a la función. A pesar del `CString` nombre, un objeto no almacena una cadena internamente como una cadena de estilo C que tiene un terminador nulo. En su `CString` lugar, un objeto realiza un seguimiento cuidadoso del número de caracteres que tiene. Tener `CString` un puntero LPCTSTR a una cadena terminada en null es una pequeña cantidad de trabajo que puede llegar a ser significativo si el código tiene que hacerlo constantemente. El resultado es temporal porque `CString` cualquier cambio en el contenido invalida las copias antiguas del puntero LPCTSTR.

En algunos casos, tiene sentido proporcionar una cadena de estilo C. Por ejemplo, puede haber una situación en la que una función llamada se escriba en C y no admita objetos. En este caso, coaccione el `CString` parámetro a LPCTSTR y la función obtendrá una cadena terminada en null de estilo C. También puede ir en la `CString` otra dirección `CString` y crear un objeto mediante el constructor que acepta un parámetro de cadena de estilo C.

Si una función va a cambiar el contenido de `CString` la`CString&`cadena, declare el parámetro como una referencia no constante ( ).

## <a name="strings-as-function-outputs"></a><a name="_core_strings_as_function_outputs"></a>Cadenas como salidas de función

Normalmente se `CString` pueden devolver `CString` objetos de funciones porque los objetos siguen la semántica de valores como los tipos primitivos. Para devolver una cadena de solo `CString` lectura, utilice una referencia constante (`const CString&`). En el ejemplo siguiente `CString` se muestra el uso de parámetros y tipos de valor devuelto:

[!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]

## <a name="see-also"></a>Consulte también

[Cadenas (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
