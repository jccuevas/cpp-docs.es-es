---
title: Compatibilidad con MBCS en Visual C++
ms.date: 11/04/2016
f1_keywords:
- _mbcs
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
ms.openlocfilehash: 0108068f15132fea38189e17371490a7c0dd5d8b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465242"
---
# <a name="mbcs-support-in-visual-c"></a>Compatibilidad con MBCS en Visual C++

Cuando se ejecuta en una versión habilitada para MBCS de Windows, el sistema de desarrollo de Visual C++ (incluidas las herramientas de línea de comandos, el depurador y el editor de código fuente integrado) está habilitado para MBCS, a excepción de la ventana de la memoria.

La ventana memoria no interpreta los bytes de datos como caracteres MBCS, aunque puede interpretarlos como caracteres ANSI o Unicode. Caracteres ANSI siempre son de 1 byte de tamaño y los caracteres Unicode son de tamaño de 2 bytes. Con MBCS, los caracteres pueden ser 1 o 2 bytes de tamaño y su interpretación depende de la página de códigos que está en uso. Por este motivo, es difícil para la ventana de memoria para mostrar de forma confiable caracteres MBCS. La ventana memoria no puede saber qué byte es el inicio de un carácter. El desarrollador puede ver los valores de byte en la ventana de la memoria y buscar el valor de las tablas para determinar la representación de caracteres. Esto es posible porque el desarrollador sabe la dirección inicial de una cadena basándose en el código fuente.

Visual C++ acepta caracteres de doble byte, siempre que sea adecuado hacerlo. Esto incluye los nombres de ruta de acceso y nombres de archivo en los cuadros de diálogo y las entradas de texto en el editor de recursos de Visual C++ (por ejemplo, texto estático en el editor de cuadro de diálogo) y entradas de texto estático en el editor de iconos. Además, el preprocesador reconoce algunas directivas de doble byte, por ejemplo, nombres de archivo en `#include` instrucciones y como argumentos a la `code_seg` y `data_seg` pragmas. En el editor de código fuente, se aceptan caracteres de doble byte en los comentarios y los literales de cadena, aunque no en elementos del lenguaje C o C++ (por ejemplo, los nombres de variable).

##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a> Compatibilidad con el Editor de métodos de entrada (IME)

Aplicaciones escritas para los mercados del este asiático que utilizan MBCS (por ejemplo, Japón) normalmente admiten el IME de Windows para escribir ambos caracteres único y de doble byte. El entorno de desarrollo de Visual C++ es totalmente compatible con el IME.

Teclados japoneses no son directamente compatibles con caracteres Kanji. El IME convierte una cadena fonética, escrita en uno de los otros alfabetos japoneses (Hiragana, Katakana o Romaji) en sus posibles representaciones Kanji. Si no hay ambigüedad, puede seleccionar entre varias alternativas. Cuando haya seleccionado los caracteres Kanji deseados, IME pasa dos `WM_CHAR` mensajes a la aplicación de control.

El IME, activado por ALT +\` combinación de teclas, aparece como un conjunto de botones (un indicador) y una ventana de conversión. La aplicación coloca la ventana en el punto de inserción de texto. La aplicación debe controlar `WM_MOVE` y `WM_SIZE` mensajes por cambiar la posición de la ventana de conversión que se ajuste a la nueva ubicación o el tamaño de la ventana de destino.

Si desea que los usuarios de la aplicación y tener la capacidad de escribir caracteres Kanji, la aplicación debe controlar los mensajes de IME de Windows. Para obtener más información acerca de la programación de IME, vea [Administrador de métodos de entrada](/windows/desktop/intl/input-method-manager).

## <a name="visual-c-debugger"></a>Depurador de Visual C++

El depurador de Visual C++ proporciona la capacidad de establecer puntos de interrupción en los mensajes IME. Además, la ventana memoria puede mostrar caracteres de doble byte.

## <a name="command-line-tools"></a>Herramientas de línea de comandos

Las herramientas de línea de comandos de Visual C++, incluidos el compilador, NMAKE y el compilador de recursos (RC. (EXE), están habilitadas para MBCS. Puede usar la opción de /c del compilador de recursos para cambiar la página de códigos predeterminada al compilar recursos de su aplicación.

Para cambiar la configuración regional predeterminada en tiempo de compilación de código fuente, utilice [#pragma setlocale](../preprocessor/setlocale.md).

## <a name="graphical-tools"></a>Herramientas gráficas

Las herramientas basadas en Windows de Visual C++, como Spy ++ y el recurso de herramientas, de edición son totalmente compatibles con las cadenas IME.

## <a name="see-also"></a>Vea también

[Compatibilidad con los juegos de caracteres multibyte (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)