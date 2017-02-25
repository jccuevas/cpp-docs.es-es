---
title: "Flujos de entrada/salida | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "E/S [C++], secuencia"
  - "E/S de secuencia"
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Flujos de entrada/salida
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`basic_iostream`, que se define en el \<istream del\>archivo de encabezado, es la plantilla de clase para los objetos que administran las secuencias entradas y resultados carácter\- basadas de E\/S.  
  
 Hay dos definiciones de tipos que definen especializaciones carácter\- específicas de `basic_iostream` y pueden ayudar a que el código sea más fácil de leer: `iostream` \(no confundir con el iostream \<del\>archivo de encabezado\) es una E\/S transmitir basado en `basic_iostream<char>`; `wiostream` es una E\/S transmitir basado en `basic_iostream<wchar_t>`.  
  
 Para obtener más información, vea [basic\_iostream \(Clase\)](../standard-library/basic-iostream-class.md), [iostream](../Topic/iostream.md) y [wiostream](../Topic/wiostream.md).  
  
 La derivación de `basic_iostream` es la plantilla `basic_fstream`de clase, que se utiliza para transmitir datos de caracteres a y desde los archivos.  
  
 También hay tipos que proporcionan especializaciones carácter\- específicas de `basic_fstream`.  Son `fstream`, que es una E\/S de archivo transmitir basado en `char`, y `wfstream`, que es una E\/S de archivo transmitir basado en `wchar_t`.  Para obtener más información, vea [basic\_fstream \(Clase\)](../standard-library/basic-fstream-class.md), [fstream](../Topic/fstream.md) y [wfstream](../Topic/wfstream.md).  Mediante estos typedefs requiere la inclusión del fstream \<\>del archivo de encabezado.  
  
> [!NOTE]
>  Cuando un objeto de `basic_fstream` se utiliza para realizar operaciones de E\/S de archivos, aunque el búfer subyacente contiene las posiciones por separado comunican para leer y escribir, entrada actual y las posiciones actuales de salida están vinculadas entre sí y, por consiguiente, leyendo a movimientos de algunos datos la posición de la salida.  
  
 La plantilla `basic_stringstream` de la clase y la especialización común, `stringstream`, se suelen utilizar para trabajar con objetos de secuencia de E\/S para insertar y para extraer datos de caracteres.  Para obtener más información, vea [basic\_stringstream \(Clase\)](../standard-library/basic-stringstream-class.md).  
  
## Vea también  
 [stringstream](../Topic/stringstream.md)   
 [basic\_stringstream \(Clase\)](../standard-library/basic-stringstream-class.md)   
 [\<sstream\>](../standard-library/sstream.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Biblioteca estándar de C\+\+](../standard-library/cpp-standard-library-reference.md)