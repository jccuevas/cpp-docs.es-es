---
title: Clase locale | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocale/std::locale
- locale
- locale/std::locale::category
- locale/std::locale::combine
- locale/std::locale::name
- locale/std::locale::classic
- locale/std::locale::global
- locale/std::locale::operator( )
- locale/std::locale::facet
- locale/std::locale::id
dev_langs:
- C++
helpviewer_keywords:
- locale class
ms.assetid: 7dd6d271-472d-4750-8fb5-ea8f55fbef62
caps.latest.revision: 28
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
ms.openlocfilehash: 6e33e125d2689d37443bec58c5b01f5b7e72ccfd
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="locale-class"></a>locale (Clase)
La clase que describe un objeto de configuración regional que encapsula la información específica de la configuración regional como un conjunto de facetas que definen colectivamente un entorno traducido y adaptado concreto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class locale;  
```  
  
## <a name="remarks"></a>Comentarios  
 Una faceta es un puntero a un objeto de una clase derivada de la clase [facet](#facet_class) que tiene un objeto público con el formato:  
  
```  
static locale::id id;  
```  
  
 Puede definir un conjunto abierto de estas facetas. También puede crear un objeto de configuración regional que designe un número arbitrario de facetas.  
  
 Los grupos predefinidos de estas facetas representan las [categorías de configuración regional](#category) administradas tradicionalmente en la biblioteca estándar de C por la función `setlocale`.  
  
 La categoría collate (LC_COLLATE) incluye las facetas:  
  
```  
collate<char>  
collate<wchar_t>  
```  
  
 La categoría ctype (LC_CTYPE) incluye las facetas:  
  
```  
ctype<char>  
ctype<wchar_t>  
codecvt<char, char, mbstate_t>  
codecvt<wchar_t, char, mbstate_t>  
codecvt<char16_t, char, mbstate_t>  
codecvt<char32_t, char, mbstate_t>  
```  
  
 La categoría monetary (LC_MONETARY) incluye las facetas:  
  
```  
moneypunct<char, false>  
moneypunct<wchar_t, false>  
moneypunct<char, true>  
moneypunct<wchar_t, true>  
money_get<char, istreambuf_iterator<char>>  
money_get<wchar_t, istreambuf_iterator<wchar_t>>  
money_put<char, ostreambuf_iterator<char>>  
money_put<wchar_t, ostreambuf_iterator<wchar_t>>  
```  
  
 La categoría numeric (LC_NUMERIC) incluye las facetas:  
  
```  
num_get<char, istreambuf_iterator<char>>  
num_get<wchar_t, istreambuf_iterator<wchar_t>>  
num_put<char, ostreambuf_iterator<char>>  
num_put<wchar_t, ostreambuf_iterator<wchar_t>>  
numpunct<char>  
numpunct<wchar_t>  
```  
  
 La categoría time (LC_TIME) incluye las facetas:  
  
```  
time_get<char, istreambuf_iterator<char>>  
time_get<wchar_t, istreambuf_iterator<wchar_t>>  
time_put<char, ostreambuf_iterator<char>>  
time_put<wchar_t, ostreambuf_iterator<wchar_t>>  
```  
  
 La categoría messages (LC_MESSAGES) incluye las facetas:  
  
```  
messages<char>  
messages<wchar_t>  
```  
  
 (La última categoría es necesaria para Posix, pero no para el estándar de C).  
  
 Las clases iostreams usan algunas de estas facetas predefinidas para controlar la conversión de valores numéricos a y desde secuencias de texto.  
  
 Un objeto de clase locale clase también almacena un nombre de configuración regional como un objeto de la clase [string](../standard-library/string-typedefs.md#string). El uso de un nombre no válido de configuración regional para construir una faceta o un objeto de configuración regional produce un objeto de la clase [runtime_error](../standard-library/runtime-error-class.md). El nombre almacenado de la configuración regional es `"*"` si el objeto de configuración regional no puede estar seguro de que una configuración regional de estilo C corresponde exactamente a la representada por el objeto. De lo contrario, puede establecer una configuración regional coincidente dentro de la biblioteca estándar de C para el objeto de configuración regional `Loc` mediante una llamada a `setlocale`(LC_ALL `,` `Loc`. [name](#name)`().c_str()`).  
  
 En esta implementación, también puede llamar a la función miembro estática:  
  
```  
static locale empty();
```  
  
 para construir un objeto de configuración regional que no tiene ninguna faceta. También es una configuración regional transparente; si las funciones de plantilla [has_facet](../standard-library/locale-functions.md#has_facet) y [use_facet](../standard-library/locale-functions.md#use_facet) no encuentran la faceta solicitada en una configuración regional transparente, consultan primero la configuración regional global y después, si es transparente, la configuración regional clásica. Así, puede escribir:  
  
```  
cout.imbue(locale::empty());
```  
  
Las inserciones posteriores a [cout](../standard-library/iostream.md#cout) se realizan según el estado actual de la configuración regional global. Incluso puede escribir:  
  
```  
locale loc(locale::empty(),
    locale::classic(),  
    locale::numeric);

