---
title: "&lt;string&gt; | Microsoft Docs"
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
  - "std::<string>"
  - "string/std::<string>"
  - "std.<string>"
  - "<string>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "string (encabezado)"
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
caps.latest.revision: 23
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;string&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define la clase de plantilla de contenedores `basic_string` y diversas plantillas auxiliares.  
  
 Para más información sobre `basic_string`, consulte [basic\_string \(Clase\)](../standard-library/basic-string-class.md).  
  
## Sintaxis  
  
```  
#include <string>  
```  
  
## Comentarios  
 El lenguaje C\+\+ y la biblioteca estándar de C\+\+ admiten dos tipos de cadenas:  
  
-   Matrices de caracteres terminadas en null, que a menudo se llaman “cadenas de C”.  
  
-   Objetos de clase de plantilla, de tipo `basic_string`, que administran todos los argumentos de plantilla similares a `char`.  
  
### Typedefs  
  
|||  
|-|-|  
|[string](../Topic/string%20\(C++%20STL%20%3Cstring%3E\).md)|Tipo que describe una especialización de la clase de plantilla `basic_string` con elementos de tipo `char` como una `string`.|  
|[wstring](../Topic/wstring.md)|Tipo que describe una especialización de la clase de plantilla `basic_string` con elementos de tipo `wchar_t` como una `wstring`.|  
|[u16string](../Topic/u16string.md)|Tipo que describe una especialización de la clase de plantilla `basic_string` basada en elementos de tipo `char16_t`.|  
|[u32string](../Topic/u32string.md)|Tipo que describe una especialización de la clase de plantilla `basic_string` basada en elementos de tipo `char32_t`.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\+](../Topic/operator+%20\(%3Cstring%3E\).md)|Concatena dos objetos de cadena.|  
|[operator\!\=](../Topic/operator!=%20\(%3Cstring%3E\).md)|Comprueba si el objeto de cadena del lado izquierdo del operador no es igual que el objeto de cadena del lado derecho.|  
|[operator\=\=](../Topic/operator==%20\(%3Cstring%3E\).md)|Comprueba si el objeto de cadena del lado izquierdo del operador es igual que el objeto de cadena del lado derecho.|  
|[operador \<](../Topic/operator%3C%20\(%3Cstring%3E\).md)|Comprueba si el objeto de cadena del lado izquierdo del operador es menor que el objeto de cadena del lado derecho.|  
|[operator\<\=](../Topic/operator%3C=%20\(in%20%3Cstring%3E\).md)|Comprueba si el objeto de cadena del lado izquierdo del operador es menor o igual que el objeto de cadena del lado derecho.|  
|[operador \<\<](../Topic/operator%3C%3C%20\(%3Cstring%3E\).md)|Función de plantilla que inserta una cadena en la secuencia de salida.|  
|[operador \>](../Topic/operator%3E%20\(%3Cstring%3E\).md)|Comprueba si el objeto de cadena del lado izquierdo del operador es mayor que el objeto de cadena del lado derecho.|  
|[operator\>\=](../Topic/operator%3E=%20\(%3Cstring%3E\).md)|Comprueba si el objeto de cadena del lado izquierdo del operador es mayor o igual que el objeto de cadena del lado derecho.|  
|[operador \>\>](../Topic/operator%3E%3E%20\(%3Cstring%3E\).md)|Función de plantilla que extrae una cadena de la secuencia de entrada.|  
  
### Funciones de plantilla especializadas  
  
|||  
|-|-|  
|[swap](../Topic/swap%20\(C++%20STL%20%3Cstring%3E\).md)|Intercambia las matrices de caracteres de dos cadenas.|  
|[stod](../Topic/stod.md)|Convierte una secuencia de caracteres en un `double.`|  
|[stof](../Topic/stof.md)|Convierte una secuencia de caracteres en un `float`|  
|[stoi](../Topic/stoi.md)|Convierte una secuencia de caracteres en un entero.|  
|[stold](../Topic/stold.md)|Convierte una secuencia de caracteres en un `long double`|  
|[stoll](../Topic/stoll.md)|Convierte una secuencia de caracteres en un `long long`|  
|[stoul](../Topic/stoul.md)|Convierte una secuencia de caracteres en un `unsigned long`.|  
|[stoull](../Topic/stoull.md)|Convierte una secuencia de caracteres en un `unsigned long long`.|  
|[to\_string](../Topic/to_string.md)|Convierte un valor en `string`.|  
|[to\_wstring](../Topic/to_wstring.md)|Convierte un valor en una `string` ancha.|  
  
### Funciones  
  
|||  
|-|-|  
|[getline](../Topic/getline%20Template%20Function.md)|Extraiga las cadenas de la secuencia de entrada línea por línea.|  
  
### Clases  
  
|||  
|-|-|  
|[basic\_string \(Clase\)](../standard-library/basic-string-class.md)|Clase de plantilla que describe los objetos que pueden almacenar una secuencia de objetos arbitrarios similares a caracteres.|  
|[char\_traits \(Struct\)](../standard-library/char-traits-struct.md)|Clase de plantilla que describe los atributos asociados a un carácter de tipo CharType|  
  
### Especializaciones  
  
|||  
|-|-|  
|[char\_traits\<char\> \(Struct\)](../standard-library/char-traits-char-struct.md)|Un struct que es una especialización del struct de plantilla `char_traits`\<CharType\> para un elemento de tipo `char`.|  
|[char\_traits\<wchar\_t\> \(Struct\)](../standard-library/char-traits-wchar-t-struct.md)|Un struct que es una especialización del struct de plantilla `char_traits`\<CharType\> para un elemento de tipo `wchar_t`.|  
|[char\_traits\<char16\_t\> \(Struct\)](../standard-library/char-traits-char16-t-struct.md)|Un struct que es una especialización del struct de plantilla `char_traits`\<CharType\> para un elemento de tipo `char16_t`.|  
|[char\_traits\<char32\_t\> \(Struct\)](../standard-library/char-traits-char32-t-struct.md)|Un struct que es una especialización del struct de plantilla `char_traits`\<CharType\> para un elemento de tipo `char32_t`.|  
  
## Requisitos  
  
-   **Encabezado:** \<string\>  
  
-   **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)