---
title: basic_ofstream (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- fstream/std::basic_ofstream
- fstream/std::basic_ofstream::close
- fstream/std::basic_ofstream::is_open
- fstream/std::basic_ofstream::open
- fstream/std::basic_ofstream::rdbuf
- fstream/std::basic_ofstream::swap
dev_langs: C++
helpviewer_keywords:
- std::basic_ofstream [C++]
- std::basic_ofstream [C++], close
- std::basic_ofstream [C++], is_open
- std::basic_ofstream [C++], open
- std::basic_ofstream [C++], rdbuf
- std::basic_ofstream [C++], swap
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 235bf7fc118f8752adefc61f5ed18ea01caec727
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="basicofstream-class"></a>basic_ofstream (Clase)
Describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de flujo de la clase [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, con elementos de tipo `Elem`, cuyos rasgos de caracteres están determinados por la clase `Tr`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Elem, class Tr = char_traits<Elem>>  
class basic_ofstream : public basic_ostream<Elem, Tr>
```  
  
#### <a name="parameters"></a>Parámetros  
 `Elem`  
 Elemento básico del búfer del archivo.  
  
 `Tr`  
 Rasgos del elemento básico del búfer del archivo (normalmente `char_traits`< `Elem`>).  
  
## <a name="remarks"></a>Comentarios  
 Cuando la especialización `wchar_t` de `basic_ofstream` escribe en el archivo, si el archivo se abre en modo de texto, escribirá una secuencia MBCS. La representación interna usará un búfer de caracteres `wchar_t`.  
  
 El objeto almacena un objeto de clase `basic_filebuf`< `Elem`, `Tr`>.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo de código se muestra cómo crear un objeto `basic_ofstream` y escribir texto en él.  
  
```  
// basic_ofstream_class.cpp  
// compile with: /EHsc  
#include <fstream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ofstream ofs("ofstream.txt");  
    if (!ofs.bad())  
    {  
        ofs << "Writing to a basic_ofstream object..." << endl;  
        ofs.close();  
    }  
}  
```  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[basic_ofstream](#basic_ofstream)|Crea un objeto del tipo `basic_ofstream`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[close](#close)|Cierra un archivo.|  
|[is_open](#is_open)|Determina si un archivo está abierto.|  
|[open](#open)|Abre un archivo.|  
|[rdbuf](#rdbuf)|Devuelve la dirección del búfer de secuencia almacenado.|  
|[swap](#swap)|Intercambia el contenido de este `basic_ofstream` con el contenido del `basic_ofstream` proporcionado.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator=](#op_eq)|Asigna el contenido de este objeto de secuencia. Se trata de una asignación de movimiento que implica un `rvalue reference` que no deja ninguna copia atrás.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<fstream>  
  
 **Espacio de nombres:** std  
  
##  <a name="basic_ofstream"></a>  basic_ofstream::basic_ofstream  
 Crea un objeto del tipo `basic_ofstream`.  
  
```
basic_ofstream();

explicit basic_ofstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ofstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_ofstream(
    basic_ofstream&& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Filename`  
 Nombre del archivo que se va a abrir.  
  
 `_Mode`  
 Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `_Prot`  
 Protección predeterminada de apertura del archivo, equivalente al parámetro `shflag` de [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).  
  
 `right`  
 Referencia a un valor R al objeto `basic_ofstream` que se usa para inicializar este objeto `basic_ofstream`.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor inicializa la clase base al llamar a [basic_ostream](../standard-library/basic-ostream-class.md)(**sb**), donde **sb** es el objeto almacenado de clase [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>. También inicializa **sb** al llamar a `basic_filebuf`< `Elem`, `Tr`>.  
  
 El segundo y el tercer constructor inicializan la clase base al llamar a `basic_ostream`(**sb**). También inicializa **sb** al llamar a `basic_filebuf`< `Elem`, `Tr`> y luego a **sb**. [open](../standard-library/basic-filebuf-class.md#open)(`_Filename`, `_Mode` &#124; `ios_base::out`). Si esta última función devuelve un puntero nulo, el constructor llama a [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**).  
  
 El cuarto constructor es una función de copia. Inicializa el objeto con el contenido de `right`, tratado como una referencia a un valor R.  
  
### <a name="example"></a>Ejemplo  
  En el siguiente ejemplo de código se muestra cómo crear un objeto `basic_ofstream` y escribir texto en él.  
  
```  
// basic_ofstream_ctor.cpp  
// compile with: /EHsc  
#include <fstream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ofstream ofs("C:\\ofstream.txt");  
    if (!ofs.bad())  
    {  
        ofs << "Writing to a basic_ofstream object..." << endl;  
        ofs.close();  
    }  
}  
```  
  
##  <a name="close"></a>  basic_ofstream::close  
 Cierra un archivo.  
  
```
void close();
```  
  
### <a name="remarks"></a>Comentarios  
 Las llamadas a funciones miembro [rdbuf](../standard-library/basic-ifstream-class.md#rdbuf)**->**[cerrar](../standard-library/basic-filebuf-class.md#close).  
  
### <a name="example"></a>Ejemplo  
  Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo que usa **close**.  
  
##  <a name="is_open"></a>  basic_ofstream::is_open  
 Indica si un archivo está abierto.  
  
```
bool is_open() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si el archivo está abierto; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [rdbuf](#rdbuf)  **->**  [is_open](../standard-library/basic-filebuf-class.md#is_open).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_ofstream_is_open.cpp  
// compile with: /EHsc  
#include <fstream>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   ifstream file;  
   // Open and close with a basic_filebuf  
   file.rdbuf( )->open( "basic_ofstream_is_open.txt", ios::in );  
   file.close( );  
   if (file.is_open())  
      cout << "it's open" << endl;  
   else  
      cout << "it's closed" << endl;  
}  
```  
  
##  <a name="open"></a>  basic_ofstream::open  
 Abre un archivo.  
  
```
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Filename`  
 Nombre del archivo que se va a abrir.  
  
 `_Mode`  
 Una de las enumeraciones de [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `_Prot`  
 Protección predeterminada de apertura del archivo, equivalente al parámetro `shflag` de [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).  
  
### <a name="remarks"></a>Comentarios  
 La función miembro llama a [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124; `ios_base::out`). Si esa función devuelve un puntero nulo, la función llama a [setstate](../standard-library/basic-ios-class.md#setstate)(**failbit**).  
  
### <a name="example"></a>Ejemplo  
  Vea [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) para obtener un ejemplo que usa **open**.  
  
##  <a name="op_eq"></a>  basic_ofstream::operator=  
 Asigna el contenido de este objeto de secuencia. Se trata de una asignación de movimiento que implica un `rvalue reference` que no deja ninguna copia atrás.  
  
```
basic_ofstream& operator=(basic_ofstream&& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Referencia a un valor R a un objeto `basic_ofstream`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `*this`.  
  
### <a name="remarks"></a>Comentarios  
 El operador de miembro reemplaza el contenido del objeto por el contenido de `right`, que se trata como referencia rvalue.  
  
##  <a name="rdbuf"></a>  basic_ofstream::rdbuf  
 Devuelve la dirección del búfer de secuencia almacenado.  
  
```
basic_filebuf<Elem, Tr> *rdbuf() const
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la dirección del búfer de secuencia almacenado.  
  
### <a name="example"></a>Ejemplo  
  Vea [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) para obtener un ejemplo que usa `rdbuf`.  
  
##  <a name="swap"></a>  basic_ofstream::swap  
 Intercambia el contenido de dos objetos `basic_ofstream`.  
  
```
void swap(basic_ofstream& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Referencia `lvalue` a otro objeto `basic_ofstream`.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro intercambia el contenido de este objeto por el contenido de `right`.  
  
## <a name="see-also"></a>Vea también  
 [basic_ostream (Clase)](../standard-library/basic-ostream-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)



