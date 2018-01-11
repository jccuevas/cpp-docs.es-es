---
title: Compatibilidad con MBCS en Visual C++ | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mbcs
dev_langs: C++
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
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bdc00509d8660d8111ff1b966b7a881a153cb6c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mbcs-support-in-visual-c"></a>Compatibilidad con MBCS en Visual C++
Cuando se ejecuta en una versión habilitada para MBCS del sistema operativo Windows 2000 o Windows XP, el sistema de desarrollo de Visual C++ (incluidos el editor de código fuente integrado, depurador y las herramientas de línea de comandos) está habilitado para MBCS, con la excepción de la ventana de memoria.  
  
 La ventana memoria no interpreta los bytes de datos como caracteres MBCS, aunque pueda interpretarlos como caracteres ANSI o Unicode. Caracteres ANSI siempre tienen 1 byte de tamaño y los caracteres Unicode son 2 bytes de tamaño. Con MBCS, los caracteres pueden ser 1 o 2 bytes de tamaño y su interpretación depende de la página de códigos que está en uso. Por este motivo, resulta difícil para la ventana de memoria para mostrar de forma confiable caracteres MBCS. La ventana memoria no puede saber qué bytes es el inicio de un carácter. El desarrollador puede ver los valores de byte en la ventana de memoria y buscar el valor en tablas para determinar la representación de caracteres. Esto es posible porque el desarrollador conoce la dirección inicial de una cadena basándose en el código fuente.  
  
 Visual C++ acepta caracteres de doble byte, donde sea adecuado realizarlo. Esto incluye nombres de ruta de acceso y nombres de archivo en los cuadros de diálogo y entradas de texto en el editor de recursos de Visual C++ (por ejemplo, texto estático en el editor de cuadro de diálogo) y entradas de texto estático en el editor de iconos. Además, el preprocesador reconoce algunas directivas de doble byte, por ejemplo, nombres de archivo en `#include` instrucciones y como argumentos a la **code_seg** y **data_seg** pragma (directivas). En el editor de código fuente, se aceptan caracteres de doble byte en comentarios y los literales de cadena, aunque no en elementos del lenguaje C o C++ (por ejemplo, los nombres de variable).  
  
##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>Compatibilidad con el Editor de métodos de entrada (IME)  
 Aplicaciones escritas para los mercados de Asia oriental que utilizan MBCS (por ejemplo, Japón) normalmente admiten el IME de Windows para escribir los caracteres de byte y de doble byte. El entorno de desarrollo de Visual C++ es totalmente compatible con el IME. Para obtener más información, consulte [ejemplo IME: muestra cómo controlar el modo IME e implemente IME nivel 3](http://msdn.microsoft.com/en-us/87ebdf65-cef0-451d-a6fc-d5fb64178b14).  
  
 Los teclados japoneses no son directamente compatibles con caracteres Kanji. El IME convierte una cadena fonética, escrita en uno de los otros alfabetos japoneses (Romaji, Katakana o Hiragana) en sus posibles representaciones Kanji. Si no hay ambigüedad, puede seleccionar entre varias alternativas. Cuando haya seleccionado los caracteres Kanji deseados, IME pasa dos `WM_CHAR` mensajes a la aplicación de control.  
  
 El IME, activado el ALT +\` la combinación de teclas, aparecerá como un conjunto de botones (un indicador) y una ventana de conversión. La aplicación sitúa la ventana en el punto de inserción de texto. La aplicación debe administrar `WM_MOVE` y `WM_SIZE` mensajes por cambiar la posición de la ventana de conversión para que se ajuste a la nueva ubicación o el tamaño de la ventana de destino.  
  
 Si desea que los usuarios de su aplicación tenga la posibilidad de escribir caracteres Kanji, la aplicación debe controlar mensajes de Windows IME. Para obtener más información acerca de la programación IME, vea [Input Method Editor](https://msdn.microsoft.com/en-us/library/ms776145.aspx).  
  
## <a name="visual-c-debugger"></a>Depurador de Visual C++  
 El depurador de Visual C++ proporciona la capacidad de establecer puntos de interrupción en los mensajes IME. Además, la ventana memoria puede mostrar caracteres de doble byte.  
  
## <a name="command-line-tools"></a>Herramientas de línea de comandos  
 Las herramientas de línea de comandos de Visual C++, incluidos el compilador, NMAKE y el compilador de recursos (RC. (EXE), están habilitadas para MBCS. Puede utilizar la opción /c del compilador de recursos para cambiar la página de códigos predeterminada al compilar recursos de su aplicación.  
  
 Para cambiar la configuración regional predeterminada en tiempo de compilación de código fuente, utilice [#pragma setlocale](../preprocessor/setlocale.md).  
  
## <a name="graphical-tools"></a>Herramientas gráficas  
 Las herramientas basadas en Windows de Visual C++, como Spy ++ y el recurso de herramientas, de edición son totalmente compatibles con las cadenas IME.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con juegos de caracteres Multibyte (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)   
 [Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)