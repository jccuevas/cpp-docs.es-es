---
title: "Compatibilidad con Unicode | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "juegos de caracteres [C++], Unicode"
  - "globalización [C++], juegos de caracteres"
  - "localización [C++], juegos de caracteres"
  - "tipos de datos portables [MFC]"
  - "Unicode [C++]"
  - "Unicode [C++], configurar compatibilidad"
  - "caracteres anchos [C++], acerca de los caracteres anchos"
ms.assetid: 180f1d10-8543-4f79-85ce-293d3cb443bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Compatibilidad con Unicode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Unicode es una especificación para admitir todos los juegos de caracteres, incluidos los que no pueden representarse en un solo byte.  Si programa para un mercado internacional, le recomendamos que utilice Unicode o [juegos de caracteres multibyte](../text/support-for-multibyte-character-sets-mbcss.md) \(MBCS\), o que habilite el programa de modo que pueda compilarlo para ambos cambiando un modificador.  
  
 Un carácter ancho es un código de carácter multilingüe de dos bytes.  La mayoría de los caracteres que se usan en la informática moderna alrededor del mundo, como los símbolos técnicos o los caracteres de publicación especiales, se puede representar de acuerdo con la especificación Unicode en forma de carácter ancho.  Los caracteres que no se pueden representar en un solo carácter ancho pueden representarse en un par Unicode con la característica de suplente Unicode.  Puesto que los caracteres anchos siempre tienen un tamaño fijo, 16 bits, con los caracteres anchos se simplifica la programación con juegos de caracteres internacionales.  
  
 Una cadena de caracteres anchos se representa como una matriz **wchar\_t\[\]** y apunta a ella un puntero `wchar_t*`.  Cualquier carácter ASCII se puede representar como un carácter ancho agregando la letra L al principio del carácter.  Por ejemplo, L'\\0' es el carácter **nulo** ancho \(de 16 bits\) de terminación.  De manera similar, cualquier literal de cadena ASCII se puede representar como un literal de cadena de caracteres anchos agregando la letra L al principio del literal ASCII \(L"Hola"\).  
  
 En general, los caracteres anchos ocupan más espacio en la memoria que los caracteres multibyte, pero se procesan más rápido.  Además, en la codificación multibyte no se pueden representar varias configuraciones regionales a la vez, mientras que la representación de Unicode representa simultáneamente a todos los juegos de caracteres del mundo.  
  
 Todo el marco MFC está habilitado para Unicode. MFC habilita Unicode con macros portables, como se muestra en la tabla siguiente.  
  
### Tipos de datos portables en MFC  
  
|Tipo de datos no portable|Reemplazado por esta macro|  
|-------------------------------|--------------------------------|  
|`char`|\_**TCHAR**|  
|**char\***, **LPSTR \(tipo de datos de Win32\)**|`LPTSTR`|  
|**const char\*, LPCSTR \(tipo de datos de Win32\)**|`LPCTSTR`|  
  
 La clase `CString` utiliza **\_TCHAR** como base y proporciona constructores y operadores para realizar conversiones fácilmente.  La mayoría de las operaciones de cadena de Unicode se puede escribir con la misma lógica que se usa para administrar el juego de caracteres ANSI de Windows, con la diferencia de que la unidad de operación básica es un carácter de 16 bits en lugar de un byte de 8 bits.  A diferencia de cuando se trabaja con juegos de caracteres multibyte, no es necesario \(y no se debe\) tratar un carácter Unicode como si fueran dos bytes independientes.  
  
## ¿Qué desea hacer?  
  
-   [Instalar la compatibilidad de Unicode con MFC](../mfc/unicode-in-mfc.md)  
  
-   [Habilitar Unicode en un programa](../text/international-enabling.md)  
  
-   [Habilitar Unicode y MBCS en mi programa](../text/internationalization-strategies.md)  
  
-   [Utilizar Unicode para crear un programa internacionalizado](../text/unicode-programming-summary.md)  
  
-   [Aprender sobre las ventajas de Unicode como, por ejemplo, cómo Unicode hace que un programa sea más eficiente en Windows 2000](../text/benefits-of-character-set-portability.md)  
  
-   [Usar wmain para pasar argumentos de caracteres anchos a un programa](../text/support-for-using-wmain.md)  
  
-   [Ver un resumen de la programación con Unicode](../text/unicode-programming-summary.md)  
  
-   [Obtener información sobre asignaciones de texto genérico para portabilidad de ancho de byte](../Topic/Generic-Text%20Mappings%20in%20Tchar.h.md)  
  
## Vea también  
 [Texto y cadenas](../text/text-and-strings-in-visual-cpp.md)   
 [Compatibilidad con el uso de wmain](../text/support-for-using-wmain.md)