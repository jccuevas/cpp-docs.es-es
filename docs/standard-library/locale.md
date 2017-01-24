---
title: "&lt;locale&gt; | Microsoft Docs"
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
  - "<locale>"
  - "std.<locale>"
  - "locale/std::<locale>"
  - "std::<locale>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "locale (encabezado)"
ms.assetid: ca56f9d2-7128-44da-8df1-f4c78c17fbf2
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;locale&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define funciones y clases de plantilla que los programas de C\+\+ pueden utilizar para encapsular y manipular distintas convenciones culturales relativas a la representación y el formato de datos numéricos, de moneda y de calendario, incluida la compatibilidad de internacionalización para la clasificación de caracteres y la intercalación de cadenas.  
  
## Sintaxis  
  
```  
  
#include <locale>  
  
```  
  
### Funciones  
  
|||  
|-|-|  
|[has\_facet](../Topic/has_facet.md)|Comprueba si una faceta determinada se almacena en una configuración regional especificada.|  
|[isalnum](../Topic/isalnum.md)|Comprueba si un elemento de una configuración regional es un carácter alfabético o numérico.|  
|[isalpha](../Topic/isalpha.md)|Comprueba si un elemento de una configuración regional es un carácter alfabético.|  
|[iscntrl](../Topic/iscntrl.md)|Comprueba si un elemento de una configuración regional es un carácter de control.|  
|[isdigit](../Topic/isdigit.md)|Comprueba si un elemento de una configuración regional es un carácter numérico.|  
|[isgraph](../Topic/isgraph.md)|Comprueba si un elemento de una configuración regional es un carácter alfabético o un signo de puntuación.|  
|[islower](../Topic/islower.md)|Comprueba si un elemento de una configuración regional está en minúsculas.|  
|[isprint](../Topic/isprint.md)|Comprueba si un elemento de una configuración regional es un carácter imprimible.|  
|[ispunct](../Topic/ispunct.md)|Comprueba si un elemento de una configuración regional es un carácter de signo de puntuación.|  
|[isspace](../Topic/isspace.md)|Comprueba si un elemento de una configuración regional es un carácter de espacio en blanco.|  
|[isupper](../Topic/isupper.md)|Comprueba si un elemento de una configuración regional está en mayúsculas.|  
|[isxdigit](../Topic/isxdigit.md)|Comprueba si un elemento de una configuración regional es un carácter usado para representar un número hexadecimal.|  
|[tolower](../Topic/tolower.md)|Pasa un carácter a minúsculas.|  
|[toupper](../Topic/toupper.md)|Pasa un carácter a mayúsculas.|  
|[use\_facet](../Topic/use_facet.md)|Devuelve una referencia a una faceta de un tipo especificado almacenado en una configuración regional.|  
  
### Clases  
  
