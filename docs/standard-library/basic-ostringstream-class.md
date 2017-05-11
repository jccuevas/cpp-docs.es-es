---
title: basic_ostringstream (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- basic_ostringstream
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
dev_langs:
- C++
helpviewer_keywords:
- basic_ostringstream class
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 96a5b0b6620810a336240e1adf06529c87bcb1b3
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="basicostringstream-class"></a>basic_ostringstream (Clase)
Describe un objeto que controla la inserción de objetos codificados y elementos en un búfer de flujo de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>  
class basic_ostringstream : public basic_ostream<Elem, Tr>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Alloc`  
 Clase de asignador.  
  
 `Elem`  
 Tipo de elemento básico de la cadena.  
  
 *Tr*  
 Rasgos de caracteres especializados en el elemento básico de la cadena.  
  
## <a name="remarks"></a>Comentarios  
 La clase describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de flujo, con elementos de tipo **Elem**, cuyos rasgos de caracteres están determinados por la clase **Tr** y cuyos elementos están asignados por un asignador de clase `Alloc`. El objeto almacena un objeto de clase basic_stringbuf< **Elem**, **Tr**, `Alloc`>.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[basic_ostringstream](#basic_ostringstream)|Construye un objeto de tipo `basic_ostringstream`.|  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
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
  
##  <a name="allocator_type"></a>  basic_ostringstream::allocator_type  
 El tipo es un sinónimo del parámetro de plantilla `Alloc`.  
  
```  
typedef Alloc allocator_type;  
```  
  
##  <a name="basic_ostringstream"></a>  basic_ostringstream::basic_ostringstream  
 Construye un objeto de tipo basic_ostringstream.  
  
```  
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Mode`  
 Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `str`  
 Objeto de tipo `basic_string`.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor inicializa la clase base al llamar a [basic_ostream](../standard-library/basic-ostream-class.md)(**sb**), donde **sb** es el objeto almacenado de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>. También inicializa **sb** al llamar a basic_stringbuf< **Elem**, **Tr**, `Alloc`>(`_Mode` &#124; `ios_base::out`).  
  
 El segundo constructor inicializa la clase base al llamar a basic_ostream(**sb**). También inicializa **sb** al llamar a basic_stringbuf< **Elem**, **Tr**, `Alloc`>(_ *Str*, `_Mode` &#124; `ios_base::out`).  
  
##  <a name="rdbuf"></a>  basic_ostringstream::rdbuf  
 Devuelve la dirección del búfer de flujo almacenado de tipo **pointer** a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.  
  
```  
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La dirección del búfer de flujo almacenado de tipo **pointer** a basic_stringbuf< **Elem**, **Tr**, `Alloc`>.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve la dirección del búfer de flujo almacenado de tipo **pointer** a basic_stringbuf< **Elem**, **Tr**, `Alloc`>.  
  
### <a name="example"></a>Ejemplo  
  Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo de uso de `rdbuf`.  
  
##  <a name="str"></a>  basic_ostringstream::str  
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


