---
title: ostrstream (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
dev_langs: C++
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 42b0786a140cf9657257d7f79a225a0473115282
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ostrstream-class"></a>ostrstream (Clase)
Describe un objeto que controla la inserción de objetos codificados y elementos en un búfer de secuencia de clase [strstreambuf](../standard-library/strstreambuf-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```
class ostrstream : public ostream
```  
  
## <a name="remarks"></a>Comentarios  
 El objeto almacena un objeto de clase `strstreambuf`.  
  
> [!NOTE]
>  Esta clase está en desuso. Considere el uso de [ostringstream](../standard-library/sstream-typedefs.md#ostringstream) o [wostringstream](../standard-library/sstream-typedefs.md#wostringstream) en su lugar.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[ostrstream](#ostrstream)|Construye un objeto de tipo `ostrstream`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[freeze](#freeze)|Hace que un búfer de secuencia no esté disponible a través de las operaciones de búfer de secuencia.|  
|[pcount](#pcount)|Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.|  
|[rdbuf](#rdbuf)|Devuelve un puntero al objeto `strstreambuf` asociado de la secuencia.|  
|[str](#str)|Llama a [freeze](../standard-library/strstreambuf-class.md#freeze) y, después, devuelve un puntero al principio de la secuencia controlada.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<strstream>  
  
 **Espacio de nombres:** std  
  
##  <a name="freeze"></a> ostrstream::freeze  
 Hace que un búfer de secuencia no esté disponible a través de las operaciones de búfer de secuencia.  
  
```
void freeze(bool _Freezeit = true);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Freezeit`  
 Un `bool` que indica si quiere que la secuencia se detenga.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro llama a [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).  
  
### <a name="example"></a>Ejemplo  
  Vea [strstream::freeze](../standard-library/strstreambuf-class.md#freeze) para obtener un ejemplo que usa **freeze**.  
  
##  <a name="ostrstream"></a> ostrstream::ostrstream  
 Construye un objeto de tipo `ostrstream`.  
  
```
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptr`  
 El búfer.  
  
 `count`  
 El tamaño del búfer en bytes.  
  
 `_Mode`  
 El modo de entrada y salida del búfer. Vea [ios_base::openmode](../standard-library/ios-base-class.md#openmode) para obtener más información.  
  
### <a name="remarks"></a>Comentarios  
 Los dos constructores inicializan la clase base mediante una llamada a [ostream](../standard-library/ostream-typedefs.md#ostream)( **sb**), donde **sb** es el objeto almacenado de la clase [strstreambuf](../standard-library/strstreambuf-class.md). El primer constructor inicializa también **sb** mediante una llamada a `strstreambuf`. El segundo constructor inicializa la clase base de una de estas dos maneras:  
  
-   Si `_Mode` & **ios_base::app**== 0, entonces `ptr` debe designar el primer elemento de una matriz de elementos `count` y el constructor llama a `strstreambuf`( `ptr`, `count`, `ptr`).  
  
-   De lo contrario, `ptr` debe designar el primer elemento de una matriz de elementos count que contiene una cadena de C cuyo primer elemento está designado por `ptr`, y el constructor llama a `strstreambuf`( `ptr`, `count`, `ptr` + `strlen`( `ptr`) ).  
  
##  <a name="pcount"></a> ostrstream::pcount  
 Devuelve un recuento del número de elementos que se escriben en la secuencia controlada.  
  
```
streamsize pcount() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos que se escriben en la secuencia controlada.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).  
  
### <a name="example"></a>Ejemplo  
  Vea [strstream::pcount](../standard-library/strstreambuf-class.md#pcount) para obtener un ejemplo que usa `pcount`.  
  
##  <a name="rdbuf"></a> ostrstream::rdbuf  
 Devuelve un puntero al objeto strstreambuf asociado del flujo.  
  
```
strstreambuf *rdbuf() const
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto strstreambuf asociado del flujo.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve la dirección del búfer de secuencia almacenado de tipo **pointer** a [strstreambuf](../standard-library/strstreambuf-class.md).  
  
### <a name="example"></a>Ejemplo  
  Vea [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) para obtener un ejemplo que usa `rdbuf`.  
  
##  <a name="str"></a> ostrstream::str  
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
 [ostream](../standard-library/ostream-typedefs.md#ostream)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)