|||  
|-|-|  
|[codecvt](../standard-library/codecvt-class.md)|Clase de plantilla que proporciona una faceta utilizada para convertir entre las codificaciones de caracteres internas y externas.|  
|[codecvt\_base](../standard-library/codecvt-base-class.md)|Una clase base de la clase codecvt que se utiliza para definir un tipo de enumeración al que se hace referencia como **result**, que se usa como el tipo de valor devuelto para las funciones miembro de la faceta para indicar el resultado de una conversión.|  
|[codecvt\_byname](../standard-library/codecvt-byname-class.md)|Una clase de plantilla derivada que describe un objeto que puede actuar como faceta de intercalación de una configuración regional concreta, lo que permite la recuperación de información específica de un área cultural relativa a las conversiones.|  
|[collate](../standard-library/collate-class.md)|Una clase de plantilla de intercalación que proporciona una faceta que controla las convenciones para la ordenación de cadenas.|  
|[collate\_byname](../standard-library/collate-byname-class.md)|Una clase de plantilla derivada que describe un objeto que puede actuar como una faceta de intercalación de una configuración regional concreta, lo que permite la recuperación de información específica de un área cultural relativa a las convenciones de ordenación de cadenas.|  
|[ctype](../standard-library/ctype-class.md)|Una clase de plantilla que proporciona una faceta que se utiliza para ordenar caracteres, convertir entre mayúsculas y minúsculas, y entre el conjunto de caracteres nativo y el que usa la configuración regional.|  
|[ctype\<char\>](../standard-library/ctype-char-class.md)|Una clase que es una especialización explícita de la clase de plantilla **ctype\<CharType**\> al tipo `char`, que describe un objeto que puede actuar como una faceta de configuración regional para caracterizar distintas propiedades de un carácter de tipo `char`.|  
|[ctype\_base](../standard-library/ctype-base-class.md)|Una clase base para la clase ctype que se utiliza para definir los tipos de enumeración usados para clasificar o comprobar caracteres individualmente o dentro de intervalos completos.|  
|[ctype\_byname](../standard-library/ctype-byname-class.md)|Una clase de plantilla derivada que describe un objeto que puede actuar como faceta ctype de una configuración regional concreta, habilitando la clasificación y conversión de caracteres entre mayúsculas y minúsculas y entre los conjuntos de caracteres especificados en la configuración regional y nativa.|  
|[configuración regional](../standard-library/locale-class.md)|Una clase que describe un objeto de configuración regional que encapsula la información específica de la configuración regional como un conjunto de facetas que definen colectivamente un entorno adaptado concreto.|  
|[mensajes](../standard-library/messages-class.md)|Una clase de plantilla que describe un objeto que puede actuar como una faceta de configuración regional para recuperar mensajes adaptados de un catálogo de mensajes internacionalizados para una configuración regional concreta.|  
|[messages\_base](../standard-library/messages-base-class.md)|Una clase base que describe un tipo `int` para el catálogo de mensajes.|  
|[messages\_byname](../standard-library/messages-byname-class.md)|Una clase de plantilla derivada que describe un objeto que puede actuar como una faceta de mensajes de una configuración regional concreta, lo que permite la recuperación de mensajes adaptados.|  
|[money\_base](../standard-library/money-base-class.md)|Una clase base para la clase ctype que se utiliza para definir los tipos de enumeración usados para clasificar o comprobar caracteres individualmente o dentro de intervalos completos.|  
|[money\_get](../standard-library/money-get-class.md)|Una clase de plantilla que describe un objeto que puede actuar como una faceta de configuración regional para controlar las conversiones de las secuencias de tipo **CharType** en valores monetarios.|  
|[money\_put](../standard-library/money-put-class.md)|Una clase de plantilla que describe un objeto que puede actuar como una faceta de configuración regional para controlar las conversiones de valores monetarios en secuencias de tipo **CharType**.|  
|[moneypunct](../standard-library/moneypunct-class.md)|Una clase de plantilla que describe un objeto que puede actuar como una faceta de configuración regional para describir las secuencias de tipo **CharType** usadas para representar un campo monetario de entrada o de salida.|  
|[moneypunct\_byname](../standard-library/moneypunct-byname-class.md)|Una clase de plantilla derivada que describe un objeto que puede actuar como una faceta moneypunct de una configuración regional concreta que permite el formato de los campos monetarios de entrada o de salida.|  
|[num\_get](../standard-library/num-get-class.md)|Una clase de plantilla que describe un objeto que puede actuar como una faceta de configuración regional para controlar las conversiones de secuencias de tipo **CharType** en valores numéricos.|  
|[num\_put](../standard-library/num-put-class.md)|Una clase de plantilla que describe un objeto que puede actuar como una faceta de configuración regional para controlar las conversiones de valores numéricos en secuencias de tipo **CharType**.|  
|[numpunct](../standard-library/numpunct-class.md)|Una clase de plantilla que describe un objeto que puede actuar como una faceta de configuración regional para describir las secuencias de tipo **CharType** usadas para representar información sobre el formato y la puntuación de expresiones numéricas y booleanas.|  
|[numpunct\_byname](../standard-library/numpunct-byname-class.md)|Una clase de plantilla derivada que describe un objeto que puede actuar como faceta moneypunct de una configuración regional concreta, lo que habilita el formato y la puntuación de expresiones numéricas y booleanas.|  
|[time\_base](../standard-library/time-base-class.md)|Una clase que actúa como clase base para las facetas de la clase de plantilla time\_get y que define el tipo enumerado dateorder y varias de sus constantes.|  
|[time\_get](../standard-library/time-get-class.md)|Una clase de plantilla que describe un objeto que puede actuar como una faceta de configuración regional para controlar las conversiones de secuencias de tipo **CharType** en valores de hora.|  
|[time\_get\_byname](../standard-library/time-get-byname-class.md)|Una clase de plantilla derivada que describe un objeto que puede actuar como una faceta de configuración regional de tipo time\_get\<**CharType**, **InputIterator**\>.|  
|[time\_put](../standard-library/time-put-class.md)|Una clase de plantilla que describe un objeto que puede actuar como una faceta de configuración regional para controlar las conversiones de valores de hora en secuencias de tipo **CharType**.|  
|[time\_put\_byname](../standard-library/time-put-byname-class.md)|Una clase de plantilla derivada que describe un objeto que puede actuar como una faceta de configuración regional de tipo `time_put`\<**CharType**, **OutputIterator**\>.|  
|[wbuffer\_convert \(Clase\)](../standard-library/wbuffer-convert-class.md)|Describe un búfer de secuencia que controla la transmisión de elementos a y desde un búfer de secuencia de bytes.|  
|[wstring\_convert \(Clase\)](../standard-library/wstring-convert-class.md)|Una clase de plantilla que realiza conversiones entre una cadena de caracteres anchos y una cadena de bytes.|  
  
## Vea también  
 [Páginas de códigos](../c-runtime-library/code-pages.md)   
 [Nombres de configuración regional, idiomas y cadenas de país\/región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)