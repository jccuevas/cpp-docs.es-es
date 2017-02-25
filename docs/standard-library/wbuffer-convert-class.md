---
title: "wbuffer_convert (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext::cvt::wbuffer_convert"
  - "wbuffer_convert"
  - "stdext.cvt.wbuffer_convert"
  - "cvt.wbuffer_convert"
  - "cvt::wbuffer_convert"
  - "wbuffer/stdext::cvt::wbuffer_convert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "wbuffer_convert (clase)"
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# wbuffer_convert (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un búfer de secuencia que controla la transmisión de elementos a y desde un búfer de secuencia de bytes.  
  
## Sintaxis  
  
```  
template<class Codecvt,  
    class Elem = wchar_t,  
    class Traits = std::char_traits<Elem>  
>  
    class wbuffer_convert  
        : public std::basic_streambuf<Elem, Traits>  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Codecvt`|Faceta [locale](../standard-library/locale-class.md) que representa el objeto de conversión.|  
|`Elem`|Tipo de elemento de carácter ancho.|  
|`Traits`|Rasgos asociados a *Elem*.|  
  
## Comentarios  
 Esta clase de plantilla describe un búfer de secuencia que controla la transmisión de elementos de tipo `_Elem` cuyos rasgos de caracteres se describen por medio de la clase `Traits`, a y desde una secuencia de tipo `std::streambuf`.  
  
 La conversión entre una secuencia de valores `Elem` y las secuencias multibyte se realiza con un objeto de clase `Codecvt<Elem, char, std::mbstate_t>`, que cumple los requisitos de la faceta de conversión de código estándar `std::codecvt<Elem, char, std::mbstate_t>`.  
  
 Un objeto de esta clase de plantilla almacena lo siguiente:  
  
-   Un puntero a su búfer de secuencia de bytes subyacente  
  
-   Un puntero al objeto de conversión asignado \(que se libera cuando el objeto [wbuffer\_convert](../standard-library/wbuffer-convert-class.md) se destruye\)  
  
-   Un objeto de estado de la conversión de tipo [state\_type](../Topic/wbuffer_convert::state_type.md)  
  
### Constructores  
  
|||  
|-|-|  
|[wbuffer\_convert](../Topic/wbuffer_convert::wbuffer_convert.md)|Construye un objeto de tipo `wbuffer_convert`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[state\_type](../Topic/wbuffer_convert::state_type.md)|Tipo que representa el estado de la conversión.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[rdbuf](../Topic/wbuffer_convert::rdbuf.md)|Devuelve el búfer de la secuencia de bytes.|  
|[estado](../Topic/wbuffer_convert::state.md)|Devuelve un objeto que representa el estado de la conversión.|  
  
## Requisitos  
 **Encabezado:** \<locale\>  
  
 **Espacio de nombres:** std