cout.imbue(loc);
```   
  
 Las reglas de formato numérico para las inserciones posteriores a `cout` son las mismas que en la configuración regional de C, incluso aunque la configuración regional global proporcione reglas que cambian para insertar fechas y cantidades monetarias.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[locale](#locale)|Crea una configuración regional, una copia de una configuración regional o una copia de la configuración regional donde una faceta o una categoría se ha reemplazado por una faceta o una categoría de otra configuración regional.|  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[category](#category)|Tipo entero que proporciona valores de máscara de bits para denotar familias de facetas estándar.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[combine](#combine)|Inserta una faceta de una configuración regional especificada en una configuración regional de destino.|  
|[name](#name)|Devuelve el nombre de configuración regional almacenado.|  
  
### <a name="static-functions"></a>Funciones estáticas  
  
|||  
|-|-|  
|[classic](#classic)|La función miembro static devuelve un objeto de configuración regional que representa la configuración regional clásica de C.|  
|[global](#global)|Restablece la configuración regional predeterminada del programa.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator!=](#op_neq)|Comprueba si dos configuraciones regionales son distintas.|  
|[operator( )](#op_call)|Compara dos objetos `basic_string`.|  
|[operator==](#op_eq_eq)|Comprueba si dos configuraciones regionales son iguales.|  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[facet](#facet_class)|Clase que actúa como clase base para todas las facetas de configuración regional.|  
|[id](#id_class)|La clase miembro proporciona un identificador único de faceta que se usa como índice para buscar facetas en una configuración regional.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<locale>  
  
 **Espacio de nombres:** std  
  
##  <a name="category"></a>  locale::category  
 Tipo entero que proporciona valores de máscara de bits para denotar familias de facetas estándar.  
  
```  
typedef int category;  
static const int collate = LC_COLLATE;  
static const int ctype = LC_CTYPE;  
static const int monetary = LC_MONETARY;  
static const int numeric = LC_NUMERIC;  
static const int time = LC_TIME;  
static const int messages = LC_MESSAGES;  
static const int all = LC_ALL;  
static const int none = 0;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es sinónimo de un tipo `int` que puede representar un grupo de elementos distintos de una configuración regional de tipo de máscara de bits en una configuración regional de clase o puede usarse para representar cualquiera de las categorías de configuración regional de C correspondientes. Los elementos son:  
  
- **collate**, que se corresponde con la categoría LC_COLLATE de C  
  
- **ctype**, que se corresponde con la categoría LC_CTYPE de C  
  
- **monetary**, que se corresponde con la categoría LC_MONETARY de C  
  
- **numeric**, que se corresponde con la categoría LC_NUMERIC de C  
  
- **time**, que se corresponde con la categoría LC_TIME de C  
  
- **messages**, que se corresponde con la categoría LC_MESSAGES de Posix  
  
 Además, dos valores útiles son:  
  
- **none**, que no se corresponde con ninguna de las categorías de C  
  
- **all**, que se corresponde con la unión de C de todas las categorías LC_ALL  
  
 Puede representar un grupo arbitrario de categorías mediante `OR` con estas constantes, como en **monetary** &#124; **time**.  
  
##  <a name="classic"></a>  locale::classic  
 La función miembro static devuelve un objeto de configuración regional que representa la configuración regional clásica de C.  
  
