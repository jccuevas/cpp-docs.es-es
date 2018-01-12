---
title: "Administración de datos de cadena | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords: Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad7a17b1b34375fcb45019bcaf8878757288a290
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="string-data-management"></a>Administración de datos de cadena
Visual C++ proporciona varias maneras de administrar los datos de cadena:  
  
-   [Manipulación de cadenas](../c-runtime-library/string-manipulation-crt.md) para trabajar con cadenas de estilo C terminada en null  
  
-   Funciones de la API de Win32 para la administración de cadenas  
  
-   La clase de MFC [clase CStringT](../atl-mfc-shared/reference/cstringt-class.md), que proporciona objetos de cadena flexible, puede cambiar el tamaño  
  
-   Clase [clase CStringT](../atl-mfc-shared/reference/cstringt-class.md), lo que proporciona un objeto de cadena independiente de MFC con la misma funcionalidad que`CString`  
  
 Casi todos los programas de trabajan con datos de cadena. MFC `CString` clase suele ser la mejor solución para control de cadenas flexibles. A partir de la versión 7.0, `CString` puede utilizarse en programas MFC o independientes de MFC. La biblioteca de tiempo de ejecución y `CString` admiten las cadenas que contienen caracteres multibyte de (extensa), como en la programación de Unicode o MBCS.  
  
 En este artículo se describe los servicios de uso generales que la biblioteca de clases proporciona relacionados con la manipulación de cadenas. Los temas tratados en este artículo son:  
  
-   [Unicode y MBCS proporcionan portabilidad](#_core_unicode_and_mbcs_provide_portability)  
  
-   [Objetos CString y punteros const char](#_core_cstrings_and_const_char_pointers)  
  
-   [Recuento de referencias de CString](#_core_cstring_reference_counting)  
  
 El [clase CStringT](../atl-mfc-shared/reference/cstringt-class.md) proporciona compatibilidad para manipular cadenas. Se pretende reemplazar y ampliar la funcionalidad que proporciona normalmente el paquete de cadena de biblioteca en tiempo de ejecución de C. La `CString` clase proporciona funciones miembro y operadores para gestionar cadena simplificada, similar a las que se encuentran en Basic. La clase también proporciona constructores y operadores para crear, asignar y comparar **objetos CString** y tipos de datos de cadena de C++ estándar. Dado que `CString` no se deriva de `CObject`, puede usar `CString` objetos independientemente de la mayor parte de la biblioteca de clases de Microsoft Foundation (MFC).  
  
 `CString`objetos siguen "semántica de valores". Un `CString` objeto representa un valor único. Piense en un `CString` como una cadena real, no como un puntero a una cadena.  
  
 Un `CString` objeto representa una secuencia de un número variable de caracteres. `CString`objetos pueden considerarse como matrices de caracteres.  
  
##  <a name="_core_unicode_and_mbcs_provide_portability"></a>Unicode y MBCS proporcionan portabilidad  
 MFC versión 3.0 y versiones posterior, MFC, incluyendo `CString`, está habilitada para Unicode y juegos de caracteres multibyte (MBCS). Esta compatibilidad facilita la escritura de aplicaciones portátiles que puede generar para los caracteres Unicode o ANSI. Para habilitar esta portabilidad, cada carácter de un `CString` objeto es de tipo **TCHAR**, que se define como `wchar_t` si define el símbolo **_UNICODE** al compilar la aplicación, o como `char` si no es así. Un `wchar_t` carácter ocupa 16 bits de ancho. MBCS está habilitado si se genera con el símbolo **_MBCS** definido. MFC se genera con cualquiera el **_MBCS** símbolos (para las bibliotecas NAFX) o la **_UNICODE** definida de símbolo (para las bibliotecas UAFX).  
  
> [!NOTE]
>  El `CString` ejemplos de esta y el que acompaña a artículos de cadenas se muestren las cadenas literales con el formato correcto para la portabilidad de Unicode, usando la **_T** macro, que convierte la cadena literal en el formulario:  
  
 `L"literal string"`  
  
> [!NOTE]
>  que el compilador trata como una cadena Unicode. Por ejemplo, el código siguiente:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]  
  
> [!NOTE]
>  se traduce como una cadena Unicode si **_UNICODE** está definido o como un ANSI de cadena si no es así. Para obtener más información, vea el artículo [con los juegos de caracteres Multibyte (MBCS) compatibilidad con Unicode y](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).  
  
 A `CString` objeto puede almacenar hasta **INT_MAX** (2.147.483.647) caracteres. El **TCHAR** tipo de datos se utiliza para obtener o establecer los caracteres individuales dentro de un `CString` objeto. A diferencia de las matrices de caracteres, la `CString` clase tiene una capacidad de asignación de memoria integrada. Esto permite `CString` objetos que se va a crecer automáticamente según sea necesario (es decir, no tiene que preocuparse de crecimiento un `CString` objeto para ajustarse a las cadenas más largas).  
  
##  <a name="_core_cstrings_and_const_char_pointers"></a>Objetos CString y punteros const char  
 A `CString` objeto también puede actuar como una cadena literal de estilo C (un `PCXSTR`, que es el mismo que **const char\***  if no se admite con Unicode). El [CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr) operador de conversión permite `CString` objetos libremente debe sustituir por punteros a caracteres en llamadas a funciones. El **CString (LPCWSTR** `pszSrc` **)** constructor permite punteros de caracteres que se sustituirá para `CString` objetos.  
  
 Se realiza ningún intento para plegarse `CString` objetos. Si realiza dos `CString` objetos que contiene `Chicago`, por ejemplo, los caracteres de `Chicago` se almacenan en dos lugares. (Esto puede no aplicarse de futuras versiones de MFC, por lo que no debe confiar en él.)  
  
> [!NOTE]
>  Use la [CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) y [CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) funciones miembro cuando necesite tener acceso directamente a un `CString` como un puntero no constante a un carácter.  
  
> [!NOTE]
>  Use la [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring) y [CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring) funciones de miembro para asignar y establecer `BSTR` objetos usados en automatización (antes conocida como automatización OLE).  
  
> [!NOTE]
>  Siempre que sea posible, asignar `CString` objetos en el marco en lugar de en el montón. Esto ahorra memoria y simplifica el paso de parámetros.  
  
 El `CString` clase no se implementa como una clase de colección de la biblioteca Microsoft Foundation Class, aunque `CString` por supuesto, se pueden almacenar objetos como elementos de colecciones.  
  
##  <a name="_core_cstring_reference_counting"></a>Recuento de referencias de CString  
 A partir de la versión 4.0 de MFC cuando [clase CStringT](../atl-mfc-shared/reference/cstringt-class.md) objetos se copian, MFC incrementa un recuento de referencias en lugar de copiar los datos. Esto hace que pasar parámetros por valor y devolver `CString` objetos por valor más eficaz. Estas operaciones hacen que el constructor de copias llamarlo, a veces más de una vez. Incrementa un recuento de referencias reduce la carga de ejecución para estas operaciones comunes y facilita el uso de `CString` una opción más atractiva.  
  
 Como cada copia se destruye, el recuento de referencias en el objeto original es reducido. La versión original `CString` objeto no se destruye hasta que su recuento de referencias se reduzca a cero.  
  
 Puede usar el `CString` funciones miembro [CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) y [CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) para deshabilitar o habilitar el recuento de referencias.  
  
## <a name="see-also"></a>Vea también  
 [Temas generales de MFC](../mfc/general-mfc-topics.md)

