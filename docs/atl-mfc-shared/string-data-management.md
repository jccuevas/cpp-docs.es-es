---
title: Administración de datos de cadena
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: 7f92b38ac659faef2dd9319b2f204ba837f0d473
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317461"
---
# <a name="string-data-management"></a>Administración de datos de cadena

Visual C++ proporciona varias formas de administrar los datos de cadena:

- [Manipulación](../c-runtime-library/string-manipulation-crt.md) de cadenas para trabajar con cadenas terminadas en null de estilo C

- Funciones de api de Win32 para administrar cadenas

- [Clase CStringT de](../atl-mfc-shared/reference/cstringt-class.md)MFC, que proporciona objetos de cadena flexibles y redimensionables

- Clase [CStringT (Clase)](../atl-mfc-shared/reference/cstringt-class.md), que proporciona un objeto de cadena independiente de MFC con la misma funcionalidad que`CString`

Casi todos los programas funcionan con datos de cadena. La clase `CString` de MFC suele ser la mejor solución para el control flexible de cadenas. A partir de la `CString` versión 7.0, se puede utilizar en programas independientes de MFC o MFC. Tanto la biblioteca en `CString` tiempo de ejecución como las cadenas de soporte que contienen caracteres multibyte (anchos), como en la programación Unicode o MBCS.

En este artículo se describen los servicios de uso general que proporciona la biblioteca de clases relacionados con la manipulación de cadenas. Los temas tratados en este artículo incluyen:

- [Unicode y MBCS Proporcionan portabilidad](#_core_unicode_and_mbcs_provide_portability)

- [CStrings y const char Punteros](#_core_cstrings_and_const_char_pointers)

- [Recuento de referencias de CString](#_core_cstring_reference_counting)

La clase [CStringT](../atl-mfc-shared/reference/cstringt-class.md) proporciona compatibilidad para manipular cadenas. Está diseñado para reemplazar y ampliar la funcionalidad normalmente proporcionada por el paquete de cadenas de biblioteca en tiempo de ejecución de C. La `CString` clase proporciona funciones miembro y operadores para el control simplificado de cadenas, similar a los que se encuentran en Basic. La clase también proporciona constructores y operadores para `CString`construir, asignar y comparar tipos de datos de cadena s y C++ estándar. Dado `CString` que no `CObject`se deriva `CString` de , puede usar objetos independientemente de la mayoría de la biblioteca de clases de Microsoft Foundation (MFC).

`CString`los objetos siguen la "semántica del valor". Un `CString` objeto representa un valor único. Piense en `CString` una cadena real, no como un puntero a una cadena.

Un `CString` objeto representa una secuencia de un número variable de caracteres. `CString`objetos se pueden considerar como matrices de caracteres.

## <a name="unicode-and-mbcs-provide-portability"></a><a name="_core_unicode_and_mbcs_provide_portability"></a>Unicode y MBCS proporcionan portabilidad

Con MFC versión 3.0 y `CString`versiones posteriores, MFC, incluido , está habilitado para Unicode y conjuntos de caracteres multibyte (MBCS). Esta compatibilidad facilita la escritura de aplicaciones portátiles que se pueden compilar para caracteres Unicode o ANSI. Para habilitar esta portabilidad, `CString` cada carácter de un objeto `wchar_t` es de tipo TCHAR, que se `char` define como si definiera el símbolo _UNICODE al compilar la aplicación, o como si no. Un `wchar_t` carácter tiene 16 bits de ancho. MBCS está habilitado si se compila con el símbolo _MBCS define. MFC se compila con el símbolo de _MBCS (para las bibliotecas NAFX) o el símbolo de _UNICODE (para las bibliotecas UAFX) definido.

> [!NOTE]
> Los `CString` ejemplos de esto y los artículos adjuntos en cadenas muestran cadenas literales correctamente formateadas para la portabilidad Unicode, utilizando la macro _T, que traduce la cadena literal al formulario:

`L"literal string"`

> [!NOTE]
> que el compilador trata como una cadena Unicode. Por ejemplo, el código siguiente:

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
> se traduce como una cadena Unicode si _UNICODE está definido o como una cadena ANSI si no. Para obtener más información, consulte el artículo Compatibilidad con conjuntos de [caracteres Unicode y multibyte (MBCS).](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

Un `CString` objeto puede almacenar hasta INT_MAX (2.147.483.647) caracteres. El tipo de datos TCHAR se utiliza `CString` para obtener o establecer caracteres individuales dentro de un objeto. A diferencia de `CString` las matrices de caracteres, la clase tiene una capacidad de asignación de memoria integrada. Esto `CString` permite que los objetos crezcan automáticamente según sea `CString` necesario (es decir, no tiene que preocuparse por cultivar un objeto para que se ajuste a cadenas más largas).

## <a name="cstrings-and-const-char-pointers"></a><a name="_core_cstrings_and_const_char_pointers"></a>CStrings y const char Punteros

Un `CString` objeto también puede actuar como una `PCXSTR`cadena literal de estilo C (una , que es lo mismo que **const char** <strong>\*</strong> si no está en Unicode). El operador de conversión [PcXSTR CSimpleStringT::operator](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) permite `CString` que los objetos se sustituyan libremente por punteros de caracteres en llamadas de función. El **CString( LPCWSTR** `pszSrc` **)** constructor permite que `CString` los punteros de caracteres se sustituyan por objetos.

No se intenta `CString` plegar objetos. Si realiza `CString` dos `Chicago`objetos que contienen `Chicago` , por ejemplo, los caracteres en se almacenan en dos lugares. (Esto puede no ser cierto para las versiones futuras de MFC, por lo que no debe depender de él.)

> [!NOTE]
> Utilice las funciones miembro [CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) y [CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) cuando necesite tener acceso directamente a `CString` un puntero no constante a un carácter.

> [!NOTE]
> Utilice las funciones miembro [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) y [CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) para asignar y establecer objetos BSTR utilizados en Automation (anteriormente conocido como automatización OLE).

> [!NOTE]
> Siempre que `CString` sea posible, asigne objetos en el marco en lugar de en el montón. Esto ahorra memoria y simplifica el paso de parámetros.

La `CString` clase no se implementa como una clase `CString` de colección Microsoft Foundation Class Library, aunque los objetos sin duda se pueden almacenar como elementos en colecciones.

## <a name="cstring-reference-counting"></a><a name="_core_cstring_reference_counting"></a>Recuento de referencias de CString

A partir de la versión 4.0 de MFC, cuando se copian objetos de [clase CStringT,](../atl-mfc-shared/reference/cstringt-class.md) MFC incrementa un recuento de referencias en lugar de copiar los datos. Esto hace que pasar parámetros por valor y devolver `CString` objetos por valor sea más eficaz. Estas operaciones hacen que se llame al constructor de copias, a veces más de una vez. El incremento de un recuento de referencias reduce `CString` esa sobrecarga para estas operaciones comunes y hace que el uso de una opción sea más atractiva.

A medida que se destruye cada copia, se reduce el recuento de referencias en el objeto original. El `CString` objeto original no se destruye hasta que su recuento de referencias se reduce a cero.

Puede usar `CString` las funciones miembro [CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) y [CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) para deshabilitar o habilitar el recuento de referencias.

## <a name="see-also"></a>Consulte también

[Temas generales de MFC](../mfc/general-mfc-topics.md)
