---
title: basic_stringstream (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sstream/std::basic_stringstream
- sstream/std::basic_stringstream::allocator_type
- sstream/std::basic_stringstream::rdbuf
- sstream/std::basic_stringstream::str
dev_langs: C++
helpviewer_keywords:
- std::basic_stringstream [C++]
- std::basic_stringstream [C++], allocator_type
- std::basic_stringstream [C++], rdbuf
- std::basic_stringstream [C++], str
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eabc994dc5792a5fa896a1d87f09c0ad511d91f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="basicstringstream-class"></a>basic_stringstream (Clase)
Describe un objeto que controla la inserción y la extracción de elementos y objetos codificados usando un búfer de flujo de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>  
class basic_stringstream : public basic_iostream<Elem, Tr>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Alloc`  
 Clase de asignador.  
  
 `Elem`  
 Tipo de elemento básico de la cadena.  
  
 *Tr*  
 Rasgos de caracteres especializados en el elemento básico de la cadena.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla describe un objeto que controla la inserción y extracción de elementos y objetos codificados mediante el uso de un búfer de flujo de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>, con elementos de tipo **Elem**, cuyos rasgos de caracteres están determinados por la clase **Tr** y cuyos elementos están asignados mediante un asignador de clase `Alloc`. El objeto almacena un objeto de clase basic_stringbuf< **Elem**, **Tr**, `Alloc`>.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[basic_stringstream](#basic_stringstream)|Construye un objeto de tipo `basic_stringstream`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|El tipo es un sinónimo del parámetro de plantilla `Alloc`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[rdbuf](#rdbuf)|Devuelve la dirección del búfer de flujo almacenado de tipo `pointer` a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|  
|[str](#str)|Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<sstream>  
  
 **Espacio de nombres:** std  
  
##  <a name="allocator_type"></a>  basic_stringstream::allocator_type  
 El tipo es un sinónimo del parámetro de plantilla `Alloc`.  
  
```  
typedef Alloc allocator_type;  
```  
  
##  <a name="basic_stringstream"></a>  basic_stringstream::basic_stringstream  
 Construye un objeto de tipo `basic_stringstream`.  
  
```  
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Mode`  
 Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `str`  
 Objeto de tipo `basic_string`.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor inicializa la clase base al llamar a [basic_iostream](../standard-library/basic-iostream-class.md)( **sb**), donde **sb** es el objeto almacenado de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>. También inicializa **sb** al llamar a basic_stringbuf< **Elem**, **Tr**, `Alloc`>( `_Mode`).  
  
 El segundo constructor inicializa la clase base al llamar a basic_iostream( **sb**). También inicializa **sb** al llamar a basic_stringbuf< **Elem**, **Tr**, `Alloc`>(_ *Str*, `_Mode`).  
  
##  <a name="rdbuf"></a>  basic_stringstream::rdbuf  
 Devuelve la dirección del búfer de flujo almacenado de tipo **pointer** a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.  
  
```  
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La dirección del búfer de flujo almacenado de tipo **pointer** a basic_stringbuf< **Elem**, **Tr**, `Alloc`>.  
  
### <a name="example"></a>Ejemplo  
  Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo de uso de `rdbuf`.  
  
##  <a name="str"></a>  basic_stringstream::str  
 Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.  
  
```  
basic_string<Elem, Tr, Alloc> str() const;

 
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Newstr`  
 La nueva cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un objeto de clase [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`>, cuya secuencia controlada es una copia de la secuencia controlada por **\*this**.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro devuelve [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). La segunda función miembro llama a `rdbuf` -> **str**(`_Newstr`).  
  
### <a name="example"></a>Ejemplo  
  Vea [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str) para obtener un ejemplo que usa **str**.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)