```  
static const locale& classic();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia a la configuración regional de C.  
  
### <a name="remarks"></a>Comentarios  
 Configuración regional de C clásica de los Estados Unidos. Configuración regional ASCII de inglés dentro de la biblioteca estándar de C que se usa de forma implícita en los programas que no están internacionalizados.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// locale_classic.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string>  
#include <locale>  
  
using namespace std;  
  
int main( )   
{  
   locale loc1( "german" );  
   locale loc2 = locale::global( loc1 );  
   cout << "The name of the previous locale is: " << loc2.name( )  
        << "." << endl;  
   cout << "The name of the current locale is: " << loc1.name( )   
        << "." << endl;  
  
   if (loc2 == locale::classic( ) )  
      cout << "The previous locale was classic." << endl;  
   else  
      cout << "The previous locale was not classic." << endl;  
  
   if (loc1 == locale::classic( ) )  
      cout << "The current locale is classic." << endl;  
   else  
      cout << "The current locale is not classic." << endl;  
}  
```  
  
```Output  
The name of the previous locale is: C.  
The name of the current locale is: German_Germany.1252.  
The previous locale was classic.  
The current locale is not classic.  
```  
  
##  <a name="combine"></a>  locale::combine  
 Inserta una faceta de una configuración regional especificada en una configuración regional de destino.  
  
```  
template <class Facet>  
locale combine(const locale& Loc) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `Loc`  
 Configuración regional que contiene la faceta que se va a insertar en la configuración regional de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro devuelve un objeto de configuración regional que reemplaza o agrega a **\*this** la faceta `Facet` indicada en `Loc`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// locale_combine.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <tchar.h>  
using namespace std;  
  
int main() {  
   locale loc ( "German_germany" );  
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s; it comes before z in the German alphabet  
   _TCHAR * s2 = _T("Das ist weizzz.");  
   int result1 = use_facet<collate<_TCHAR> > ( loc ).  
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );  
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;  
  
   locale loc2 ( "C" );  
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).  
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );  
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;  
  
   locale loc3 = loc2.combine<collate<_TCHAR> > (loc);  
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).  
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );  
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;  
}  
```  
  
##  <a name="facet_class"></a>  Clase facet  
 Clase que actúa como clase base para todas las facetas de configuración regional.  

```    
class facet { 
protected:    
    explicit facet(size_t _Refs = 0);
   virtual ~facet();
private:    
   facet(const facet&)
   // not defined void operator=(const facet&)
     // not defined    
};  
```  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que no puede copiar o asignar un objeto de la clase facet. Puede crear y destruir objetos derivados de la clase `locale::facet`, pero no los objetos de la clase base correcta. Normalmente, se construye un objeto `_Myfac` derivado de facet al construir una configuración regional, como en **localeloc**( `locale::classic`( ), **new**`_Myfac`);  
  
 En tales casos, el constructor de la clase base facet debe tener un argumento `_Refs` cero. Cuando el objeto ya no es necesario, se elimina. Por lo tanto, proporcione un argumento _ *Refs* distinto de cero solo en los pocos casos en los que se haga responsable de la duración del objeto.  
  
##  <a name="global"></a>  locale::global  
 Restablece la configuración regional predeterminada del programa. Esto afecta a la configuración regional global de C y C++.  
  
```  
static locale global(const locale& Loc);
```  
  
### <a name="parameters"></a>Parámetros  
 `Loc`  
 Configuración regional que el programa usará como configuración regional predeterminada.  
  
### <a name="return-value"></a>Valor devuelto  
 Configuración regional anterior al restablecimiento de la configuración regional predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Al inicio del programa, la configuración regional global es igual que la configuración regional clásica. La función `global()` llama a `setlocale( LC_ALL, loc.name. c_str())` para establecer una configuración regional coincidente en la biblioteca estándar de C++.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// locale_global.cpp  
// compile by using: /EHsc  
#include <locale>  
#include <iostream>  
#include <tchar.h>  
using namespace std;  
  
int main( )  
{  
   locale loc ( "German_germany" );  
   locale loc1;  
   cout << "The initial locale is: " << loc1.name( ) << endl;  
   locale loc2 = locale::global ( loc );  
   locale loc3;  
   cout << "The current locale is: " << loc3.name( ) << endl;  
   cout << "The previous locale was: " << loc2.name( ) << endl;  
}  
```  
  
```Output  
The initial locale is: C  
The current locale is: German_Germany.1252  
The previous locale was: C  
```  
  
##  <a name="id_class"></a>  Clase id  
 La clase miembro proporciona un identificador único de faceta que se usa como índice para buscar facetas en una configuración regional.  
  
class id { protected:    id(); private:    id(const id&) // not defined void operator=(const id&)  // not defined    };  
  
### <a name="remarks"></a>Comentarios  
 La clase de miembro describe el objeto de miembro estático requerido por cada faceta de configuración regional única. Tenga en cuenta que no puede copiar o asignar un objeto de la clase **id**.  
  
##  <a name="locale"></a>  locale::locale  
 Crea una configuración regional, una copia de una configuración regional o una copia de la configuración regional donde una faceta o una categoría se ha reemplazado por una faceta o una categoría de otra configuración regional.  
  
```  
locale();

