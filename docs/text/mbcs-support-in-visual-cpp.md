---
title: Compatibilidad con MBCS en Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- tools [C++], MBCS support
- Asian languages [C++]
- Code Editor [C++], MBCS support
- IME [C++]
- Chinese characters [C++]
- Input Method Editor [C++], MBCS
- resource editors [C++], MBCS support
- debugger [C++], MBCS support
- character sets [C++], multibyte
- Japanese characters [C++]
- multibyte characters [C++]
- Kanji character support [C++]
- NMAKE program, MBCS support
- double-byte character sets [C++]
- IME [C++], MBCS
- Input Method Editor [C++]
- MBCS [C++], enabling
ms.assetid: 6179f6b7-bc61-4a48-9267-fb7951223e38
ms.openlocfilehash: b5f2b6dd56d3a755ee73058c024152e12157a6bd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501947"
---
# <a name="mbcs-support-in-visual-c"></a>Compatibilidad con MBCS en Visual C++

Cuando se ejecuta en una versión habilitada para MBCS de Windows, C++ el sistema de desarrollo visual (incluido el editor de código fuente integrado, el depurador y las herramientas de línea de comandos) está habilitado para MBCS, con la excepción de la ventana memoria.

La ventana memoria no interpreta bytes de datos como caracteres MBCS, aunque puede interpretarlos como caracteres ANSI o Unicode. Los caracteres ANSI siempre tienen un tamaño de 1 byte y los caracteres Unicode tienen un tamaño de 2 bytes. Con MBCS, los caracteres pueden tener un tamaño de 1 o 2 bytes, y su interpretación depende de la página de códigos que esté en uso. Por este motivo, es difícil que la ventana memoria muestre caracteres MBCS de forma confiable. La ventana memoria no puede saber qué byte es el inicio de un carácter. El desarrollador puede ver los valores de byte en la ventana memoria y buscar el valor en las tablas para determinar la representación de caracteres. Esto es posible porque el desarrollador conoce la dirección de inicio de una cadena basada en el código fuente.

Visual C++ acepta caracteres de doble byte siempre que sea adecuado hacerlo. Esto incluye los nombres de ruta de acceso y los nombres de archivo en los cuadros C++ de diálogo y entradas de texto en el editor de recursos visuales (por ejemplo, texto estático en el editor de cuadros de diálogo y entradas de texto estático en el editor de iconos). Además, el preprocesador reconoce algunas directivas de doble byte (por ejemplo, nombres de archivo en `#include` instrucciones y como argumentos de las `code_seg` pragmas y `data_seg` ). En el editor de código fuente, se aceptan caracteres de doble byte en comentarios y literales de cadena, aunque no enC++ elementos de C/Language (como los nombres de variable).

##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>Compatibilidad con el editor de métodos de entrada (IME)

Las aplicaciones escritas para los mercados de Asia oriental que usan MBCS (por ejemplo, Japón) suelen admitir el IME de Windows para escribir caracteres de un solo byte y de doble byte. El entorno C++ de desarrollo visual contiene compatibilidad total con el IME.

Los teclados japoneses no admiten directamente caracteres kanji. El IME convierte una cadena fonética, que se escribe en uno de los otros alfabetos japoneses (romaji, Katakana o Hiragana) en sus posibles representaciones kanji. Si hay ambigüedad, puede seleccionar entre varias alternativas. Cuando ha seleccionado el carácter kanji previsto, el IME pasa dos `WM_CHAR` mensajes a la aplicación de control.

El IME, activado por la combinación de\` teclas Alt +, aparece como un conjunto de botones (un indicador) y una ventana de conversión. La aplicación coloca la ventana en el punto de inserción de texto. La aplicación debe controlar `WM_MOVE` los `WM_SIZE` mensajes y cambiando la posición de la ventana de conversión para ajustarse a la nueva ubicación o tamaño de la ventana de destino.

Si desea que los usuarios de la aplicación tengan la posibilidad de escribir caracteres kanji, la aplicación debe controlar los mensajes de Windows IME. Para obtener más información acerca de la programación con IME, consulte [Administrador de métodos de entrada](/windows/win32/intl/input-method-manager).

## <a name="visual-c-debugger"></a>Depurador visual C++

El depurador visual C++ proporciona la capacidad de establecer puntos de interrupción en mensajes de IME. Además, la ventana memoria puede mostrar caracteres de doble byte.

## <a name="command-line-tools"></a>Herramientas de línea de comandos

Las herramientas C++ de línea de comandos visual, incluido el compilador, NMAKE y el compilador de recursos (RC. EXE), están habilitados para MBCS. Puede usar la opción/c del compilador de recursos para cambiar la página de códigos predeterminada al compilar los recursos de la aplicación.

Para cambiar la configuración regional predeterminada en tiempo de compilación del código fuente, use [#pragma setlocale](../preprocessor/setlocale.md).

## <a name="graphical-tools"></a>Herramientas gráficas

Las herramientas C++ basadas en Windows de Visual, como Spy + + y las herramientas de edición de recursos, admiten totalmente cadenas de IME.

## <a name="see-also"></a>Vea también

[Compatibilidad con los juegos de caracteres multibyte (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)
