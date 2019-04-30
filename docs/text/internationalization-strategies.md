---
title: Estrategias de internacionalización
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- language-portable code [C++]
- MBCS [C++], internationalization strategies
- Windows API [C++], international programming strategies
- Win32 [C++], international programming strategies
- Unicode [C++], globalizing applications
- character sets [C++], international programming strategies
- localization [C++], character sets
ms.assetid: b09d9854-0709-4b9a-a00c-b0b8bc4199b1
ms.openlocfilehash: f8c5cec680072ffa34b1ee0bef9e09231de5f1ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410634"
---
# <a name="internationalization-strategies"></a>Estrategias de internacionalización

Dependiendo de sus sistemas operativos de destino y mercados, tendrá varias estrategias de internacionalización:

- La aplicación usa Unicode.

   Se utiliza la funcionalidad específica de Unicode y todos los caracteres tienen un ancho de 16 bits (aunque puede utilizar caracteres ANSI en algunas partes del programa para fines especiales). La biblioteca de tiempo de ejecución de C proporciona funciones, macros y tipos de datos para la programación exclusivas de Unicode. MFC es totalmente compatible con Unicode.

- La aplicación utiliza MBCS y se puede ejecutar en cualquier plataforma de Win32.

   Use la funcionalidad específica de MBCS. Las cadenas pueden contener caracteres de byte único, los caracteres de doble byte o ambos. La biblioteca de tiempo de ejecución de C proporciona funciones, macros y tipos de datos para la programación solo MBCS. MFC está totalmente habilitado para MBCS.

- Se escribe el código fuente de la aplicación para la portabilidad completa, al volver a compilar con el símbolo `_UNICODE` o el símbolo `_MBCS` definido, puede generar versiones que usan alguno. Para obtener más información, consulte [asignaciones de texto genérico en tchar.h](../text/generic-text-mappings-in-tchar-h.md).

   Utilice totalmente portables tipos C para funciones, macros y datos de tiempo de ejecución. La flexibilidad de MFC es compatible con cualquiera de estas estrategias.

El resto de estos temas centrarse en escribir código totalmente portable que se pueden compilar como Unicode o MBCS.

## <a name="see-also"></a>Vea también

[Unicode y MBCS](../text/unicode-and-mbcs.md)<br/>
[Configuraciones regionales y páginas de códigos](../text/locales-and-code-pages.md)
