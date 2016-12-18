---
title: "Compatibilidad con MBCS en Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mbcs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "idiomas asiáticos [C++]"
  - "juegos de caracteres [C++], multibyte"
  - "caracteres chinos [C++]"
  - "Editor de código [C++], compatibilidad con MBCS"
  - "depurador [C++], compatibilidad con MBCS"
  - "juegos de caracteres de doble byte [C++]"
  - "IME [C++]"
  - "IME [C++], MBCS"
  - "Editor de métodos de entrada [C++]"
  - "Editor de métodos de entrada [C++], MBCS"
  - "caracteres japoneses [C++]"
  - "compatibilidad con caracteres Kanji [C++]"
  - "MBCS [C++], habilitar"
  - "caracteres multibyte [C++]"
  - "NMAKE (programa), compatibilidad con MBCS"
  - "editores de recursos [C++], compatibilidad con MBCS"
  - "herramientas [C++], compatibilidad con MBCS"
ms.assetid: 6179f6b7-bc61-4a48-9267-fb7951223e38
caps.latest.revision: 7
caps.handback.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Compatibilidad con MBCS en Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se ejecuta en una versión habilitada para MBCS del sistema operativo Windows 2000 o Windows XP, el sistema de programación Visual C\+\+ \(incluidos el editor de código fuente integrado, el depurador y las herramientas de línea de comandos\) está habilitado para MBCS, con la excepción de la ventana de memoria.  
  
 La ventana de memoria no interpreta los bytes de datos como caracteres MBCS, aunque puede interpretar como caracteres ANSI o Unicode.  Los caracteres ANSI siempre tienen 1 bytes de tamaño y los caracteres Unicode de 2 bytes de tamaño.  Con MBCS, los caracteres pueden ser 1 o 2 bytes de tamaño y su interpretación dependen de qué página de códigos está en uso.  Debido a esto, es difícil que la ventana memoria presente confiable caracteres MBCS.  La ventana de memoria no puede saber qué byte es el inicio de un carácter.  El desarrollador puede ver los valores de los bytes en la ventana de memoria y buscar el valor en tablas para determinar la representación de caracteres.  Es posible porque el desarrollador conoce la dirección inicial de una cadena basada en el código fuente.  
  
 Visual C\+\+ acepta caracteres de doble byte siempre que sea adecuado.  Se incluyen nombres de archivos y rutas de acceso en cuadros de diálogo, así como entradas de texto en el editor de recursos de Visual C\+\+ \(por ejemplo, texto estático en el editor de cuadros de diálogo y entradas de texto estático en el editor de iconos\).  Además, el preprocesador reconoce algunas directivas de doble byte, por ejemplo, nombres de archivo en instrucciones `#include`, y como argumentos a los pragmas **code\_seg** y **data\_seg**.  En el editor de código fuente, se aceptan caracteres de doble byte en comentarios y en literales de cadena, aunque no en los elementos de lenguaje C\/C\+\+ \(como nombres de variables\).  
  
##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a> Compatibilidad con el Editor de métodos de entrada \(IME\)  
 Las aplicaciones creadas para los mercados de Asia oriental que utilizan MBCS \(por ejemplo, Japón\) admiten normalmente el Editor de métodos de entrada \(IME\) de Windows para escribir caracteres de un solo byte y de doble byte.  El entorno de desarrollo de Visual C\+\+ es totalmente compatible con el Editor de métodos de entrada.  Para obtener más información, vea [Ejemplo IME: Muestra cómo controlar el modo IME e implementar IME de nivel 3](http://msdn.microsoft.com/es-es/87ebdf65-cef0-451d-a6fc-d5fb64178b14).  
  
 Los teclados japoneses no admiten directamente los caracteres Kanji.  IME convierte una cadena fonética, escrita en uno de los restantes alfabetos japoneses \(Romaji, Katakana o Hiragana\) en su posible representación Kanji.  Si hay alguna ambigüedad, se puede elegir entre varias alternativas.  Una vez seleccionados los caracteres Kanji deseados, IME pasa dos mensajes `WM_CHAR` a la aplicación de control.  
  
 El Editor de métodos de entrada, que se activa mediante la combinación de teclas ALT\+\`, aparece como un conjunto de botones \(un indicador\) y una ventana de conversión.  La aplicación sitúa la ventana en el punto de inserción de texto.  La aplicación debe controlar los mensajes `WM_MOVE` y `WM_SIZE` volviendo a situar la ventana de conversión para que se ajuste a la nueva ubicación o al tamaño de la ventana de destino.  
  
 Si se desea que los usuarios de la aplicación tengan la facultad de escribir caracteres Kanji, la aplicación debe controlar mensajes del Editor de métodos de entrada de Windows.  Para obtener más información acerca de la programación IME, vea [Editor de métodos de entrada](https://msdn.microsoft.com/en-us/library/ms776145.aspx).  
  
## Depurador de Visual C\+\+  
 El depurador de Visual C\+\+ proporciona la posibilidad de establecer puntos de interrupción en mensajes del Editor de métodos de entrada \(IME\).  Además, la ventana de memoria puede mostrar caracteres de doble byte.  
  
## Herramientas de línea de comandos  
 Las herramientas de línea de comandos de Visual C\+\+, incluidos el compilador, NMAKE y el compilador de recursos \(RC.EXE\), están habilitadas para MBCS.  Se puede utilizar la opción \/c del compilador de recursos para cambiar la página de códigos predeterminada al compilar los recursos de una aplicación.  
  
 Para cambiar la configuración regional predeterminada en tiempo de compilación del código fuente, utilice [\#pragma setlocale](../preprocessor/setlocale.md).  
  
## Herramientas gráficas  
 Las herramientas basadas en Windows de Visual C\+\+, como Spy\+\+ y las herramientas de edición de recursos, son totalmente compatibles con las cadenas del Editor de métodos de entrada \(IME\).  
  
## Vea también  
 [Compatibilidad con los juegos de caracteres multibyte \(MBCS\)](../text/support-for-multibyte-character-sets-mbcss.md)   
 [Sugerencias de programación para MBCS](../Topic/MBCS%20Programming%20Tips.md)