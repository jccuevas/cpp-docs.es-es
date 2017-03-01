---
title: basic_ostream (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::basic_ostream
- std.basic_ostream
- ostream/std::basic_ostream
- basic_ostream
dev_langs:
- C++
helpviewer_keywords:
- basic_ostream class
ms.assetid: 5baadc65-b662-4fab-8c9f-94457c58cda1
caps.latest.revision: 24
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 73cde54e382bb04b82739239bd0f07142c5b3321
ms.lasthandoff: 02/24/2017

---
# <a name="basicostream-class"></a>basic_ostream (Clase)
Esta clase de plantilla describe un objeto que controla la inserción de elementos y objetos codificados en un búfer de flujo con elementos de tipo **Elem**, también conocidos como [char_type](../standard-library/basic-ios-class.md#basic_ios__char_type), cuyos rasgos de caracteres están determinados por la clase **Tr**, también conocida como [traits_type](../standard-library/basic-ios-class.md#basic_ios__traits_type).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_ostream : virtual public basic_ios<Elem, Tr>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Elem`  
 Objeto `char_type`.  
  
 `Tr`  
 El carácter `traits_type`.  
  
## <a name="remarks"></a>Comentarios  
 La mayoría de las funciones miembro que sobrecargan [operator<<](#basic_ostream__operator_lt__lt_) son funciones de salida con formato. Siguen el patrón:  
  
```  
iostate state = goodbit;  
const sentry ok(*this);

if (ok)  
 {try  
 {<convert and insert elements  
    accumulate flags in state> }  
    catch (...)  
 {try  
 {setstate(badbit);

}  
    catch (...)  
 {}  
    if ((exceptions()& badbit) != 0)  
    throw; }}  
width(0);
// Except for operator<<(Elem)  
setstate(state);

return (*this);
```  
  
 Otras dos funciones miembro son funciones de salida sin formato. Siguen el patrón:  
  
```  
iostate state = goodbit;  
const sentry ok(*this);

if (!ok)  
    state |= badbit;  
else  
 {try  
 {<obtain and insert elements  
    accumulate flags in state> }  
    catch (...)  
 {try  
 {setstate(badbit);

}  
    catch (...)  
 {}  
    if ((exceptions()& badbit) != 0)  
    throw; }}  
setstate(state);

return (*this);
```  
  
 Ambos grupos de funciones llaman a [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)**(badbit)** si detectan un error al insertar elementos.  
  
 Un objeto de clase basic_istream\< **Elem**, **Tr**> solo almacena un objeto base público virtual de clase [basic_ios](../standard-library/basic-ios-class.md)**\<Elem**, **Tr>**.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [basic_ofstream (Clase)](../standard-library/basic-ofstream-class.md) para obtener más información sobre los flujos de salida.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[basic_ostream](#basic_ostream__basic_ostream)|Construye un objeto `basic_ostream`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[flush](#basic_ostream__flush)|Vacía el búfer.|  
|[put](#basic_ostream__put)|Coloca un carácter en una secuencia.|  
|[seekp](#basic_ostream__seekp)|Restablece la posición en el flujo de salida.|  
|[sentry](#basic_ostream__sentry)|La clase anidada describe un objeto cuya declaración estructura las funciones de salida con y sin formato.|  
|[swap](#basic_ostream__operator_eq)|Cambia los valores de este objeto `basic_ostream` por los del objeto `basic_ostream` proporcionado.|  
|[tellp](#basic_ostream__tellp)|Notifica la posición en el flujo de salida.|  
|[write](#basic_ostream__write)|Coloca los caracteres en una secuencia.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator=](#basic_ostream_operator_eq)|Asigna el valor del parámetro de objeto `basic_ostream` a este objeto.|  
|[operator<<](#basic_ostream_operator_lt_lt_)|Escribe en la secuencia.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<ostream>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namebasicostreambasicostreama--basicostreambasicostream"></a><a name="basic_ostream__basic_ostream"></a>  basic_ostream::basic_ostream  
 Construye un objeto `basic_ostream`.  
  
```  
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,  
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` strbuf`  
 Objeto de tipo [basic_streambuf](../standard-library/basic-streambuf-class.md).  
  
 `_Isstd`  
 `true` si se trata de un flujo estándar; de lo contrario, `false`.  
  
 ` right`  
 Referencia a un valor R a un objeto de tipo `basic_ostream`.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor inicializa la clase base al llamar a [init](../standard-library/basic-ios-class.md#basic_ios__init)(` strbuf`). El segundo constructor inicializa la clase base al llamar a [basic_ios::move](../standard-library/basic-ios-class.md#basic_ios__move)`(`` right``)`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream__basic_ofstream) para obtener más información sobre los flujos de salida.  
  
##  <a name="a-namebasicostreamflusha--basicostreamflush"></a><a name="basic_ostream__flush"></a>  basic_ostream::flush  
 Vacía el búfer.  
  
```  
basic_ostream<Elem, Tr>& flush();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto basic_ostream.  
  
### <a name="remarks"></a>Comentarios  
 Si [rdbuf](../standard-library/basic-ios-class.md#basic_ios__rdbuf) no es un puntero nulo, la función llama a **rdbuf->**[pubsync](../standard-library/basic-streambuf-class.md#basic_streambuf__pubsync). Si eso devuelve -1, la función llama a [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**badbit**). Devuelve **\*this**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_ostream_flush.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "test";  
   cout.flush();  
}  
```  
  
```Output  
test  
```  
  
##  <a name="a-namebasicostreamoperatorltlta--basicostreamoperatorltlt"></a><a name="basic_ostream_operator_lt_lt_"></a>  basic_ostream::operator&lt;&lt;  
 Escribe en la secuencia.  
  
```  
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& (* Pfn)(basic_ostream<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(
    ios_base& (* Pfn)(ios_base&));

basic_ostream<Elem, Tr>& operator<<(
    basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
basic_ostream<Elem, Tr>& operator<<(bool val);
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int __w64  val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long __w64  val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```  
  
### <a name="parameters"></a>Parámetros  
 `Pfn`  
 Puntero de función.  
  
 ` strbuf`  
 Puntero a un objeto **stream_buf**.  
  
 ` val`  
 Elemento que se va a escribir en el flujo.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto basic_ostream.  
  
### <a name="remarks"></a>Comentarios  
 El encabezado `<ostream>` también define varios operadores de inserción globales. Para más información, vea [operator<< (\<ostream>)](../standard-library/ostream-operators.md#operator_lt__lt_).  
  
 La primera función miembro garantiza que una expresión con el formato **ostr << endl** llame a [endl](../standard-library/ostream-functions.md#endl)**(ostr)** y luego devuelva **\*this**. Las funciones segunda y tercera garantizan que los demás manipuladores, como [hex](../standard-library/ios-functions.md#hex), se comporten de forma similar. Las funciones restantes son todas funciones de salida con formato.  
  
 La función  
  
```  
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```  
  
 extrae elementos de ` strbuf` si ` strbuf` no es un puntero nulo y los inserta. La extracción se detiene al final del archivo o si una extracción inicia una excepción (que se vuelve a iniciar). También se detiene, sin extraer el elemento en cuestión, si se produce un error en una inserción. Si la función no inserta ningún elemento, o si una extracción inicia una excepción, la función llama a [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**failbit**). En cualquier caso, la función devuelve **\*this**.  
  
 La función  
  
```  
basic_ostream<Elem, Tr>& operator<<(bool val);
```  
  
 convierte _`Val` en un campo booleano y lo inserta al llamar a [use_facet](../standard-library/basic-filebuf-class.md#basic_filebuf__open)**<num_put\<Elem, OutIt>**`(`[getloc](../standard-library/ios-base-class.md#ios_base__getloc)). [put](#basic_ostream__put)(**OutIt**([rdbuf](../standard-library/basic-ios-class.md#basic_ios__rdbuf)), **\*this**, `getloc`, **val**). Aquí, **OutIt** se define como [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)**\<Elem, Tr>**. La función devuelve **\*this**.  
  
 Las funciones  
  
```  
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```  
  
 convierten ` val` en un campo numérico y lo insertan al llamar a **use_facet<num_put\<Elem, OutIt>**(`getloc`). **put**(**OutIt**(`rdbuf`), **\*this**, `getloc`, **val**). Aquí, **OutIt** se define como **ostreambuf_iterator\<Elem, Tr>**. La función devuelve **\*this**.  
  
 Las funciones  
  
```  
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```  
  
 convierten `val` en un campo numérico y lo insertan al llamar a **use_facet<num_put\<Elem, OutIt>**(`getloc`)**. put**(**OutIt**(`rdbuf`), **\*this**, `getloc`, **val**). Aquí, **OutIt** se define como **ostreambuf_iterator\<Elem, Tr>**. La función devuelve **\*this**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_ostream_op_write.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string.h>  
  
using namespace std;  
  
ios_base& hex2( ios_base& ib )  
{  
   ib.unsetf( ios_base::dec );  
   ib.setf( ios_base::hex );  
   return ib;  
}  
  
basic_ostream<char, char_traits<char> >& somefunc(basic_ostream<char, char_traits<char> > &i)
{
    if (i == cout)
    {
        i << "i is cout" << endl;
    }
    return i;
}

class CTxtStreambuf : public basic_streambuf< char, char_traits< char > >
{
public:
    CTxtStreambuf(char *_pszText)
    {
        pszText = _pszText;
        setg(pszText, pszText, pszText + strlen(pszText));
    };
    char *pszText;
};

int main()
{
    cout << somefunc;
    cout << 21 << endl;

    hex2(cout);
    cout << 21 << endl;

    CTxtStreambuf f("text in streambuf");
    cout << &f << endl;
}
```  
  
##  <a name="a-namebasicostreamoperatoreqa--basicostreamoperator"></a><a name="basic_ostream__operator_eq"></a>  basic_ostream::operator=  
 Asigna valores del parámetro de objeto `basic_ostream` proporcionado a este objeto.  
  
```  
basic_ostream& operator=(basic_ostream&& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 Referencia `rvalue` a un objeto `basic_ostream`.  
  
### <a name="remarks"></a>Comentarios  
 El operador miembro llama a swap `(`` right``)`.  
  
##  <a name="a-namebasicostreamputa--basicostreamput"></a><a name="basic_ostream__put"></a>  basic_ostream::put  
 Coloca un carácter en una secuencia.  
  
```  
basic_ostream<Elem, Tr>& put(char_type _Ch);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Ch`  
 Un carácter.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto basic_ostream.  
  
### <a name="remarks"></a>Comentarios  
 La función de salida sin formato inserta el elemento `_Ch`. Devuelve **\*this**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_ostream_put.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout.put( 'v' );  
   cout << endl;  
   wcout.put( L'l' );  
}  
```  
  
```Output  
v  
l  
```  
  
##  <a name="a-namebasicostreamseekpa--basicostreamseekp"></a><a name="basic_ostream__seekp"></a>  basic_ostream::seekp  
 Restablece la posición en el flujo de salida.  
  
```  
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Pos`  
 Posición en el flujo.  
  
 `_Off`  
 Desplazamiento en relación con `_Way`.  
  
 `_Way`  
 Una de las enumeraciones [ios_base::seekdir](../standard-library/ios-base-class.md#ios_base__seekdir).  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto basic_ostream.  
  
### <a name="remarks"></a>Comentarios  
 Si [fail](../standard-library/basic-ios-class.md#basic_ios__fail) es **False**, la primera función miembro llama a **newpos =** [rdbuf](../standard-library/basic-ios-class.md#basic_ios__rdbuf)**->** [pubseekpos](../standard-library/basic-streambuf-class.md#basic_streambuf__pubseekpos)(_*Pos*), para algunos `pos_type` el objeto temporal **newpos**. Si **fail** es False, la segunda función llama a **newpos = rdbuf->** [pubseekoff](../standard-library/basic-streambuf-class.md#basic_streambuf__pubseekoff)(*_Off, _Way*). En cualquier caso, si (`off_type`)**newpos ==** (`off_type`)(-1) (se produce un error en la operación de posicionamiento), la función llama a **istr.**[setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**failbit**). Ambas funciones devuelven **\*this**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_ostream_seekp.cpp  
// compile with: /EHsc  
#include <fstream>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    ofstream x("basic_ostream_seekp.txt");  
    streamoff i = x.tellp();  
    cout << i << endl;  
    x << "testing";  
    i = x.tellp();  
    cout << i << endl;  
    x.seekp(2);   // Put char in third char position in file  
    x << " ";  
  
    x.seekp(2, ios::end);   // Put char two after end of file  
    x << "z";  
}  
```  
  
```Output  
0  
7  
```  
  
##  <a name="a-namebasicostreamsentrya--basicostreamsentry"></a><a name="basic_ostream__sentry"></a>  basic_ostream::sentry  
 La clase anidada describe un objeto cuya declaración estructura las funciones de salida con y sin formato.  
  
class sentry {  
   public:  
   explicit sentry(basic_ostream\<Elem, Tr>& _Ostr); operator bool() const; ~sentry(); };  
  
### <a name="remarks"></a>Comentarios  
 La clase anidada describe un objeto cuya declaración estructura las funciones de salida con y sin formato. Si **ostr.**[good](../standard-library/basic-ios-class.md#basic_ios__good) es **True** y **ostr.**[tie](../standard-library/basic-ios-class.md#basic_ios__tie) no es un puntero nulo, el constructor llama a **ostr.tie->**[flush](#basic_ostream__flush). El constructor almacena el valor devuelto por **ostr.good** en **status**. Una llamada posterior a **operator bool** devuelve este valor almacenado.  
  
 Si `uncaught_exception` devuelve **False** y [flags](../standard-library/ios-base-class.md#ios_base__flags) **&** [unitbuf](../standard-library/ios-functions.md#unitbuf) es distinto de cero, el destructor llama a [flush](#basic_ostream__flush).  
  
##  <a name="a-namebasicostreamswapa--basicostreamswap"></a><a name="basic_ostream__swap"></a>  basic_ostream::swap  
 Cambia los valores de este objeto `basic_ostream` por los del objeto `basic_ostream` proporcionado.  
  
```  
void swap(basic_ostream& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 Referencia a un objeto `basic_ostream`.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro llama a [basic_ios::swap](../standard-library/basic-ios-class.md#basic_ios__swap)`(`` right``)` para cambiar el contenido de este objeto por el de ` right`.  
  
##  <a name="a-namebasicostreamtellpa--basicostreamtellp"></a><a name="basic_ostream__tellp"></a>  basic_ostream::tellp  
 Notifica la posición en el flujo de salida.  
  
```  
pos_type tellp();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Posición en el flujo de salida.  
  
### <a name="remarks"></a>Comentarios  
 Si [fail](../standard-library/basic-ios-class.md#basic_ios__fail) es **False**, la función miembro devuelve [rdbuf](../standard-library/basic-ios-class.md#basic_ios__rdbuf)**->** [pubseekoff](../standard-library/basic-streambuf-class.md#basic_streambuf__pubseekoff)(0, `cur`, **in**). De lo contrario, devuelve `pos_type`(-1).  
  
### <a name="example"></a>Ejemplo  
  Vea [seekp](#basic_ostream__seekp) para obtener un ejemplo de uso de `tellp`.  
  
##  <a name="a-namebasicostreamwritea--basicostreamwrite"></a><a name="basic_ostream__write"></a>  basic_ostream::write  
 Coloca caracteres en un flujo.  
  
```  
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```  
  
### <a name="parameters"></a>Parámetros  
 ` count`  
 Recuento de caracteres que se van a colocar en el flujo.  
  
 ` str`  
 Caracteres que se van a colocar en el flujo.  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia al objeto basic_ostream.  
  
### <a name="remarks"></a>Comentarios  
 La [función de salida sin formato](../standard-library/basic-ostream-class.md) inserta la secuencia de ` count` elementos, empezando por ` str`.  
  
### <a name="example"></a>Ejemplo  
  Vea [streamsize](../standard-library/ios-typedefs.md#streamsize) para obtener un ejemplo de uso de `write`.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)


