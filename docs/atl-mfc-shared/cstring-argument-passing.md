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
ms.openlocfilehash: 1729167786d71c107fe6a4369d5a0c7e7c8594f1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236390"
---
# <a name="cstring-argument-passing"></a>Paso de argumentos de CString

En este artículo se explica cómo pasar [CString](../atl-mfc-shared/reference/cstringt-class.md) a las funciones y cómo se devuelven los objetos `CString` objetos desde funciones.

##  <a name="_core_cstring_argument.2d.passing_conventions"></a> Convenciones de paso de argumentos de CString

Cuando se define una interfaz de clase, debe determinar la convención para pasar argumentos para las funciones de miembro. Hay algunas reglas estándares para pasar y devolver `CString` objetos. Si sigue las reglas descritas en [cadenas como entradas de la función](#_core_strings_as_function_inputs) y [cadenas como salida de la función](#_core_strings_as_function_outputs), tendrá código eficaz y correcto.

##  <a name="_core_strings_as_function_inputs"></a> Cadenas como entradas de la función

Una manera más eficaz y segura utilizar un `CString` objeto en las funciones llamadas consiste en pasar un `CString` objeto a la función. A pesar del nombre, un `CString` objeto no almacena una cadena internamente como una cadena de estilo C que tiene un terminador null. En su lugar, un `CString` objeto realiza el seguimiento de una cuidadosa del número de caracteres tiene. Tener `CString` proporciona un puntero LPCTSTR en una cadena terminada en null es una pequeña cantidad de trabajo que puede ser considerable si el código tiene que hacerlo constantemente. El resultado es temporal porque cualquier cambio en el `CString` contenido invalida copias antiguas del puntero con LPCTSTR.

Tiene sentido en algunos casos, para proporcionar una cadena de estilo C. Por ejemplo, puede haber una situación donde una función llamada está escrita en C y no admite objetos. En este caso, forzar el `CString` parámetro LPCTSTR y la función obtendrá una cadena de estilo C terminada en null. También puede ir a la otra dirección y crear un `CString` objeto utilizando el `CString` constructor que acepta un parámetro de cadena de estilo C.

Si el contenido de la cadena se va a cambiarse por una función, declare el parámetro como una que no es constante `CString` referencia (`CString&`).

##  <a name="_core_strings_as_function_outputs"></a> Cadenas como salida de la función

Normalmente, puede devolver `CString` objetos de funciones porque `CString` objetos siguen la semántica de valores como tipos primitivos. Para devolver una cadena de solo lectura, utilice una constante `CString` referencia (`const CString&`). El ejemplo siguiente muestra el uso de `CString` parámetros y tipos de valor devuelto:

[!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/cpp/cstring-argument-passing_2.cpp)]

## <a name="see-also"></a>Vea también

[Cadenas (ATL y MFC)](../atl-mfc-shared/strings-atl-mfc.md)
