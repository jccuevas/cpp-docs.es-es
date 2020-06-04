---
title: Compatibilidad con los juegos de caracteres multibyte (MBCS)
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- multibyte characters [C++]
- MBCS [C++]
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
ms.openlocfilehash: 0b43168ec4331e99dea7e939b097674cc880804e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375761"
---
# <a name="support-for-multibyte-character-sets-mbcss"></a>Compatibilidad con los juegos de caracteres multibyte (MBCS)

Los juegos de caracteres multibyte (MBCS) son un enfoque anterior a la necesidad de admitir juegos de caracteres, como el japonés y el chino, que no pueden representarse en un solo byte. Si está realizando nuevo desarrollo, debe utilizar Unicode para todas las cadenas de texto, excepto quizás las cadenas del sistema que los usuarios finales no ven. MBCS es una tecnología heredada y no se recomienda para el nuevo desarrollo.

La implementación más habitual de MBCS son los juegos de caracteres de doble byte (DBCS). Visual C++ en general, y MFC en particular, están totalmente habilitados para DBCS.

Para obtener ejemplos, vea los archivos de código fuente de MFC.

Para las plataformas utilizadas en mercados cuyos idiomas utilizan juegos de caracteres de gran tamaño, la mejor alternativa a Unicode es MBCS. MFC admite MBCS mediante el uso de tipos de datos internacionalizables y funciones en tiempo de ejecución de C. Los programadores deben hacer lo mismo en su propio código.

En MBCS, los caracteres están codificados en uno o dos bytes. En los caracteres de dos bytes, el primero, o byte inicial, indica que él mismo y el byte siguiente deben interpretarse como un solo carácter. El primer byte procede de un intervalo de códigos reservado para su utilización como bytes iniciales. Los intervalos de bytes que pueden ser bytes iniciales dependen de la página de códigos que se utiliza. Por ejemplo, la página de códigos japonesa 932 utiliza el intervalo de 0x81 a 0x9F como bytes iniciales, pero la página de códigos coreana 949 utiliza un intervalo distinto.

Conviene tener en cuenta los siguientes aspectos en la programación con MBCS.

Los caracteres MBCS del entorno MBCS pueden aparecer en cadenas como nombres de archivo y directorio.

### <a name="editing-operations"></a>Operaciones de edición

Las operaciones de edición en aplicaciones MBCS se deben ejecutar en caracteres, no en bytes. El intercalador no debe dividir un carácter, la tecla **Flecha derecha** debe moverse a la derecha un carácter, y así sucesivamente. **Eliminar** debe eliminar un carácter; **Deshacer** debe reinsertarlo.

### <a name="string-handling"></a>Control de cadenas

En una aplicación que utiliza MBCS, el control de cadenas plantea problemas especiales. Los caracteres de ambos anchos se mezclan en una sola cadena; por consiguiente, no se debe olvidar de que hay que comprobar los bytes iniciales.

### <a name="run-time-library-support"></a>Compatibilidad con bibliotecas en tiempo de ejecución

MFC y la biblioteca en tiempo de ejecución de C admiten la programación de un solo byte, MBCS y Unicode. Las cadenas de un `str` solo byte se procesan con la familia de `_mbs` funciones en tiempo de `wcs` ejecución, las cadenas MBCS se procesan con las funciones correspondientes y las cadenas Unicode se procesan con las funciones correspondientes. Las implementaciones de funciones miembro de clase de MFC utilizan funciones en tiempo de ejecución portables, que se asignan bajo las circunstancias correctas a la familia `str` normal de funciones, las funciones MBCS o las funciones Unicode, como se describe en "Portabilidad de MBCS/Unicode".

### <a name="mbcsunicode-portability"></a>Portabilidad de MBCS/Unicode

Con el archivo de encabezado tchar.h, puede crear aplicaciones de un solo byte, MBCS y Unicode desde los mismos orígenes. Tchar.h define macros *_tcs* con el prefijo `str` `_mbs`_tcs `wcs` , que se asignan a , , o funciones, según corresponda. Para compilar MBCS, se ha de definir el símbolo `_MBCS`. Para crear Unicode, `_UNICODE`defina el símbolo . De forma predeterminada, `_UNICODE` está definido para aplicaciones MFC. Para obtener más información, consulte [Asignaciones de texto genérico en tchar.h](../text/generic-text-mappings-in-tchar-h.md).

> [!NOTE]
> El comportamiento es indefinido `_UNICODE` `_MBCS`si define ambos y .

Los archivos de encabezado Mbctype.h y Mbstring.h definen macros y funciones específicas de MBCS, que pueden ser necesarias en algunos casos. Por ejemplo, `_ismbblead` indica si un determinado byte de una cadena es un byte inicial.

Para la portabilidad internacional, codifique el programa con [Unicode](../text/support-for-unicode.md) o conjuntos de caracteres multibyte (MBCS).

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Habilitar MBCS en mi programa](../text/international-enabling.md)

- [Habilitar Unicode y MBCS en mi programa](../text/internationalization-strategies.md)

- [Utilizar MBCS para crear un programa internacionalizado](../text/mbcs-programming-tips.md)

- [Ver un resumen de programación con MBCS](../text/mbcs-programming-tips.md)

- [Obtener información sobre asignaciones de texto genérico para portabilidad de ancho de byte](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Consulte también

[Texto y cadenas](../text/text-and-strings-in-visual-cpp.md)<br/>
[Compatibilidad con MBCS en Visual C++](../text/mbcs-support-in-visual-cpp.md)
