---
title: Administración de datos de cadena
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: b247e97f5aa6b5e85a6a6b6f57a64224a9e0f435
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747182"
---
# <a name="string-data-management"></a>Administración de datos de cadena

Visual C++ proporciona varias maneras de administrar los datos de cadena:

- [Manipulación de cadenas](../c-runtime-library/string-manipulation-crt.md) para trabajar con cadenas de estilo C terminada en null

- Funciones de la API de Win32 para la administración de cadenas

- La clase de MFC [clase CStringT](../atl-mfc-shared/reference/cstringt-class.md), que proporciona objetos de cadena flexible, puede cambiar el tamaño

- Clase [clase CStringT](../atl-mfc-shared/reference/cstringt-class.md), lo que proporciona un objeto de cadena independiente de MFC con la misma funcionalidad que `CString`

Casi todos los programas trabajan con datos de cadena. MFC `CString` clase suele ser la mejor solución para control de cadenas flexibles. Comenzando con la versión 7.0, `CString` puede usarse en programas MFC o independientes de MFC. Tanto la biblioteca en tiempo de ejecución y `CString` admiten cadenas de caracteres multibyte de (anchos), como se muestra en la programación de Unicode o MBCS.

En este artículo se describe los servicios de uso general que la biblioteca de clases proporciona relacionados con la manipulación de cadenas. Los temas tratados en este artículo incluyen:

- [Unicode y MBCS proporcionan portabilidad](#_core_unicode_and_mbcs_provide_portability)

- [Objetos CString y punteros const char](#_core_cstrings_and_const_char_pointers)

- [Recuento de referencias de CString](#_core_cstring_reference_counting)

El [clase CStringT](../atl-mfc-shared/reference/cstringt-class.md) proporciona compatibilidad para manipular cadenas. Se pretende reemplazar y ampliar la funcionalidad que proporciona el paquete de cadena de biblioteca en tiempo de ejecución de C con normalidad. La `CString` clase proporciona funciones miembro y operadores para el tratamiento de cadena simplificada, similar a las que se encuentran en Basic. La clase también proporciona constructores y operadores para crear, asignar y comparar `CString`s y estándar de C++ de los tipos de datos de cadena. Dado que `CString` no se deriva `CObject`, puede usar `CString` objetos independientemente de la mayoría de la biblioteca de clases de Microsoft Foundation (MFC).

`CString` los objetos siguen la "semántica de valores". Un `CString` objeto representa un valor único. Puede considerar un `CString` como una cadena real, no como un puntero a una cadena.

Un `CString` objeto representa una secuencia de un número variable de caracteres. `CString` los objetos pueden considerarse como matrices de caracteres.

##  <a name="_core_unicode_and_mbcs_provide_portability"></a> Unicode y MBCS proporcionan portabilidad

Con MFC versión 3.0 y versiones posterior, MFC, incluido `CString`, está habilitada para Unicode y juegos de caracteres multibyte (MBCS). Esta compatibilidad facilita la escritura de aplicaciones portátiles que puede generar para los caracteres Unicode o ANSI. Para habilitar esta portabilidad, cada carácter de un `CString` objeto es de tipo TCHAR, que se define como `wchar_t` si define el símbolo _UNICODE al compilar la aplicación, o como `char` si no es así. Un `wchar_t` es de carácter ancho de 16 bits. MBCS se habilita si se compila con el símbolo _MBCS definido. MFC se ha creado con el símbolo _MBCS (para las bibliotecas NAFX) o se ha definido el símbolo _UNICODE (para las bibliotecas UAFX).

> [!NOTE]
>  El `CString` ejemplos de este y los artículos que lo acompaña sobre las cadenas de mostrar las cadenas literales que tiene el formato correcto para la portabilidad de Unicode, mediante la macro _T, que convierte la cadena literal en el formulario:

`L"literal string"`

> [!NOTE]
>  que el compilador trata como una cadena Unicode. Por ejemplo, el código siguiente:

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
>  se traduce como una cadena Unicode si se define _UNICODE o como una cadena ANSI si no lo es. Para obtener más información, vea el artículo [juego de caracteres Multibyte (MBCS) compatibilidad con Unicode y](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

Un `CString` objeto puede almacenar hasta caracteres INT_MAX (2.147.483.647). El tipo de datos TCHAR se utiliza para obtener o establecer los caracteres individuales dentro de un `CString` objeto. A diferencia de las matrices de caracteres, el `CString` clase tiene una funcionalidad de asignación de memoria integrada. Esto permite `CString` objetos que se va a crecer automáticamente según sea necesario (es decir, que no tiene que preocuparse sobre el crecimiento de un `CString` objeto para ajustarse a las cadenas más largas).

##  <a name="_core_cstrings_and_const_char_pointers"></a> Objetos CString y punteros const char

Un `CString` objeto también puede actuar como una cadena literal de estilo C (una `PCXSTR`, que es el mismo que **const char** <strong>\*</strong> if no bajo Unicode). El [CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) permite el operador de conversión `CString` objetos que se sustituirá libremente para punteros de caracteres en las llamadas de función. El **CString (LPCWSTR** `pszSrc` **)** constructor permite punteros de caracteres que se sustituirá para `CString` objetos.

Se realiza ningún intento plegar `CString` objetos. Si realiza dos `CString` que contiene los objetos `Chicago`, por ejemplo, los caracteres de `Chicago` se almacenan en dos lugares. (Esto puede no ser cierto de futuras versiones de MFC, por lo que debe no dependen de él.)

> [!NOTE]
>  Use la [CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) y [CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) funciones miembro cuando necesite tener acceso directamente a un `CString` como un puntero a un carácter no constante.

> [!NOTE]
>  Use la [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) y [CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) funciones miembro para asignar y establecer objetos BSTR utilizados en automatización (antes conocida como automatización OLE).

> [!NOTE]
>  Siempre que sea posible, asignar `CString` objetos en el marco en lugar de en el montón. Esto ahorra memoria y simplifica el paso de parámetros.

El `CString` clase no se implementa como una clase de colección de la biblioteca Microsoft Foundation Class, aunque `CString` ciertamente pueden almacenarse como elementos en colecciones de objetos.

##  <a name="_core_cstring_reference_counting"></a> Recuento de referencias de CString

A partir de la versión 4.0, MFC cuando [clase CStringT](../atl-mfc-shared/reference/cstringt-class.md) se copian los objetos, MFC incrementa un recuento de referencias en lugar de copiar los datos. Esto hace que pasar parámetros por valor y devolver `CString` objetos por valor más eficaz. Estas operaciones hacen que el constructor de copias llamarlo, a veces más de una vez. Incrementa un recuento de referencias reduce la carga de ejecución para estas operaciones comunes y facilitan el uso de `CString` una opción más atractiva.

Como cada copia se destruye, el recuento de referencias en el objeto original es reducido. La versión original `CString` objeto no se destruye hasta que su recuento de referencias se reduce a cero.

Puede usar el `CString` funciones miembro [CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) y [CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) para deshabilitar o habilitar un recuento de referencias.

## <a name="see-also"></a>Vea también

[Temas generales de MFC](../mfc/general-mfc-topics.md)
