---
title: "ctype (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ctype"
  - "std::ctype"
  - "std.ctype"
  - "CType"
  - "xlocale/std::ctype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ctype (clase)"
ms.assetid: 3627154c-49d9-47b5-b28f-5bbedee38e3b
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# ctype (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase que proporciona una faceta que se emplea para clasificar los caracteres, pasar de mayúsculas a minúsculas y convertir entre el juego de caracteres nativo y el que usa la configuración regional.  
  
## Sintaxis  
  
```  
template <class CharType>  
   class ctype : public ctype_base;  
```  
  
#### Parámetros  
 `CharType`  
 Tipo usado dentro de un programa para codificar caracteres.  
  
## Comentarios  
 Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero.  El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.** Se proporciona a los criterios de clasificación un tipo de máscara de bits anidado en el ctype\_base de la clase base.  
  
 La Biblioteca estándar de C\+\+ define dos especializaciones explícitas de esta clase de plantilla:  
  
-   [ctype](#vclrf_locale_ctype_class)\<`char`\>, una especialización explícita cuyas diferencias se describen por separado.  
  
-   **ctype**\<`wchar_t`\>, que trata los elementos como caracteres anchos.  
  
 Otras especializaciones de la clase de plantilla **ctype**\<**CharType**\>:  
  
-   Convierte un valor ***ch*** de tipo **CharType** en un valor de tipo `char` con la expresión \(`char`\)**ch**.  
  
-   Convierte un valor ***byte*** de tipo `char` en un valor de tipo **CharType** con la expresión **CharType** \(**byte**\).  
  
 Todas las demás operaciones se realizan sobre los valores `char` igual que para la especialización explícita **ctype**\<`char`\>.  
  
### Constructores  
  
|||  
|-|-|  
|[ctype](../Topic/ctype::ctype.md)|Constructor de objetos de clase `ctype` que actúan como facetas de configuración regional para los caracteres.|  
  
### Typedefs  
  
|||  
|-|-|  
|[char\_type](../Topic/ctype::char_type.md)|Tipo que describe un carácter usado por una configuración regional.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[do\_is](../Topic/ctype::do_is.md)|Función virtual a la que se llama para comprobar si un carácter individual tiene un atributo determinado, o para clasificar los atributos de cada carácter de un intervalo y almacenarlos en una matriz.|  
|[do\_narrow](../Topic/ctype::do_narrow.md)|Función virtual a la que se llama para convertir un carácter de tipo `CharType` usado por una configuración regional en el carácter correspondiente de tipo `char` del juego de caracteres nativo.|  
|[do\_scan\_is](../Topic/ctype::do_scan_is.md)|Función virtual a la que se llama para buscar el primer carácter de un intervalo que coincide con una máscara especificada.|  
|[do\_scan\_not](../Topic/ctype::do_scan_not.md)|Función virtual a la que se llama para buscar el primer carácter de un intervalo que no coincide con una máscara especificada.|  
|[do\_tolower](../Topic/ctype::do_tolower.md)|Función virtual a la que se llama para convertir a minúsculas un carácter o un intervalo de caracteres.|  
|[do\_toupper](../Topic/ctype::do_toupper.md)|Función virtual a la que se llama para convertir a mayúsculas un carácter o un intervalo de caracteres.|  
|[do\_widen](../Topic/ctype::do_widen.md)|Función virtual a la que se llama para convertir un carácter de tipo `char` del juego de caracteres nativo en el carácter correspondiente de tipo `CharType` usado por una configuración regional.|  
|[is](../Topic/ctype::is.md)|Comprueba si un carácter individual tiene un atributo determinado, o clasifica los atributos de cada carácter de un intervalo y los almacena en una matriz.|  
|[narrow](../Topic/ctype::narrow.md)|Convierte un carácter de tipo `CharType` usado por una configuración regional en el carácter correspondiente de tipo char del juego de caracteres nativo.|  
|[scan\_is](../Topic/ctype::scan_is.md)|Busca el primer carácter de un intervalo que coincide con una máscara especificada.|  
|[scan\_not](../Topic/ctype::scan_not.md)|Busca el primer carácter de un intervalo que no coincide con una máscara especificada.|  
|[tolower](../Topic/ctype::tolower.md)|Convierte a minúsculas un carácter o un intervalo de caracteres.|  
|[toupper](../Topic/ctype::toupper.md)|Convierte a mayúsculas un carácter o un intervalo de caracteres.|  
|[widen](../Topic/ctype::widen.md)|Convierte un carácter de tipo `char` del juego de caracteres nativo en el carácter correspondiente de tipo `CharType` usado por una configuración regional.|  
  
## Requisitos  
 **Encabezado:** \<locale\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<locale\>](../standard-library/locale.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)