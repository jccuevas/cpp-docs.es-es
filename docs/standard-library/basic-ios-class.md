---
title: basic_ios (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ios/std::basic_ios
- ios/std::basic_ios::char_type
- ios/std::basic_ios::int_type
- ios/std::basic_ios::off_type
- ios/std::basic_ios::pos_type
- ios/std::basic_ios::traits_type
- ios/std::basic_ios::bad
- ios/std::basic_ios::clear
- ios/std::basic_ios::copyfmt
- ios/std::basic_ios::eof
- ios/std::basic_ios::exceptions
- ios/std::basic_ios::fail
- ios/std::basic_ios::fill
- ios/std::basic_ios::good
- ios/std::basic_ios::imbue
- ios/std::basic_ios::init
- ios/std::basic_ios::move
- ios/std::basic_ios::narrow
- ios/std::basic_ios::rdbuf
- ios/std::basic_ios::rdstate
- ios/std::basic_ios::set_rdbuf
- ios/std::basic_ios::setstate
- ios/std::basic_ios::swap
- ios/std::basic_ios::tie
- ios/std::basic_ios::widen
- ios/std::basic_ios::explicit operator bool
dev_langs:
- C++
helpviewer_keywords:
- std::basic_ios [C++]
- std::basic_ios [C++], char_type
- std::basic_ios [C++], int_type
- std::basic_ios [C++], off_type
- std::basic_ios [C++], pos_type
- std::basic_ios [C++], traits_type
- std::basic_ios [C++], bad
- std::basic_ios [C++], clear
- std::basic_ios [C++], copyfmt
- std::basic_ios [C++], eof
- std::basic_ios [C++], exceptions
- std::basic_ios [C++], fail
- std::basic_ios [C++], fill
- std::basic_ios [C++], good
- std::basic_ios [C++], imbue
- std::basic_ios [C++], init
- std::basic_ios [C++], move
- std::basic_ios [C++], narrow
- std::basic_ios [C++], rdbuf
- std::basic_ios [C++], rdstate
- std::basic_ios [C++], set_rdbuf
- std::basic_ios [C++], setstate
- std::basic_ios [C++], swap
- std::basic_ios [C++], tie
- std::basic_ios [C++], widen
ms.assetid: 4fdcd8e1-62d2-4611-8a70-1e4f58434007
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6bbcfb2f315c9b453d49b2bbdb5be60a6dbc8f6f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="basicios-class"></a>basic_ios (Clase)
La clase de plantilla describe las funciones de almacenamiento y miembro comunes tanto a los flujos de entrada (de la clase de plantilla [basic_istream](../standard-library/basic-istream-class.md)) como a los de salida (de la clase de plantilla [basic_ostream](../standard-library/basic-ostream-class.md)) que dependen de los parámetros de plantilla. (La clase [ios_base](../standard-library/ios-base-class.md) describe lo que es común y no depende de los parámetros de plantilla). Un objeto de clase **basic_ios\<class Elem, class Traits>** ayuda a controlar un flujo con elementos de tipo **Elem**, cuyos rasgos de carácter están determinados por la clase **Traits**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
 
template <class Elem, class Traits>  
class basic_ios : public ios_base  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Elem`  
 Un tipo.  
  
 `Traits`  
 Una variable de tipo `char_traits`.  
  
## <a name="remarks"></a>Comentarios  
 Un objeto de clase **basic_ios\<class Elem, class Traits>** almacena:  
  
-   Un puntero de valor equivalente a un objeto de tipo [basic_istream](../standard-library/basic-istream-class.md)**\<Elem, Traits>**.  
  
-   Un puntero de búfer de flujo a un objeto de tipo [basic_streambuf](../standard-library/basic-streambuf-class.md)**\<Elem, Traits >**.  
  
- [Información de formato](../standard-library/ios-base-class.md).  
  
- [Información de estado de flujo](../standard-library/ios-base-class.md) en un objeto base de tipo [ios_base](../standard-library/ios-base-class.md).  
  
-   Un carácter de relleno en un objeto de tipo `char_type`.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[basic_ios](#basic_ios)|Construye la clase `basic_ios`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|Sinónimo del parámetro de plantilla `Elem`.|  
|[int_type](#int_type)|Sinónimo de `Traits::int_type`.|  
|[off_type](#off_type)|Sinónimo de `Traits::off_type`.|  
|[pos_type](#pos_type)|Sinónimo de `Traits::pos_type`.|  
|[traits_type](#traits_type)|Sinónimo del parámetro de plantilla `Traits`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[bad](#bad)|Indica una pérdida de integridad del búfer de secuencia.|  
|[clear](#clear)|Borra todas las marcas de error.|  
|[copyfmt](#copyfmt)|Copia las marcas de una secuencia a otra.|  
|[eof](#eof)|Indica si se ha alcanzado el extremo de una secuencia.|  
|[exceptions](#exceptions)|Indica qué excepciones iniciará la secuencia.|  
|[fail](#fail)|Indica un error al extraer un campo válido de una secuencia.|  
|[fill](#fill)|Especifica o devuelve el carácter que se usará si el texto no tiene el mismo ancho que la secuencia.|  
|[good](#good)|Indica que la secuencia está en buen estado.|  
|[imbue](#imbue)|Cambia la configuración regional.|  
|[init](#init)|Llamada por constructores `basic_ios`.|  
|[move](#move)|Mueve todos los valores, excepto el puntero al búfer de secuencia, desde el parámetro hasta el objeto actual.|  
|[narrow](#narrow)|Busca el carácter equivalente a un determinado `char_type`.|  
|[rdbuf](#rdbuf)|Redirige la secuencia al búfer especificado.|  
|[rdstate](#rdstate)|Lee el estado de bits de las marcas.|  
|[set_rdbuf](#set_rdbuf)|Asigna un búfer de secuencia para que sea el búfer de lectura de este objeto de secuencia.|  
|[setstate](#setstate)|Establece marcas adicionales.|  
|[swap](#swap)|Cambia los valores de este objeto `basic_ios` por los de otro objeto `basic_ios`. No se intercambian los punteros a los búferes de secuencia.|  
|[tie](#tie)|Se asegura de que una secuencia se procese antes que otra.|  
|[widen](#widen)|Busca el `char_type` equivalente a un determinado carácter.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[explicit operator bool](#op_bool)|Permite el uso de un objeto `basic_ios` como un `bool`. La conversión automática de tipo está deshabilitada para evitar efectos secundarios típicos no deseados.|  
|[operator void *](#op_void_star)|Indica si la secuencia sigue siendo aceptable.|  
|[operator!](#op_not)|Indica si la secuencia no es inaceptable.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<ios>  
  
 **Espacio de nombres:** std  
  
##  <a name="bad"></a>  basic_ios::bad  
 Indica una pérdida de integridad del búfer de flujo.  
  
```  
bool bad() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si `rdstate & badbit` es distinto de cero; en caso contrario, `false`.  
  
 Para más información sobre `badbit`, vea [ios_base::iostate](../standard-library/ios-base-class.md#iostate).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_ios_bad.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( void )  
{  
  using namespace std;  
  bool b = cout.bad( );  
  cout << boolalpha;  
  cout << b << endl;  
    
  b = cout.good( );  
  cout << b << endl;  
}  
  
```  
  
##  <a name="basic_ios"></a>  basic_ios::basic_ios  
 Construye la clase basic_ios.  
  
```   
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```  
  
### <a name="parameters"></a>Parámetros  
 `sb`  
 Búfer estándar para almacenar elementos de entrada o salida.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor inicializa sus objetos miembro al llamar a [init](#init)(_ *Sb*). El segundo constructor (protegido) deja sus objetos miembro sin inicializar. Una llamada posterior a **init** debe inicializar el objeto para que se pueda destruir con seguridad.  
  
##  <a name="char_type"></a>  basic_ios::char_type  
 Sinónimo del parámetro de plantilla **Elem**.  
  
```   
typedef Elem char_type;  
```  
  
##  <a name="clear"></a>  basic_ios::clear  
 Borra todas las marcas de error.  
  
```   
void clear(iostate state = goodbit, bool reraise = false); 
void clear(io_state state);
```  
  
### <a name="parameters"></a>Parámetros  
 `state` (opcional)  
 Las marcas que quiere establecer después de borrar todas las marcas. Tiene como valor predeterminado `goodbit`.  
  
 `reraise` (opcional)  
 Especifica si la excepción debe volver a generarse. El valor predeterminado es `false` (no volver a generar la excepción).  
  
### <a name="remarks"></a>Comentarios  
 Las marcas son **goodbit**, **failbit**, **eofbit** y **badbit**. Prueba de estas marcas con [good](#good), [bad](#bad), [eof](#eof) y [fail](#fail)  
  
 La función miembro reemplaza la información de estado de la secuencia almacenada por:  
  
 `state` &#124; `(`[rdbuf](#rdbuf) != 0 **goodbit** : **badbit**)  
  
 Si `state`**&**[exceptions](#exceptions) es distinto de cero, inicia un objeto de clase [failure](../standard-library/ios-base-class.md#failure).  
  
### <a name="example"></a>Ejemplo  
  Vea [rdstate](#rdstate) y [getline](../standard-library/string-functions.md#getline) para obtener ejemplos de uso de **clear**.  
  
##  <a name="copyfmt"></a>  basic_ios::copyfmt  
 Copia las marcas de una secuencia a otra.  
  
```   
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Flujo cuyas marcas se quieren copiar.  
  
### <a name="return-value"></a>Valor devuelto  
 Objeto **this** del flujo en el que se están copiando las marcas.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro informa sobre el evento de devolución de llamada **borrar\_eventos**. Luego copia de `right` en **\*this** el carácter de relleno, el puntero de valor equivalente y la información de formato. Antes de modificar la máscara de la excepción, informa sobre el evento de devolución de llamada **copyfmt_event**. Si, una vez que la copia está completa, **state &**[exceptions](#exceptions) es distinto de cero, la función llama realmente a [clear](#clear) con el argumento [rdstate](#rdstate). Devuelve **\*this**.  
  
### <a name="example"></a>Ejemplo  
  
```cpp    
// basic_ios_copyfmt.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )  
{  
  using namespace std;  
  ofstream x( "test.txt" );  
  int i = 10;  
    
  x << showpos;  
  cout << i << endl;  
  cout.copyfmt( x );  
  cout << i << endl;  
}  
  
```  
  
##  <a name="eof"></a>  basic_ios::eof  
 Indica si se ha alcanzado el extremo de una secuencia.  
  
```  
bool eof() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si se ha alcanzado el fin del flujo; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve `true` si [rdstate](#rdstate) `& eofbit` es distinto de cero. Para más información sobre `eofbit`, vea [ios_base::iostate](../standard-library/ios-base-class.md#iostate).  
  
### <a name="example"></a>Ejemplo  
  
```cpp    
// basic_ios_eof.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
using namespace std;  
  
int main( int argc, char* argv[] )  
{  
  fstream   fs;  
  int n = 1;  
  fs.open( "basic_ios_eof.txt" );   // an empty file  
  cout << boolalpha  
  cout << fs.eof() << endl;  
  fs >> n;   // Read the char in the file  
  cout << fs.eof() << endl;  
}  
  
```  
  
##  <a name="exceptions"></a>  basic_ios::exceptions  
 Indica qué excepciones iniciará la secuencia.  
  
```   
iostate exceptions() const; 
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```  
  
### <a name="parameters"></a>Parámetros  
 *Newexcept*  
 Marcas que quiere que inicie una excepción.  
  
### <a name="return-value"></a>Valor devuelto  
 Marcas especificadas actualmente para iniciar una excepción para el flujo.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro devuelve la máscara de excepción almacenada. La segunda función miembro almacena *_Except* en la máscara de excepción y devuelve su anterior valor almacenado. Tenga en cuenta que, al almacenar una nueva máscara de excepción, se puede iniciar una excepción como la llamada a [clear](#clear)([rdstate](#rdstate)).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_ios_exceptions.cpp  
// compile with: /EHsc /GR  
#include <iostream>  
  
int main( )  
{  
  using namespace std;  
    
  cout << cout.exceptions( ) << endl;  
  cout.exceptions( ios::eofbit );  
  cout << cout.exceptions( ) << endl;  
  try  
  {  
    cout.clear( ios::eofbit );   // Force eofbit on  
  }  
  catch ( exception &e )  
  {  
    cout.clear( );  
    cout << "Caught the exception." << endl;  
    cout << "Exception class: " << typeid(e).name()  << endl;  
    cout << "Exception description: " << e.what() << endl;  
  }  
}  
  
```  
  
```Output  
  
0  
1  
Caught the exception.  
Exception class: class std::ios_base::failure  
Exception description: ios_base::eofbit set   
```  
  
##  <a name="fail"></a>  basic_ios::fail  
 Indica un error al extraer un campo válido de una secuencia.  
  
```  
bool fail() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si [rdstate](#rdstate) `& (badbit|failbit)` es distinto de cero; en caso contrario, `false`.  
  
 Para más información sobre `failbit`, vea [ios_base::iostate](../standard-library/ios-base-class.md#iostate).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_ios_fail.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( void )  
{  
  using namespace std;  
  bool b = cout.fail( );  
  cout << boolalpha;  
  cout << b << endl;  
}  
  
```  
  
##  <a name="fill"></a>  basic_ios::fill  
 Especifica o devuelve el carácter que se usará si el texto no tiene el mismo ancho que la secuencia.  
  
```   
char_type fill() const; 
char_type fill(char_type Char);
```  
  
### <a name="parameters"></a>Parámetros  
 `Char`  
 Carácter que se quiere como carácter de relleno.  
  
### <a name="return-value"></a>Valor devuelto  
 Carácter de relleno actual.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro devuelve el carácter de relleno almacenado. La segunda función miembro almacena `Char` en el carácter de relleno y devuelve su anterior valor almacenado.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_ios_fill.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iomanip>  
  
int main( )  
{  
  using namespace std;  
    
  cout << setw( 5 ) << 'a' << endl;     
  cout.fill( 'x' );  
  cout << setw( 5 ) << 'a' << endl;      
  cout << cout.fill( ) << endl;  
}  
  
```  
  
```Output  
  
a  
xxxxa  
x   
```  
  
##  <a name="good"></a>  basic_ios::good  
 Indica que la secuencia está en buen estado.  
  
```  
bool good() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si [rdstate](#rdstate) `== goodbit` (sin marcas de estado establecidas); de lo contrario, `false`.  
  
 Para más información sobre `goodbit`, vea [ios_base::iostate](../standard-library/ios-base-class.md#iostate).  
  
### <a name="example"></a>Ejemplo  
  Vea [basic_ios::bad](#bad) para obtener un ejemplo de uso de `good`.  
  
##  <a name="imbue"></a>  basic_ios::imbue  
 Cambia la configuración regional.  
  
```   
locale imbue(const locale& Loc);
```  
  
### <a name="parameters"></a>Parámetros  
 `Loc`  
 Cadena de configuración regional.  
  
### <a name="return-value"></a>Valor devuelto  
 Configuración regional anterior.  
  
### <a name="remarks"></a>Comentarios  
 Si [rdbuf](#rdbuf) no es un puntero nulo, la función miembro llama a  
  
 `rdbuf`-> [pubimbue](../standard-library/basic-streambuf-class.md#pubimbue)(_ *Loc*)  
  
 En cualquier caso, devuelve [ios_base::imbue](../standard-library/ios-base-class.md#imbue)(_ *Loc*).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_ios_imbue.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <locale>  
  
int main( )  
{  
  using namespace std;  
    
  cout.imbue( locale( "french_france" ) );  
  double x = 1234567.123456;  
  cout << x << endl;  
}  
  
```  
  
##  <a name="init"></a>  basic_ios::init  
 Lo llaman los constructores basic_ios.  
  
```  
 
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Sb`  
 Búfer estándar para almacenar elementos de entrada o salida.  
  
 `_Isstd`  
 Especifica si se trata de un flujo estándar.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro almacena valores en todos los objetos miembro, de modo que:  
  
- [rdbuf](#rdbuf) devuelve *_Sb*.  
  
- [tie](#tie) devuelve un puntero nulo.  
  
- [rdstate](#rdstate) devuelve [goodbit](../standard-library/ios-base-class.md#iostate) si `_Sb` es distinto de cero; en caso contrario, devuelve [badbit](../standard-library/ios-base-class.md#iostate).  
  
- [exceptions](#exceptions) devuelve **goodbit**.  
  
- [flags](../standard-library/ios-base-class.md#flags) devuelve [skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [dec](../standard-library/ios-base-class.md#fmtflags).  
  
- [width](../standard-library/ios-base-class.md#width) devuelve 0.  
  
- [precision](../standard-library/ios-base-class.md#precision) devuelve 6.  
  
- [fill](#fill) devuelve el carácter de espacio.  
  
- [getloc](../standard-library/ios-base-class.md#getloc) devuelve `locale::classic`.  
  
- [iword](../standard-library/ios-base-class.md#iword) devuelve cero y [pword](../standard-library/ios-base-class.md#pword) devuelve un puntero nulo para todos los valores de argumento.  
  
##  <a name="int_type"></a>  basic_ios::int_type  
 Sinónimo de **traits_type::int_type**.  
  
```  
typedef typename traits_type::int_type int_type;  
```  
  
##  <a name="move"></a>  basic_ios::move  
 Mueve todos los valores, excepto el puntero al búfer de secuencia, desde el parámetro hasta el objeto actual.  
  
```   
void move(basic_ios&& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Objeto `ios_base` cuyos valores se van a mover.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro protegida mueve todos los valores almacenados en `right` a `*this`, excepto el `stream buffer pointer` almacenado, que no cambia en `right` y se establece en un puntero nulo en `*this`. El `tie pointer` almacenado está establecido en un puntero nulo en `right`.  
  
##  <a name="narrow"></a>  basic_ios::narrow  
 Busca el carácter equivalente a un determinado `char_type`.  
  
```  
char narrow(char_type Char, char Default = '\0') const;
```  
  
### <a name="parameters"></a>Parámetros  
 `Char`  
 `char` que se va a convertir.  
  
 `Default`  
 `char` que se quiere que se devuelva si no se encuentra ningún equivalente.  
  
### <a name="return-value"></a>Valor devuelto  
 `char` equivalente a un determinado `char_type`.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [use_facet](../standard-library/basic-filebuf-class.md#open)\<ctype\<E >> ( [getloc](../standard-library/ios-base-class.md#getloc)()).`narrow` ( `Char`, `Default`).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_ios_narrow.cpp  
// compile with: /EHsc  
#include <ios>  
#include <iostream>  
#include <wchar.h>  
  
int main( )  
{  
  using namespace std;  
  wchar_t *x = L"test";  
  char y[10];  
  cout << x[0] << endl;  
  wcout << x << endl;  
  y[0] = wcout.narrow( x[0] );  
  cout << y[0] << endl;  
}  
```  
  
##  <a name="off_type"></a>  basic_ios::off_type  
 Sinónimo de **traits_type::off_type**.  
  
```  
typedef typename traits_type::off_type off_type;  
```  
  
##  <a name="op_void_star"></a>  basic_ios::operator void *  
 Indica si la secuencia sigue siendo aceptable.  
  
```  
 operator void *() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El operador devuelve un puntero nulo solo si [fail](#fail).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_ios_opgood.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )  
{  
  using namespace std;  
  cout << (bool)(&cout != 0) << endl;   // Stream is still good  
}  
  
```  
  
```Output  
1  
```  
  
##  <a name="op_not"></a>  basic_ios::operator!  
 Indica si la secuencia no es inaceptable.  
  
```   
bool operator!() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve [fail](#fail).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_ios_opbad.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )  
{  
  using namespace std;  
  cout << !cout << endl;   // Stream is not bad  
}  
  
```  
  
```Output  
0  
```  
  
##  <a name="op_bool"></a>  basic_ios::operator bool  
 Permite el uso de un objeto `basic_ios` como un `bool`. La conversión automática de tipo está deshabilitada para evitar efectos secundarios típicos no deseados.  
  
```  
explicit operator bool() const;
```  
  
### <a name="remarks"></a>Comentarios  
 El operador devuelve un valor que puede convertirse en `false` solo si `fail()`. El tipo devuelto puede convertirse solo a `bool`, no a `void *` ni a cualquier otro tipo escalar conocido.  
  
##  <a name="pos_type"></a>  basic_ios::pos_type  
 Sinónimo de **traits_type::pos_type**.  
  
```  
typedef typename traits_type::pos_type pos_type;  
```  
  
##  <a name="rdbuf"></a>  basic_ios::rdbuf  
 Redirige la secuencia al búfer especificado.  
  
```   
basic_streambuf<Elem, Traits> *rdbuf() const; 
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Sb`  
 Flujo.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro devuelve el puntero del búfer de flujo almacenado.  
  
 La segunda función miembro almacena `_Sb` en el puntero del búfer de flujo almacenado y devuelve el valor almacenado previamente.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_ios_rdbuf.cpp  
// compile with: /EHsc  
#include <ios>  
#include <iostream>  
#include <fstream>  
  
int main( )  
{  
  using namespace std;  
  ofstream file( "rdbuf.txt" );  
  streambuf *x = cout.rdbuf( file.rdbuf( ) );  
  cout << "test" << endl;   // Goes to file  
  cout.rdbuf(x);  
  cout << "test2" << endl;  
}  
  
```  
  
```Output  
test2  
```  
  
##  <a name="rdstate"></a>  basic_ios::rdstate  
 Lee el estado de bits de las marcas.  
  
```  
 
iostate rdstate() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Información de estado del flujo almacenado.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// basic_ios_rdstate.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
using namespace std;  
  
void TestFlags( ios& x )  
{  
  cout << ( x.rdstate( ) & ios::badbit ) << endl;  
  cout << ( x.rdstate( ) & ios::failbit ) << endl;  
  cout << ( x.rdstate( ) & ios::eofbit ) << endl;  
  cout << endl;  
}  
  
int main( )  
{  
  fstream x( "c:\test.txt", ios::out );  
  x.clear( );  
  TestFlags( x );  
  x.clear( ios::badbit | ios::failbit | ios::eofbit );  
  TestFlags( x );  
}  
  
```  
  
```Output  
  
0  
0  
0  
  
4  
2  
1   
```  
  
##  <a name="setstate"></a>  basic_ios::setstate  
 Establece marcas adicionales.  
  
```   
void setstate(iostate _State);
```  
  
### <a name="parameters"></a>Parámetros  
 `_State`  
 Marcas adicionales que se van a establecer.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro llama realmente a [clear](#clear)(_ *State* &#124; [rdstate](#rdstate)).  
  
### <a name="example"></a>Ejemplo  
  
```cpp    
// basic_ios_setstate.cpp  
// compile with: /EHsc  
#include <ios>  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
  bool b = cout.bad( );  
  cout << b << endl;   // Good  
  cout.clear( ios::badbit );  
  b = cout.bad( );  
  // cout.clear( );  
  cout << b << endl;   // Is bad, good  
  b = cout.fail( );  
  cout << b << endl;   // Not failed  
  cout.setstate( ios::failbit );  
  b = cout.fail( );  
  cout.clear( );  
  cout << b << endl;   // Is failed, good  
  return 0;  
}  
  
```  
  
```Output  
  
0  
1   
```  
  
##  <a name="set_rdbuf"></a>  basic_ios::set_rdbuf  
 Asigna un búfer de secuencia para que sea el búfer de lectura de este objeto de secuencia.  
  
```   
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)  
```  
  
### <a name="parameters"></a>Parámetros  
 `strbuf`  
 Búfer de flujo que se va a convertir en el búfer de lectura.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro protegida almacena `strbuf` en `stream buffer pointer`. No llama a `clear`.  
  
##  <a name="tie"></a>  basic_ios::tie  
 Se asegura de que una secuencia se procese antes que otra.  
  
```  
 
basic_ostream<Elem, Traits> *tie() const; 
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```  
  
### <a name="parameters"></a>Parámetros  
 `str`  
 Flujo.  
  
### <a name="return-value"></a>Valor devuelto  
 La primera función miembro devuelve el puntero de valor equivalente almacenado. La segunda función miembro almacena `str` en el puntero de valor equivalente y devuelve su anterior valor almacenado.  
  
### <a name="remarks"></a>Comentarios  
 `tie` provoca la sincronización de dos flujos, de modo que las operaciones de un flujo se producen una vez finalizadas las operaciones del otro.  
  
### <a name="example"></a>Ejemplo  
  En este ejemplo, al unir cin y cout, se garantiza que la cadena "Escriba un número:" pase a la consola antes de que el propio número se extraiga de cin. Esto elimina la posibilidad de que la cadena "Escriba un número:" siga estando en el búfer al leer el número, de modo que se asegure que el usuario realmente tiene algún mensaje al que deba responder. De forma predeterminada, cin y cout están unidos.  
  
```  
  
#include <ios>  
#include <iostream>  
  
int main( )  
{  
  using namespace std;  
  int i;  
  cin.tie( &cout );  
  cout << "Enter a number:";  
  cin >> i;  
}  
  
```  
  
##  <a name="traits_type"></a>  basic_ios::traits_type  
 Sinónimo del parámetro de plantilla **Traits**.  
  
```   
typedef Traits traits_type;  
```  
  
##  <a name="widen"></a>  basic_ios::widen  
 Busca el `char_type` equivalente a un determinado `char`.  
  
```   
char_type widen(char Char) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `Char`  
 Carácter que se va a convertir.  
  
### <a name="return-value"></a>Valor devuelto  
 Busca el `char_type` equivalente a un determinado `char`.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype**\< **E**> >([getloc](../standard-library/ios-base-class.md#getloc)). `widen`( `Char`).  
  
### <a name="example"></a>Ejemplo  
  
```cpp    
// basic_ios_widen.cpp  
// compile with: /EHsc  
#include <ios>  
#include <iostream>  
#include <wchar.h>  
  
int main( )  
{  
  using namespace std;  
  char *z = "Hello";  
  wchar_t y[2] = {0,0};  
  cout << z[0] << endl;  
  y[0] = wcout.widen( z[0] );  
  wcout << &y[0] << endl;  
}  
  
```  
  
##  <a name="swap"></a>  basic_ios::swap  
 Cambia los valores de este objeto `basic_ios` por los de otro objeto `basic_ios`. Pero no se intercambian los punteros a los búferes de flujo.  
  
```   
void swap(basic_ios&& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Objeto `basic_ios` que se usa para intercambiar valores.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro protegida intercambia todos los valores almacenados en `right` con `*this`, excepto el `stream buffer pointer` almacenado.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)

