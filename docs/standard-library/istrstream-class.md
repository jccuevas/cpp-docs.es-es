---
title: Clase istrstream | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istrstream
- strstream/std::istrstream::rdbuf
- strstream/std::istrstream::str
dev_langs:
- C++
helpviewer_keywords:
- istrstream class
ms.assetid: c2d41c75-bd2c-4437-bd77-5939ce1b97af
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: 528634e98da7f57ee915124d38f20277495efcdb
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="istrstream-class"></a>istrstream (Clase)
Describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de flujo de clase [strstreambuf](../standard-library/strstreambuf-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```
class istrstream : public istream
```  
  
## <a name="remarks"></a>Comentarios  
 El objeto almacena un objeto de clase `strstreambuf`.  
  
> [!NOTE]
>  Esta clase está en desuso. Considere el uso de [istringstream](../standard-library/sstream-typedefs.md#istringstream) o [wistringstream](../standard-library/sstream-typedefs.md#wistringstream) en su lugar.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[istrstream](#istrstream)|Construye un objeto de tipo `istrstream`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[rdbuf](#rdbuf)|Devuelve un puntero al objeto `strstreambuf` asociado de la secuencia.|  
|[str](#str)|Llama a [freeze](../standard-library/strstreambuf-class.md#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<strstream>  
  
 **Espacio de nombres:** std  
  
##  <a name="istrstream"></a>  istrstream::istrstream  
 Construye un objeto de tipo `istrstream`.  
  
```
explicit istrstream(
    const char* ptr);

explicit istrstream(
    char* ptr);

istrstream(
    const char* ptr,
    streamsize count);

istrstream(
    char* ptr,
    int count);
```  
  
### <a name="parameters"></a>Parámetros  
 `count`  
 Longitud del búfer (`ptr`).  
  
 `ptr`  
 Contenido con el que se inicializa el búfer.  
  
### <a name="remarks"></a>Comentarios  
 Todos los constructores inicializan la clase base mediante una llamada a [istream](../standard-library/istream-typedefs.md#istream)(**sb**), donde **sb** es el objeto almacenado de la clase [strstreambuf](../standard-library/strstreambuf-class.md). Los dos primeros constructores también inicializan **sb** mediante una llamada a `strstreambuf`( ( **const**`char` \*) `ptr`, 0 ). Los dos constructores restantes llaman a `strstreambuf`( ( **const**`char` *) `ptr`, `count` ).  
  
##  <a name="rdbuf"></a>  istrstream::rdbuf  
 Devuelve un puntero al objeto strstreambuf asociado del flujo.  
  
```
strstreambuf *rdbuf() const
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto strstreambuf asociado del flujo.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve la dirección del búfer de flujo almacenado de tipo pointer a [strstreambuf](../standard-library/strstreambuf-class.md).  
  
### <a name="example"></a>Ejemplo  
  Vea [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) para obtener un ejemplo del uso de `rdbuf`.  
  
##  <a name="str"></a>  istrstream::str  
 Llama a [freeze](../standard-library/strstreambuf-class.md#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.  
  
```
char *str();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al principio de la secuencia controlada.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).  
  
### <a name="example"></a>Ejemplo  
  Vea [strstream::str](../standard-library/strstreambuf-class.md#str) para obtener un ejemplo del uso de **str**.  
  
## <a name="see-also"></a>Vea también  
 [istream](../standard-library/istream-typedefs.md#istream)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)




