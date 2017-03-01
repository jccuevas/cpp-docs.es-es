---
title: basic_istream (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- basic_istream
- istream/std::basic_istream
- std::basic_istream
- std.basic_istream
dev_langs:
- C++
helpviewer_keywords:
- basic_istream class
ms.assetid: c7c27111-de6d-42b4-95a3-a7e65259bf17
caps.latest.revision: 21
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
translationtype: Machine Translation
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: 32308d4cd6a3cc1409f04958dde8dad9204718bc
ms.lasthandoff: 02/24/2017

---
# <a name="basicistream-class"></a>basic_istream (Clase)
Describe un objeto que controla la extracción de elementos y objetos codificados de un búfer de flujo con elementos de tipo `Elem`, también conocido como [char_type](../standard-library/basic-ios-class.md#basic_ios__char_type), cuyos rasgos de caracteres están determinados por la clase *Tr*, también conocida como [traits_type](../standard-library/basic-ios-class.md#basic_ios__traits_type).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_istream : virtual public basic_ios<Elem, Tr>  
```  
  
## <a name="remarks"></a>Comentarios  
 La mayoría de las funciones miembro que sobrecargan [operator>>](#basic_istream__operator_gt__gt_) son funciones de entrada con formato. Siguen el patrón:  
  
```cpp  
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{
    try
    {
        /*extract elements and convert
            accumulate flags in state.
            store a successful conversion*/
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);

return (*this);
```  
  
 Muchas otras funciones miembro son funciones de entrada sin formato. Siguen el patrón:  
  
```cpp  
iostate state = goodbit;
count = 0;    // the value returned by gcount  
const sentry ok(*this, true);

if (ok)
{
    try
    {
        /* extract elements and deliver
            count extracted elements in count
            accumulate flags in state */
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);
```  
  
 Ambos grupos de funciones llaman a [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**eofbit**) si encuentran el final del archivo al extraer los elementos.  
  
 Un objeto de clase `basic_istream`< `Elem`, *Tr*> almacena:  
  
-   Un objeto base público virtual de clase [basic_ios](../standard-library/basic-ios-class.md)< `Elem`, *Tr*> `.`  
  
-   Un recuento de extracción de la última operación de entrada sin formato (denominada **count** en el código anterior).  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [basic_ifstream (Clase)](../standard-library/basic-ifstream-class.md) para obtener más información sobre los flujos de entrada.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[basic_istream](#basic_istream__basic_istream)|Construye un objeto de tipo `basic_istream`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[gcount](#basic_istream__gcount)|Devuelve el número de caracteres leídos durante la última entrada sin formato.|  
|[get](#basic_istream__get)|Lee uno o varios caracteres del flujo de entrada.|  
|[getline](#basic_istream__getline)|Lee una línea del flujo de entrada.|  
|[ignore](#basic_istream__ignore)|Hace que se omita una serie de elementos desde la posición de lectura actual.|  
|[peek](#basic_istream__peek)|Devuelve el siguiente carácter que se debe leer.|  
|[putback](#basic_istream__putback)|Coloca un carácter especificado en la secuencia.|  
|[read](#basic_istream__read)|Lee un número especificado de caracteres de la secuencia y los almacena en una matriz.|  
|[readsome](#basic_istream__readsome)|Solo lee del búfer.|  
|[seekg](#basic_istream__seekg)|Mueve la posición de lectura de una secuencia.|  
|[sentry](#basic_istream__sentry)|La clase anidada describe un objeto cuya declaración estructura las funciones de entrada con y sin formato.|  
|[swap](#basic_istream__swap)|Intercambia este objeto `basic_istream` por el parámetro del objeto `basic_istream` proporcionado.|  
|[sync](#basic_istream__sync)|Sincroniza el dispositivo de entrada asociado a la secuencia con el búfer de la secuencia.|  
|[tellg](#basic_istream__tellg)|Notifica la posición de lectura actual en la secuencia.|  
|[unget](#basic_istream__unget)|Devuelve el último carácter leído a la secuencia.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator>>](#basic_istream__operator_gt__gt_)|Llama a una función del flujo de entrada o lee datos con formato del flujo de entrada.|  
|[operator=](#basic_istream__operator_eq)|Asigna a este objeto el `basic_istream` de la parte derecha del operador. Se trata de una asignación de movimiento con una referencia `rvalue` que no deja ninguna copia.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<istream>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namebasicistreambasicistreama--basicistreambasicistream"></a><a name="basic_istream__basic_istream"></a>  basic_istream::basic_istream  
 Construye un objeto de tipo `basic_istream`.  
  
```  
explicit basic_istream(
    basic_streambuf<Elem, Tr>* strbuf,  
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` strbuf`  
 Objeto de tipo [basic_streambuf](../standard-library/basic-streambuf-class.md).  
  
 `_Isstd`  
 `true` si se trata de un flujo estándar; de lo contrario, `false`.  
  
 ` right`  
 Objeto `basic_istream` que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor inicializa la clase base al llamar a [init](../standard-library/basic-ios-class.md#basic_ios__init)(_S `trbuf`). También almacena cero en el recuento de extracción. Para más información sobre este recuento de extracción, vea la sección Comentarios del tema [basic_istream (Clase)](../standard-library/basic-istream-class.md).  
  
 El segundo constructor inicializa la clase base al llamar a `move``( right)`. También almacena _R `ight.gcount()` en el recuento de extracción y cero en el recuento de extracción de _R `ight`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [basic_ifstream::basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream__basic_ifstream) para más información sobre los flujos de entrada.  
  
##  <a name="a-namebasicistreamgcounta--basicistreamgcount"></a><a name="basic_istream__gcount"></a>  basic_istream::gcount  
 Devuelve el número de caracteres leídos durante la última entrada sin formato.  
  
```  
streamsize gcount() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Recuento de extracción.  
  
### <a name="remarks"></a>Comentarios  
 Use [basic_istream::get](#basic_istream__get) para leer caracteres sin formato.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_istream_gcount.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )   
{  
   cout << "Type the letter 'a': ";  
  
   ws( cin );  
   char c[10];  
  
   cin.get( &c[0],9 );  
   cout << c << endl;  
  
   cout << cin.gcount( ) << endl;  
}  
```  
  
```Output  
  
a  
  
```  
  
```Output  
  
      aType the letter 'a':  
a  
1  
```  
  
##  <a name="a-namebasicistreamgeta--basicistreamget"></a><a name="basic_istream__get"></a>  basic_istream::get  
 Lee uno o varios caracteres del flujo de entrada.  
  
```  
int_type get();

basic_istream<Elem, Tr>& get(Elem& Ch);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count, Elem Delim);

basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf);
basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf, Elem Delim);
```  
  
### <a name="parameters"></a>Parámetros  
 ` count`  
 Número de caracteres que se van a leer desde `strbuf`.  
  
 `Delim`  
 Carácter que debe finalizar la lectura si se encuentra antes de ` count`.  
  
 ` str`  
 Cadena en la que se va a escribir.  
  
 `Ch`  
 Carácter que se va a obtener.  
  
 ` strbuf`  
 Búfer en el que se va a escribir.  
  
### <a name="return-value"></a>Valor devuelto  
 El formato sin parámetros de get devuelve el elemento read como un entero o el final del archivo. Los formatos restantes devuelven el flujo (* `this`).  
  
### <a name="remarks"></a>Comentarios  
 La primera de estas funciones de entrada sin formato extrae un elemento, si es posible, como si devolviera `rdbuf`-> `sbumpc`. De lo contrario, devuelve **traits_type::**[eof](../standard-library/char-traits-struct.md#char_traits__eof). Si la función no extrae ningún elemento, llama a [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**failbit**).  
  
 La segunda función extrae el elemento [int_type](../standard-library/basic-ios-class.md#basic_ios__int_type) `meta` del mismo modo. Si `meta` se compara en relación de igualdad con **traits_type::eof**, la función llama a `setstate`(**failbit**). De lo contrario, almacena **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#char_traits__to_char_type)(`meta`) en `Ch`. La función devuelve **\*this**.  
  
 La tercera función devuelve **get**(_ *Str*, ` count`, `widen`('\ **n**')).  
  
 La cuarta función extrae hasta ` count` - 1 elementos y los almacena en la matriz a partir de _ *Str*. Siempre almacena `char_type` después de cualquier elemento extraído que almacene. Para realizar pruebas, la extracción se detiene:  
  
-   Al final del archivo.  
  
-   Después de que la función extraiga un elemento que se compare con relación de igualdad con `Delim`, en cuyo caso el elemento se vuelve a colocar en la secuencia controlada.  
  
-   Después de que la función extraiga ` count` - 1 elementos.  
  
 Si la función no extrae ningún elemento, llama a `setstate`(**failbit**). En cualquier caso, devuelve **\*this**.  
  
 La quinta función devuelve **get**(**strbuf**, `widen`('\ **n**')).  
  
 La sexta función extrae los elementos y los inserta en **strbuf**. La extracción se detiene al final del archivo o en un elemento que se compara con relación de igualdad con _ *Delim*, que no se extrae. También se detiene sin extraer el elemento en cuestión si se produce un error en una inserción o si se inicia una excepción (que se detecta pero no vuelve a iniciarse). Si la función no extrae ningún elemento, llama a `setstate`(**failbit**). En cualquier caso, la función devuelve **\*this**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_istream_get.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )   
{  
   char c[10];  
  
   c[0] = cin.get( );  
   cin.get( c[1] );  
   cin.get( &c[2],3 );  
   cin.get( &c[4], 4, '7' );  
  
   cout << c << endl;  
}  
```  
  
```Output  
  
1111  
```  
  
##  <a name="a-namebasicistreamgetlinea--basicistreamgetline"></a><a name="basic_istream__getline"></a>  basic_istream::getline  
 Obtiene una línea del flujo de entrada.  
  
```  
basic_istream<Elem, Tr>& getline(
    char_type* str,   
    streamsize count);

basic_istream<Elem, Tr>& getline(
    char_type* str,   
    streamsize count,   
    char_type Delim);
```  
  
### <a name="parameters"></a>Parámetros  
 ` count`  
 Número de caracteres que se van a leer desde **strbuf**.  
  
 `Delim`  
 Carácter que debe finalizar la lectura si se encuentra antes de ` count`.  
  
 ` str`  
 Cadena en la que se va a escribir.  
  
### <a name="return-value"></a>Valor devuelto  
 Flujo (**\*this**).  
  
### <a name="remarks"></a>Comentarios  
 La primera de estas funciones de entrada sin formato devuelve **getline**(_ *Str*, ` count`, `widen`(' `\`**n**')).  
  
 La segunda función extrae hasta ` count` - 1 elementos y los almacena en la matriz a partir de _ *Str*. Siempre almacena el carácter de fin de cadena después de los elementos extraídos que almacena. Para realizar pruebas, la extracción se detiene:  
  
-   Al final del archivo.  
  
-   Después de que la función extraiga un elemento que se compare con relación de igualdad con `Delim`, en cuyo caso el elemento no se vuelve a colocar ni se anexa a la secuencia controlada.  
  
-   Después de que la función extraiga ` count` - 1 elementos.  
  
 Si la función no extrae ningún elemento o ` count` - 1 elementos, llama a [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**failbit**). En cualquier caso, devuelve **\*this**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_istream_getline.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )   
{  
   char c[10];  
  
   cin.getline( &c[0], 5, '2' );  
   cout << c << endl;  
}  
```  
  
```Output  
  
121  
```  
  
##  <a name="a-namebasicistreamignorea--basicistreamignore"></a><a name="basic_istream__ignore"></a>  basic_istream::ignore  
 Hace que se omita una serie de elementos desde la posición de lectura actual.  
  
```  
basic_istream<Elem, Tr>& ignore(
    streamsize count = 1,  
    int_type Delim = traits_type::eof());
```  
  
### <a name="parameters"></a>Parámetros  
 ` count`  
 Número de elementos que se van a omitir desde la posición de lectura actual.  
  
 `Delim`  
 Elemento que, si se encuentra antes del recuento, provoca la devolución de **ignore** y permite que todos los elementos después de `Delim` se lean.  
  
### <a name="return-value"></a>Valor devuelto  
 Flujo (**\*this**).  
  
### <a name="remarks"></a>Comentarios  
 La función de entrada sin formato extrae hasta ` count` elementos y los descarta. Pero si ` count` es igual a **numeric_limits\<int>::max**, se toma como arbitrariamente grande. La extracción se detiene anticipadamente al final del archivo o en un elemento `Ch`, de modo que **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#char_traits__to_int_type)(`Ch`) se compara con relación de igualdad con _*Delim* (que también se extrae). La función devuelve **\*this**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_istream_ignore.cpp  
// compile with: /EHsc  
#include <iostream>  
int main( )   
{  
   using namespace std;  
   char chararray[10];  
   cout << "Type 'abcdef': ";  
   cin.ignore( 5, 'c' );  
   cin >> chararray;  
   cout << chararray;  
}  
```  
  
```Output  
  
abcdef  
  
```  
  
```Output  
  
abcdefdef  
```  
  
##  <a name="a-namebasicistreamoperatorgtgta--basicistreamoperatorgtgt"></a><a name="basic_istream__operator_gt__gt_"></a>  basic_istream::operator&gt;&gt;
  
Llama a una función del flujo de entrada o lee datos con formato del flujo de entrada.  
    
```  
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));  
basic_istream& operator>>(basic_streambuf<Elem, Tr>* strbuf);
basic_istream& operator>>(bool& val);
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```  
  
### <a name="parameters"></a>Parámetros  
 `Pfn`  
 Puntero de función.  
  
 ` strbuf`  
 Objeto de tipo **stream_buf**.  
  
 ` val`  
 Valor que se va a leer desde el flujo.  
  
### <a name="return-value"></a>Valor devuelto  
 Flujo (**\*this**).  
  
### <a name="remarks"></a>Comentarios  
 El encabezado `<istream>` también define varios operadores de extracción globales. Para más información, vea [operator>> (\<istream>)](../standard-library/istream-operators.md#operator_gt__gt_).  
  
 La primera función miembro garantiza que una expresión con el formato **istr** >> `ws` llame a [ws](../standard-library/istream-functions.md#ws)(**istr**) y luego devuelva **\*this**. Las funciones segunda y tercera garantizan que los demás manipuladores, como [hex](../standard-library/ios-functions.md#hex), se comporten de forma similar. Las funciones restantes son las funciones de entrada con formato.  
  
 La función:  
  
```  
basic_istream& operator>>(
    basic_streambuf<Elem, Tr>* strbuf);
```  
  
 extrae elementos si _ *Strbuf* no es un puntero nulo y los inserta en ` strbuf`. La extracción se detiene al final del archivo. También se detiene sin extraer el elemento en cuestión si se produce un error en una inserción o si se inicia una excepción (que se detecta pero no vuelve a iniciarse). Si la función no extrae ningún elemento, llama a [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**failbit**). En cualquier caso, la función devuelve **\*this**.  
  
 La función:  
  
```  
basic_istream& operator>>(bool& val);
```  
  
 extrae un campo y lo convierte en un valor booleano al llamar a [use_facet](../standard-library/basic-filebuf-class.md#basic_filebuf__open) < `num_get`\< **Elem**, **InIt**>([getloc](../standard-library/ios-base-class.md#ios_base__getloc)). [get](../standard-library/ios-base-class.md#ios_base__getloc)(**InIt**([rdbuf](../standard-library/basic-ios-class.md#basic_ios__rdbuf)), `Init`(0), **\*this**, `getloc`, ` val`). Aquí, **InIt** se define como [istreambuf_iterator](../standard-library/istreambuf-iterator-class.md) \< **Elem**, **Tr**>. La función devuelve **\*this**.  
  
 Las funciones:  
  
```  
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val); 
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val); 
basic_istream& operator>>(void *& val);
```  
  
 extraen un campo y lo convierten en un valor numérico al llamar a `use_facet`< `num_get`\< **Elem**, **InIt**>(`getloc`). [get](#basic_istream__get)(**InIt**(`rdbuf`), `Init`(0), **\*this**, `getloc`, ` val`). Aquí, **InIt** se define como `istreambuf_iterator`\< **Elem**, **Tr**> y ` val` tiene el tipo **long***,*`unsigned long`*,* o **void \***, según sea necesario.  
  
 Si el valor convertido no se puede representar como el tipo de ` val`, la función llama a [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**failbit**). En cualquier caso, la función devuelve **\*this**.  
  
 Las funciones:  
  
```  
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```  
  
 extraen un campo y lo convierten en un valor numérico al llamar a `use_facet`< `num_get`\< **Elem**, **InIt**>(`getloc`). **get**(**InIt**(`rdbuf`), `Init`(0), **\*this**, `getloc`, ` val`). Aquí, **InIt** se define como `istreambuf_iterator`\< **Elem**, **Tr**> y ` val` tiene el tipo **double** o `long double`, según sea necesario.  
  
 Si el valor convertido no se puede representar como el tipo de ` val`, la función llama a `setstate`(**failbit**). En cualquier caso, devuelve **\*this**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// istream_basic_istream_op_is.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
ios_base& hex2( ios_base& ib )   
{  
   ib.unsetf( ios_base::dec );  
   ib.setf( ios_base::hex );  
   return ib;  
}  
  
basic_istream<char, char_traits<char> >& somefunc(basic_istream<char, char_traits<char> > &i)  
{  
   if ( i == cin )   
   {  
      cerr << "i is cin" << endl;  
   }  
   return i;  
}  
  
int main( )   
{  
   int i = 0;  
   cin >> somefunc;  
   cin >> i;  
   cout << i << endl;  
   cin >> hex2;  
   cin >> i;  
   cout << i << endl;  
}  
```  
  
##  <a name="a-namebasicistreamoperatoreqa--basicistreamoperator"></a><a name="basic_istream__operator_eq"></a>  basic_istream::operator=  
 Asigna a este objeto el `basic_istream` de la parte derecha del operador. Se trata de una asignación de movimiento con una referencia `rvalue` que no deja ninguna copia.  
  
```  
basic_istream& operator=(basic_istream&& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 Referencia `rvalue` a un objeto `basic_ifstream`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve *this.  
  
### <a name="remarks"></a>Comentarios  
 El operador miembro llama a swap `( right)`.  
  
##  <a name="a-namebasicistreampeeka--basicistreampeek"></a><a name="basic_istream__peek"></a>  basic_istream::peek  
 Devuelve el siguiente carácter que se debe leer.  
  
```  
int_type peek();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siguiente carácter que se va a leer.  
  
### <a name="remarks"></a>Comentarios  
 La función de entrada sin formato extrae un elemento, si es posible, como si devolviera `rdbuf` -> [sgetc](../standard-library/basic-streambuf-class.md#basic_streambuf__sgetc). De lo contrario, devuelve **traits_type::**[eof](../standard-library/char-traits-struct.md#char_traits__eof).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_istream_peek.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )   
{  
   char c[10], c2;  
   cout << "Type 'abcde': ";  
  
   c2 = cin.peek( );  
   cin.getline( &c[0], 9 );  
  
   cout << c2 << " " << c << endl;  
}  
```  
  
```Output  
  
abcde  
  
```  
  
```Output  
  
      abcdeType 'abcde': abcde  
a abcde  
```  
  
##  <a name="a-namebasicistreamputbacka--basicistreamputback"></a><a name="basic_istream__putback"></a>  basic_istream::putback  
 Coloca un carácter especificado en la secuencia.  
  
```  
basic_istream<Elem, Tr>& putback(
    char_type Ch);
```  
  
### <a name="parameters"></a>Parámetros  
 `Ch`  
 Carácter que se va a volver a colocar en el flujo.  
  
### <a name="return-value"></a>Valor devuelto  
 Flujo (**\*this**).  
  
### <a name="remarks"></a>Comentarios  
 La [función de entrada sin formato](../standard-library/basic-istream-class.md) vuelve a colocar `Ch`, si es posible, como si llamara a [rdbuf](../standard-library/basic-ios-class.md#basic_ios__rdbuf)`->`[sputbackc](../standard-library/basic-streambuf-class.md#basic_streambuf__sputbackc). Si rdbuf es un puntero nulo, o si la llamada a `sputbackc` devuelve **traits_type::**[eof](../standard-library/char-traits-struct.md#char_traits__eof), la función llama a [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**badbit**). En cualquier caso, devuelve **\*this**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_istream_putback.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )   
{  
   char c[10], c2, c3;  
  
   c2 = cin.get( );  
   c3 = cin.get( );  
   cin.putback( c2 );  
   cin.getline( &c[0], 9 );  
   cout << c << endl;  
}  
```  
  
```Output  
  
qwq  
```  
  
##  <a name="a-namebasicistreamreada--basicistreamread"></a><a name="basic_istream__read"></a>  basic_istream::read  
 Lee un número especificado de caracteres de la secuencia y los almacena en una matriz.  
  
 Este método es potencialmente inseguro, ya que se basa en el llamador para comprobar que los valores pasados son correctos.  
  
```  
basic_istream<Elem, Tr>& read(
    char_type* str,   
    streamsize count);
```  
  
### <a name="parameters"></a>Parámetros  
 ` str`  
 Matriz en la que se van a leer los caracteres.  
  
 ` count`  
 Número de caracteres que se va a leer.  
  
### <a name="return-value"></a>Valor devuelto  
 Flujo (`*this`).  
  
### <a name="remarks"></a>Comentarios  
 La función de entrada sin formato extrae hasta `count` elementos y los almacena en la matriz a partir de_ `Str`. La extracción se detiene anticipadamente al final del archivo, en cuyo caso la función llama a [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(`failbit`). En cualquier caso, devuelve `*this`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_istream_read.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main()  
{  
    char c[10];  
    int count = 5;  
  
    cout << "Type 'abcde': ";  
  
    // Note: cin::read is potentially unsafe, consider  
    // using cin::_Read_s instead.  
    cin.read(&c[0], count);  
    c[count] = 0;  
  
    cout << c << endl;  
}  
```  
  
```Output  
  
abcde  
  
```  
  
```Output  
  
      abcdeType 'abcde': abcde  
abcde  
```  
  
##  <a name="a-namebasicistreamreadsomea--basicistreamreadsome"></a><a name="basic_istream__readsome"></a>  basic_istream::readsome  
 Lee el número especificado de valores de carácter.  
  
 Este método es potencialmente inseguro, ya que se basa en el llamador para comprobar que los valores pasados son correctos.  
  
```  
streamsize readsome(
    char_type* str,  
    streamsize count);
```  
  
### <a name="parameters"></a>Parámetros  
 `str`  
 Matriz en la que `readsome` almacena los caracteres que lee.  
  
 `count`  
 Número de caracteres que se va a leer.  
  
### <a name="return-value"></a>Valor devuelto  
 Número de caracteres realmente leídos, [gcount](#basic_istream__gcount).  
  
### <a name="remarks"></a>Comentarios  
 Esta función de entrada sin formato extrae hasta `count` elementos del flujo de entrada y los almacena en la matriz `str`.  
  
 Esta función no espera a la entrada. Lee aquellos datos que estén disponibles.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_istream_readsome.cpp  
// compile with: /EHsc /W3  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   char c[10];  
   int count = 5;  
  
   cout << "Type 'abcdefgh': ";  
  
   // cin.read blocks until user types input.  
   // Note: cin::read is potentially unsafe, consider  
   // using cin::_Read_s instead.  
   cin.read(&c[0], 2);  
  
   // Note: cin::readsome is potentially unsafe, consider  
   // using cin::_Readsome_s instead.  
   int n = cin.readsome(&c[0], count);  // C4996  
   c[n] = 0;  
   cout << n << " characters read" << endl;  
   cout << c << endl;  
}  
```  
  
##  <a name="a-namebasicistreamseekga--basicistreamseekg"></a><a name="basic_istream__seekg"></a>  basic_istream::seekg  
 Mueve la posición de lectura de una secuencia.  
  
```  
basic_istream<Elem, Tr>& seekg(pos_type pos);

basic_istream<Elem, Tr>& seekg(off_type off, ios_base::seekdir way);
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 Posición absoluta a la que se va a mover el puntero de lectura.  
  
 `off`  
 Desplazamiento para mover el puntero de lectura en relación con `way`.  
  
 `way`  
 Una de las enumeraciones [ios_base::seekdir](../standard-library/ios-base-class.md#ios_base__seekdir).  
  
### <a name="return-value"></a>Valor devuelto  
 Flujo (**\*this**).  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro realiza una búsqueda absoluta y la segunda una búsqueda relativa.  
  
> [!NOTE]
>  No use la segunda función miembro con archivos de texto, ya que el estándar de C++ no admite las búsquedas relativas en archivos de texto.  
  
 Si [fail](../standard-library/basic-ios-class.md#basic_ios__fail) es False, la primera función miembro llama a **newpos** = [rdbuf](../standard-library/basic-ios-class.md#basic_ios__rdbuf) -> [pubseekpos](../standard-library/basic-streambuf-class.md#basic_streambuf__pubseekpos)(`pos`), para algunos **pos_type** el objeto temporal **newpos**. Si **fail** es False, la segunda función llama a **newpos** = **rdbuf** -> [pubseekoff](../standard-library/basic-streambuf-class.md#basic_streambuf__pubseekoff)(`off`, `way`). En cualquier caso, si (`off_type`) **newpos** == ( `off_type`)(-1) (se produce un error en la operación de posicionamiento), la función llama a **istr**. [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**failbit**). Ambas funciones devuelven **\*this**.  
  
 Si [fail](../standard-library/basic-ios-class.md#basic_ios__fail) es True, las funciones miembro no hacen nada.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_istream_seekg.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main ( )   
{  
   using namespace std;  
   ifstream file;  
   char c, c1;  
  
   file.open( "basic_istream_seekg.txt" );  
   file.seekg(2);   // seek to position 2  
   file >> c;  
   cout << c << endl;  
}  
```  
  
##  <a name="a-namebasicistreamsentrya--basicistreamsentry"></a><a name="basic_istream__sentry"></a>  basic_istream::sentry  
 La clase anidada describe un objeto cuya declaración estructura las funciones de entrada con y sin formato.  
  
class sentry {  
   public:  
   explicit sentry(basic_istream\<Elem, Tr>& _Istr,  
   bool _Noskip = false); operator bool() const; };  
  
### <a name="remarks"></a>Comentarios  
 Si `_Istr``.`[good](../standard-library/basic-ios-class.md#basic_ios__good) es True, el constructor:  
  
-   Llama a `_Istr`. [tie](../standard-library/basic-ios-class.md#basic_ios__tie) -> [flush](../standard-library/basic-ostream-class.md#basic_ostream__flush) si `_Istr`. `tie` no es un puntero nulo  
  
-   Llama realmente a [ws](../standard-library/istream-functions.md#ws)(`_Istr`) si `_Istr`. [flags](../standard-library/ios-base-class.md#ios_base__flags)**&**[skipws](../standard-library/ios-functions.md#skipws) es distinto de cero  
  
 Si, después de dicha de preparación, `_Istr`. **good** es False, el constructor llama a `_Istr`. [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**failbit**). En cualquier caso, el constructor almacena el valor devuelto por `_Istr`. **good** en **status**. Una llamada posterior a **operator bool** devuelve este valor almacenado.  
  
##  <a name="a-namebasicistreamswapa--basicistreamswap"></a><a name="basic_istream__swap"></a>  basic_istream::swap  
 Intercambia el contenido de dos objetos `basic_istream`.  
  
```  
void swap(basic_istream& right);
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 Referencia lvalue a un objeto `basic_istream`.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro llama a [basic_ios::swap](../standard-library/basic-ios-class.md#basic_ios__swap)`(`` right``)`. También intercambia el recuento de extracción por el recuento de extracción de ` right`.  
  
##  <a name="a-namebasicistreamsynca--basicistreamsync"></a><a name="basic_istream__sync"></a>  basic_istream::sync  
 Sincroniza el dispositivo de entrada asociado a la secuencia con el búfer de la secuencia.  
  
```  
int sync();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si [rdbuf](../standard-library/basic-ios-class.md#basic_ios__rdbuf) es un puntero nulo, la función devuelve -1. De lo contrario, llama a `rdbuf` -> [pubsync](../standard-library/basic-streambuf-class.md#basic_streambuf__pubsync). Si eso devuelve -1, la función llama a [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**badbit**) y devuelve -1. De lo contrario, la función devuelve cero.  
  
##  <a name="a-namebasicistreamtellga--basicistreamtellg"></a><a name="basic_istream__tellg"></a>  basic_istream::tellg  
 Notifica la posición de lectura actual en la secuencia.  
  
```  
pos_type tellg();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La posición actual en la secuencia.  
  
### <a name="remarks"></a>Comentarios  
 Si [fail](../standard-library/basic-ios-class.md#basic_ios__fail) es False, la función miembro devuelve [rdbuf](../standard-library/basic-ios-class.md#basic_ios__rdbuf) -> [pubseekoff](../standard-library/basic-streambuf-class.md#basic_streambuf__pubseekoff)(0, `cur`, **in**). De lo contrario, devuelve `pos_type`(-1).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_istream_tellg.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main()  
{  
    using namespace std;  
    ifstream file;  
    char c;  
    streamoff i;  
  
    file.open("basic_istream_tellg.txt");  
    i = file.tellg();  
    file >> c;  
    cout << c << " " << i << endl;  
  
    i = file.tellg();  
    file >> c;  
    cout << c << " " << i << endl;  
}  
```  
  
##  <a name="a-namebasicistreamungeta--basicistreamunget"></a><a name="basic_istream__unget"></a>  basic_istream::unget  
 Devuelve el último carácter leído a la secuencia.  
  
```  
basic_istream<Elem, Tr>& unget();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Flujo (**\*this**).  
  
### <a name="remarks"></a>Comentarios  
 La [función de entrada sin formato](../standard-library/basic-istream-class.md) vuelve a colocar el elemento anterior en el flujo, si es posible, como si llamara a `rdbuf` -> [sungetc](../standard-library/basic-streambuf-class.md#basic_streambuf__sungetc). Si [rdbuf](../standard-library/basic-ios-class.md#basic_ios__rdbuf) es un puntero nulo, o si la llamada a `sungetc` devuelve **traits_type::**[eof](../standard-library/basic-ios-class.md#basic_ios__eof), la función llama a [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)(**badbit**). En cualquier caso, devuelve **\*this**.  
  
 Para más información sobre los errores de `unget`, vea [basic_streambuf::sungetc](../standard-library/basic-streambuf-class.md#basic_streambuf__sungetc).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_istream_unget.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main( )   
{  
   char c[10], c2;  
  
   cout << "Type 'abc': ";  
   c2 = cin.get( );  
   cin.unget( );  
   cin.getline( &c[0], 9 );  
   cout << c << endl;  
}  
```  
  
```Output  
  
abc  
  
```  
  
```Output  
  
      abcType 'abc': abc  
abc  
```  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)