explicit locale(const char* Locname, category Cat = all);
explicit locale(const string& Locname);
locale( const locale& Loc);
locale(const locale& Loc, const locale& Other, category Cat);
locale(const locale& Loc, const char* Locname, category Cat);

template <class Facet>  
locale(const locale& Loc, const Facet* Fac);
```  
  
### <a name="parameters"></a>Parámetros  
 `Locname`  
 Nombre de una configuración regional.  
  
 `Loc`  
 Configuración regional que se va a copiar en la construcción de la nueva configuración regional.  
  
 `Other`  
 Configuración regional de la que se va a seleccionar una categoría.  
  
 `Cat`  
 Categoría que se va a sustituir en la configuración regional construida.  
  
 `Fac`  
 Faceta que se va a sustituir en la configuración regional construida.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor inicializa el objeto para que coincida con la configuración regional global. El segundo y el tercer constructor inicializan todas las categorías de configuración regional para que tengan un comportamiento coherente con el nombre de la configuración regional `Locname`. Los demás constructores copian `Loc`, con las excepciones que se indican a continuación:  
  
 `locale(const locale& Loc, const locale& Other, category Cat);`  
  
 reemplaza en `Other` las facetas que se corresponden con una categoría de C para la cual C & `Cat` es distinto de cero.  
  
 `locale(const locale& Loc, const char* Locname, category Cat);`  
  
 `locale(const locale& Loc, const string& Locname, category Cat);`  
  
 reemplaza en `locale(Locname, _All)` las facetas que se corresponden con una categoría de C para la cual C & `Cat` es distinto de cero.  
  
 `template<class Facet> locale(const locale& Loc, Facet* Fac);`  
  
 reemplaza (o se agrega) en `Loc` la faceta `Fac` si `Fac` no es un puntero nulo.  
  
 Si un nombre de configuración regional `Locname` es un puntero nulo o no válido, la función produce un [runtime_error](../standard-library/runtime-error-class.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// locale_locale.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <tchar.h>  
using namespace std;  
  
int main( ) {  
  
   // Second constructor  
   locale loc ( "German_germany" );  
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet  
   _TCHAR * s2 = _T("Das ist weizzz.");  
   int result1 = use_facet<collate<_TCHAR> > ( loc ).  
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );  
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;  
  
   // The first (default) constructor  
   locale loc2;  
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).  
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );  
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;  
  
   // Third constructor  
   locale loc3 (loc2,loc, _M_COLLATE );  
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).  
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );  
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;  
  
   // Fourth constructor  
   locale loc4 (loc2, "German_Germany", _M_COLLATE );  
   int result4 = use_facet<collate<_TCHAR> > ( loc4 ).  
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );  
   cout << isalpha (_T ( '\x00df' ), loc4 ) << result4 << endl;  
}  
```  
  
##  <a name="name"></a>  locale::name  
 Devuelve el nombre de configuración regional almacenado.  
  
```  
string name() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Cadena que proporciona el nombre de la configuración regional.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// locale_name.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string>  
#include <locale>  
  
using namespace std;  
  
int main( )   
{  
   locale loc1( "german" );  
   locale loc2 = locale::global( loc1 );  
   cout << "The name of the previous locale is: "   
        << loc2.name( ) << "." << endl;  
   cout << "The name of the current locale is: "   
        << loc1.name( ) << "." << endl;  
}  
```  
  
```Output  
The name of the previous locale is: C.  
The name of the current locale is: German_Germany.1252.  
```  
  
##  <a name="op_neq"></a>  locale::operator!=  
 Comprueba si dos configuraciones regionales son distintas.  
  
