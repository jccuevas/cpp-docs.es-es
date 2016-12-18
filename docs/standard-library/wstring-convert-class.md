---
title: "wstring_convert (Clase) | Microsoft Docs"
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
  - "cvt.wstring_convert"
  - "wstring_convert"
  - "stdext::cvt::wstring_convert"
  - "cvt::wstring_convert"
  - "wstring/stdext::cvt::wstring_convert"
  - "stdext.cvt.wstring_convert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "wstring_convert (clase)"
ms.assetid: e34f5b65-d572-4bdc-ac69-20778712e376
caps.latest.revision: 25
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wstring_convert (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla `wstring_convert` realiza conversiones entre una cadena de caracteres anchos y una cadena de bytes.  
  
## Sintaxis  
  
```  
template<  
    class Codecvt,  
    class Elem = wchar_t  
>  
class wstring_convert  
```  
  
#### Parámetros  
 Codecvt  
 Faceta [locale](../standard-library/locale-class.md) que representa el objeto de conversión.  
  
 Elem  
 Tipo de elemento de carácter ancho.  
  
## Comentarios  
 La clase de plantilla describe un objeto que controla las conversiones entre objetos de cadena de caracteres anchos de la clase `std::basic_string<Elem>` y objetos de cadena de bytes de la clase `std::basic_string<char>` \(también conocida como `std::string`\). La clase de plantilla define los tipos `wide_string` y `byte_string` como sinónimos de estos dos tipos. La conversión entre una secuencia de valores `Elem` \(almacenada en un objeto `wide_string`\) y las secuencias multibyte \(almacenadas en un objeto `byte_string`\) se realiza con un objeto de clase `Codecvt<Elem, char, std::mbstate_t>`, que cumple los requisitos de la faceta de conversión de código estándar `std::codecvt<Elem, char, std::mbstate_t>`.  
  
 Un objeto de esta clase de plantilla almacena lo siguiente:  
  
-   Una cadena de bytes que se mostrará al producirse errores  
  
-   Una cadena caracteres anchos que se mostrará al producirse errores  
  
-   Un puntero al objeto de conversión asignado \(que se libera cuando el objeto wbuffer\_convert se destruye\)  
  
-   Un objeto de estado de la conversión de tipo [state\_type](../Topic/wstring_convert::state_type.md)  
  
-   Un recuento de conversión  
  
### Constructores  
  
|||  
|-|-|  
|[wstring\_convert](../Topic/wstring_convert::wstring_convert.md)|Construye un objeto de tipo `wstring_convert`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[byte\_string](../Topic/wstring_convert::byte_string.md)|Tipo que representa una cadena de bytes.|  
|[wide\_string](../Topic/wstring_convert::wide_string.md)|Tipo que representa una cadena de caracteres anchos.|  
|[state\_type](../Topic/wstring_convert::state_type.md)|Tipo que representa el estado de la conversión.|  
|[int\_type](../Topic/wstring_convert::int_type.md)|Tipo que representa un número entero.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[from\_bytes](../Topic/wstring_convert::from_bytes.md)|Convierte una cadena de bytes en una cadena de caracteres anchos.|  
|[to\_bytes](../Topic/wstring_convert::to_bytes.md)|Convierte una cadena de caracteres anchos en una cadena de bytes.|  
|[converted](../Topic/wstring_convert::converted.md)|Devuelve el número de conversiones correctas.|  
|[estado](../Topic/wstring_convert::state.md)|Devuelve un objeto que representa el estado de la conversión.|  
  
## Requisitos  
 **Encabezado:** \<locale\>  
  
 **Espacio de nombres:** std