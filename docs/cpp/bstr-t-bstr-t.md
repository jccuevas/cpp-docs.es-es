---
title: "_bstr_t::_bstr_t | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_bstr_t::_bstr_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_bstr_t (clase)"
  - "_bstr_t (método)"
  - "BSTR (objeto)"
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::_bstr_t
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Construye un objeto `_bstr_t`.  
  
## Sintaxis  
  
```  
_bstr_t( ) throw( );   
_bstr_t(  
   const _bstr_t& s1   
) throw( );  
_bstr_t(  
   const char* s2   
);  
_bstr_t(  
   const wchar_t* s3   
);  
_bstr_t(  
   const _variant_t& var   
);  
_bstr_t(  
   BSTR bstr,  
   bool fCopy   
);  
```  
  
#### Parámetros  
 `s1`  
 Objeto `_bstr_t` que se va a copiar.  
  
 `s2`  
 Cadena multibyte.  
  
 `s3`  
 Cadena Unicode.  
  
 `var`  
 Objeto [\_variant\_t](../cpp/variant-t-class.md).  
  
 `bstr`  
 Objeto `BSTR` existente.  
  
 `fCopy`  
 Si es `false`, el argumento `bstr` se adjunta al nuevo objeto sin crear una copia mediante una llamada a `SysAllocString`.  
  
## Comentarios  
 En la siguiente tabla se describen los constructores `_bstr_t`.  
  
|Constructor|Descripción|  
|-----------------|-----------------|  
|`_bstr_t( )`|Construye un objeto `_bstr_t` predeterminado que encapsula un objeto `BSTR` null.|  
|`_bstr_t( _bstr_t&`  `s1`  `)`|Construye un objeto `_bstr_t` como copia de otro.<br /><br /> Se trata de una copia *superficial*, que incrementa el recuento de referencias del objeto `BSTR` encapsulado, en lugar de crear uno nuevo.|  
|`_bstr_t( char*`  `s2`  `)`|Construye un objeto `_bstr_t` mediante una llamada a `SysAllocString` para crear un nuevo objeto `BSTR` y, a continuación, lo encapsula.<br /><br /> Este constructor realiza primero una conversión de multibyte a Unicode.|  
|`_bstr_t( wchar_t*`  `s3`  `)`|Construye un objeto `_bstr_t` mediante una llamada a `SysAllocString` para crear un nuevo objeto `BSTR` y, a continuación, lo encapsula.|  
|`_bstr_t( _variant_t&`  `var`  `)`|Construye un objeto `_bstr_t` a partir de un objeto `_variant_t`: primero recupera un objeto `BSTR` del objeto VARIANT encapsulado.|  
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|Construye un objeto `_bstr_t` a partir de un objeto `BSTR` existente \(en lugar de una cadena `wchar_t*`\).  Si `fCopy` es false, el objeto `BSTR` proporcionado se adjunta al nuevo objeto sin crear una nueva copia con `SysAllocString`.<br /><br /> Las funciones contenedoras usan este constructor en los encabezados de la biblioteca de tipos para encapsular y tomar la propiedad de un objeto `BSTR` devuelto por un método de interfaz.|  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_bstr\_t \(Clase\)](../cpp/bstr-t-class.md)   
 [\_variant\_t \(Clase\)](../cpp/variant-t-class.md)