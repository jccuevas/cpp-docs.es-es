---
title: basic_istringstream (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sstream/std::basic_istringstream
- sstream/std::basic_istringstream::allocator_type
- sstream/std::basic_istringstream::rdbuf
- sstream/std::basic_istringstream::str
- sstream/std::basic_istringstream::swap
dev_langs: C++
helpviewer_keywords:
- std::basic_istringstream [C++]
- std::basic_istringstream [C++], allocator_type
- std::basic_istringstream [C++], rdbuf
- std::basic_istringstream [C++], str
- std::basic_istringstream [C++], swap
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0f5ba9776b27ec98967f64d3c2bfb114c62c36fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="basicistringstream-class"></a>basic_istringstream (Clase)
Describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de flujo de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>  
class basic_istringstream : public basic_istream<Elem, Tr>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Alloc`  
 Clase de asignador.  
  
 `Elem`  
 Tipo de elemento básico de la cadena.  
  
 *Tr*  
 Rasgos de caracteres especializados en el elemento básico de la cadena.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla describe un objeto que controla la extracción de elementos y objetos codificados desde un búfer de flujo de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>, con elementos de tipo **Elem**, cuyos rasgos de caracteres están determinados por la clase **Tr** y cuyos elementos se asignan mediante un asignador de clase `Alloc`. El objeto almacena un objeto de clase basic_stringbuf< **Elem**, **Tr**, `Alloc`>.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[basic_istringstream](#basic_istringstream)|Construye un objeto de tipo `basic_istringstream`.|  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|El tipo es un sinónimo del parámetro de plantilla `Alloc`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[rdbuf](#rdbuf)|Devuelve la dirección del búfer de flujo almacenado de tipo `pointer` a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|  
|[str](#str)|Establece u obtiene el texto en un búfer de cadena sin cambiar la posición de escritura.|  
|[swap](#swap)|Intercambia los valores de este objeto `basic_istringstream` con los del objeto proporcionado.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator=](#op_eq)|Asigna los valores a este objeto `basic_istringstream` desde el parámetro de objeto.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<sstream>  
  
 **Espacio de nombres:** std  
  
##  <a name="allocator_type"></a>  basic_istringstream::allocator_type  
 El tipo es un sinónimo del parámetro de plantilla `Alloc`.  
  
```  
typedef Alloc allocator_type;  
```  
  
##  <a name="basic_istringstream"></a>  basic_istringstream::basic_istringstream  
 Construye un objeto de tipo `basic_istringstream`.  
  
```  
explicit basic_istringstream(
    ios_base::openmode _Mode = ios_base::in);

explicit basic_istringstream(
    const basic_string<Elem, Tr, Alloc>& str,  
    ios_base::openmode _Mode = ios_base::in);

basic_istringstream(
    basic_istringstream&& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Mode`  
 Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `str`  
 Objeto de tipo `basic_string`.  
  
 `right`  
 Referencia a un valor R de un objeto `basic_istringstream`.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor inicializa la clase base al llamar a [basic_istream](../standard-library/basic-istream-class.md)(`sb`), donde `sb` es el objeto almacenado de clase [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>. También inicializa `sb` al llamar a `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>(`_Mode` &#124; `ios_base::in`).  
  
 El segundo constructor inicializa la clase base al llamar a `basic_istream(sb)`. También inicializa `sb` al llamar a `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>(`str`, `_Mode` &#124; `ios_base::in`).  
  
 El tercer constructor inicializa el objeto con el contenido de `right`, tratado como una referencia a un valor R.  
  
##  <a name="op_eq"></a>  basic_istringstream::operator=  
 Asigna los valores a este objeto `basic_istringstream` desde el parámetro de objeto.  
  
```  
basic_istringstream& operator=(basic_istringstream&& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Referencia a un valor R a un objeto `basic_istringstream`.  
  
### <a name="remarks"></a>Comentarios  
 Operador de miembro que reemplaza el contenido del objeto por el contenido de `right`, que se trata como asignación de movimiento de la referencia a un valor R.  
  
##  <a name="rdbuf"></a>  basic_istringstream::rdbuf  
 Devuelve la dirección del búfer de flujo almacenado de tipo **pointer** a [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.  
  
```  
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 La dirección del búfer de flujo almacenado de tipo **pointer** a basic_stringbuf< **Elem**, **Tr**, `Alloc`>.  
  
### <a name="example"></a>Ejemplo  
  Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo que usa `rdbuf`.  
  
##  <a name="str"></a>  basic_istringstream::str  
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
  
##  <a name="swap"></a>  basic_istringstream::swap  
 Intercambia los valores de dos objetos `basic_istringstream`.  
  
```  
void swap(basic_istringstream& right);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`right`|Referencia `lvalue` a un objeto `basic_istringstream`.|  
  
### <a name="remarks"></a>Comentarios  
 La función miembro intercambia los valores de este objeto y los valores de `right`.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)

