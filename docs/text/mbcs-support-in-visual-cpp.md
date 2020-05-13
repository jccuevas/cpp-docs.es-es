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
ms.openlocfilehash: 404fcee5e48d8db28e56a005f24f8cac5892240e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375793"
---
# <a name="mbcs-support-in-visual-c"></a>Compatibilidad con MBCS en Visual C++

Cuando se ejecuta en una versión de Windows habilitada para MBCS, el sistema de desarrollo de Visual C++ (incluido el editor de código fuente integrado, el depurador y las herramientas de línea de comandos) está habilitado para MBCS, con la excepción de la ventana de memoria.

La ventana de memoria no interpreta bytes de datos como caracteres MBCS, aunque puede interpretarlos como caracteres ANSI o Unicode. Los caracteres ANSI siempre tienen un tamaño de 1 byte y los caracteres Unicode tienen un tamaño de 2 bytes. Con MBCS, los caracteres pueden tener un tamaño de 1 o 2 bytes y su interpretación depende de la página de códigos que esté en uso. Debido a esto, es difícil para la ventana de memoria mostrar de forma fiable caracteres MBCS. La ventana de memoria no puede saber qué byte es el inicio de un carácter. El desarrollador puede ver los valores de bytes en la ventana de memoria y buscar el valor en las tablas para determinar la representación de caracteres. Esto es posible porque el desarrollador conoce la dirección inicial de una cadena basada en el código fuente.

Visual C++ acepta caracteres de doble byte siempre que sea apropiado hacerlo. Esto incluye nombres de ruta de acceso y nombres de archivo en cuadros de diálogo y entradas de texto en el editor de recursos de Visual C++ (por ejemplo, texto estático en el editor de cuadros de diálogo y entradas de texto estático en el editor de iconos). Además, el preprocesador reconoce algunas directivas de doble `#include` byte, por ejemplo, `code_seg` nombres `data_seg` de archivo en instrucciones y como argumentos para pragmas. En el editor de código fuente, se aceptan caracteres de doble byte en comentarios y literales de cadena, aunque no en elementos de lenguaje C/C++ (como nombres de variables).

## <a name="support-for-the-input-method-editor-ime"></a><a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>Compatibilidad con el Editor de métodos de entrada (IME)

Las aplicaciones escritas para mercados de Asia oriental que utilizan MBCS (por ejemplo, Japón) normalmente admiten el IME de Windows para introducir caracteres de un solo byte y de doble byte. El entorno de desarrollo de Visual C++ contiene compatibilidad completa con el IME.

Los teclados japoneses no admiten directamente caracteres Kanji. El IME convierte una cadena fonética, introducida en uno de los otros alfabetos japoneses (Romaji, Katakana o Hiragana) en sus posibles representaciones Kanji. Si hay ambiguedad, puede seleccionar entre varias alternativas. Cuando haya seleccionado el carácter Kanji deseado, `WM_CHAR` el IME pasa dos mensajes a la aplicación controladora.

El IME, activado por\` la combinación de teclas ALT+, aparece como un conjunto de botones (un indicador) y una ventana de conversión. La aplicación coloca la ventana en el punto de inserción de texto. La aplicación `WM_MOVE` debe `WM_SIZE` controlar y los mensajes cambiando la posición de la ventana de conversión para que se ajuste a la nueva ubicación o tamaño de la ventana de destino.

Si desea que los usuarios de la aplicación tengan la capacidad de escribir caracteres Kanji, la aplicación debe controlar los mensajes IME de Windows. Para obtener más información acerca de la programación IME, consulte [Input Method Manager](/windows/win32/intl/input-method-manager).

## <a name="visual-c-debugger"></a>Depurador de Visual C++

El depurador de Visual C++ proporciona la capacidad de establecer puntos de interrupción en los mensajes IME. Además, la ventana Memoria puede mostrar caracteres de doble byte.

## <a name="command-line-tools"></a>Herramientas de línea de comandos

Las herramientas de línea de comandos de Visual C++, incluido el compilador, NMAKE y el compilador de recursos (RC). EXE), están habilitados para MBCS. Puede usar la opción /c del compilador de recursos para cambiar la página de códigos predeterminada al compilar los recursos de la aplicación.

Para cambiar la configuración regional predeterminada en tiempo de compilación del código fuente, utilice [#pragma setlocale](../preprocessor/setlocale.md).

## <a name="graphical-tools"></a>Herramientas gráficas

Las herramientas basadas en Windows de Visual C++, como Spy++ y las herramientas de edición de recursos, son totalmente compatibles con las cadenas IME.

## <a name="see-also"></a>Consulte también

[Compatibilidad con conjuntos de caracteres multibyte (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)