```  
bool operator!=(const locale& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Una de las configuraciones regionales cuya desigualdad se va a comprobar.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor booleano que es **true** si las configuraciones regionales no son copias de la misma configuración regional; **false** si las configuraciones regionales son copias de la misma configuración regional.  
  
### <a name="remarks"></a>Comentarios  
 Dos configuraciones regionales son iguales si son la misma configuración regional, si una es una copia de la otra o si tienen nombres idénticos.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// locale_op_ne.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string>  
#include <locale>  
  
using namespace std;  
  
int main( )   
{  
   locale loc1( "German_Germany" );  
   locale loc2( "German_Germany" );  
   locale loc3( "English" );  
  
   if ( loc1 != loc2 )  
      cout << "locales loc1 (" << loc1.name( )  
      << ") and\n loc2 (" << loc2.name( ) << ") are not equal." << endl;  
   else  
      cout << "locales loc1 (" << loc1.name( )  
      << ") and\n loc2 (" << loc2.name( ) << ") are equal." << endl;  
  
   if ( loc1 != loc3 )  
      cout << "locales loc1 (" << loc1.name( )  
      << ") and\n loc3 (" << loc3.name( ) << ") are not equal." << endl;  
   else  
      cout << "locales loc1 (" << loc1.name( )  
      << ") and\n loc3 (" << loc3.name( ) << ") are equal." << endl;  
}  
```  
  
```Output  
locales loc1 (German_Germany.1252) and  
 loc2 (German_Germany.1252) are equal.  
locales loc1 (German_Germany.1252) and  
 loc3 (English_United States.1252) are not equal.  
```  
  
##  <a name="op_call"></a>  locale::operator()  
 Compara dos objetos `basic_string`.  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,  
    const basic_string<CharType, Traits, Allocator>& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `left`  
 Cadena izquierda.  
  
 `right`  
 Cadena derecha.  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro devuelve:  
  
-   -1 si la primera secuencia compara menos que la segunda secuencia.  
  
-   +1 si la segunda secuencia compara menos que la primera secuencia.  
  
-   0 si las secuencias son equivalentes.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro ejecuta eficazmente:  
  
```  
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```  
  
 Por lo tanto, puede usar un objeto de configuración regional como un objeto de función.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// locale_op_compare.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string>  
#include <locale>  
  
int main( )   
{  
   using namespace std;  
   wchar_t *sa = L"ztesting";  
   wchar_t *sb = L"\0x00DFtesting";  
   basic_string<wchar_t> a( sa );  
   basic_string<wchar_t> b( sb );  
  
   locale loc( "German_Germany" );  
   cout << loc( a,b ) << endl;  
  
   const collate<wchar_t>& fac = use_facet<collate<wchar_t> >( loc );  
   cout << ( fac.compare( sa, sa + a.length( ),  
       sb, sb + b.length( ) ) < 0) << endl;  
}  
```  
  
```Output  
0  
0  
```  
  
##  <a name="op_eq_eq"></a>  locale::operator==  
 Comprueba si dos configuraciones regionales son iguales.  
  
```  
bool operator==(const locale& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Una de las configuraciones regionales cuya igualdad se va a comprobar.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor booleano que es **true** si las configuraciones regionales son copias de la misma configuración regional; **false** si las configuraciones regionales no son copias de la misma configuración regional.  
  
### <a name="remarks"></a>Comentarios  
 Dos configuraciones regionales son iguales si son la misma configuración regional, si una es una copia de la otra o si tienen nombres idénticos.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// locale_op_eq.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string>  
#include <locale>  
  
using namespace std;  
  
int main( )   
{  
   locale loc1( "German_Germany" );  
   locale loc2( "German_Germany" );  
   locale loc3( "English" );  
  
   if ( loc1 == loc2 )  
      cout << "locales loc1 (" << loc1.name( )  
      << ")\n and loc2 (" << loc2.name( ) << ") are equal."   
      << endl;  
   else  
      cout << "locales loc1 (" << loc1.name( )  
      << ")\n and loc2 (" << loc2.name( ) << ") are not equal."   
      << endl;  
  
   if ( loc1 == loc3 )  
      cout << "locales loc1 (" << loc1.name( )  
      << ")\n and loc3 (" << loc3.name( ) << ") are equal."   
      << endl;  
   else  
      cout << "locales loc1 (" << loc1.name( )  
      << ")\n and loc3 (" << loc3.name( ) << ") are not equal."   
      << endl;  
}  
```  
  
```Output  
locales loc1 (German_Germany.1252)  
 and loc2 (German_Germany.1252) are equal.  
locales loc1 (German_Germany.1252)  
 and loc3 (English_United States.1252) are not equal.  
```  
  
## <a name="see-also"></a>Vea también  
 [<locale>](../standard-library/locale.md)   
 [Páginas de códigos](../c-runtime-library/code-pages.md)   
 [Nombres de configuración regional, idiomas y cadenas de país/región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)


