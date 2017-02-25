---
title: "locale (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xlocale/std::locale"
  - "std::locale"
  - "std.locale"
  - "locale"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "locale (clase)"
ms.assetid: 7dd6d271-472d-4750-8fb5-ea8f55fbef62
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# locale (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase que describe un objeto de configuración regional que encapsula la información específica de la configuración regional como un conjunto de facetas que definen colectivamente un entorno traducido y adaptado concreto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class locale;  
```  
  
## <a name="remarks"></a>Comentarios  
 Una faceta es un puntero a un objeto de una clase derivada de la clase [faceta](#facet_class) que tiene un objeto público del formulario:  
  
```  
static locale::id id;  
```  
  
 Puede definir un conjunto abierto de estas facetas. También puede crear un objeto de configuración regional que designe un número arbitrario de facetas.  
  
 Los grupos predefinidos de estas facetas representan el [categorías de configuración regional](#locale__category) administradas tradicionalmente en la biblioteca estándar de C por la función `setlocale`.  
  
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
  
 Un objeto de clase locale clase también almacena un nombre de configuración regional como un objeto de clase [cadena](../Topic/%3Cstring%3E%20typedefs.md#string). Uso de un nombre de configuración regional no válido para construir una faceta o un objeto de configuración regional produce un objeto de clase [runtime_error](../standard-library/runtime-error-class.md). El nombre almacenado de la configuración regional es `"*"` si el objeto de configuración regional no puede estar seguro de que una configuración regional de estilo C corresponde exactamente a la representada por el objeto. De lo contrario, puede establecer una configuración regional coincidente dentro de la biblioteca estándar de C, para el objeto de configuración regional `_Loc`, llamando `setlocale`(LC_ALL `,` `_Loc`. [nombre](#locale__name)`().c_str()`).  
  
 En esta implementación, también puede llamar a la función miembro estática:  
  
```  
static locale empty();
```  
  
 para construir un objeto de configuración regional que no tiene ninguna faceta. También es una configuración regional transparente; Si las funciones de plantilla [has_facet](../Topic/%3Clocale%3E%20functions.md#has_facet) y [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) no se encuentra la faceta solicitada en una configuración regional transparente, consultan primero la configuración regional global y, a continuación, si es transparente, la configuración regional clásica. Así, puede escribir:  
  
```  
cout.imbue(locale::empty());
```  
  
 Las inserciones posteriores a [cout](../Topic/%3Ciostream%3E%20functions.md#cout) se realizan según el estado actual de la configuración regional global. Incluso puede escribir:  
  
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
|[configuración regional](#locale__locale)|Crea una configuración regional, una copia de una configuración regional o una copia de la configuración regional donde una faceta o una categoría se ha reemplazado por una faceta o una categoría de otra configuración regional.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[categoría](#locale__category)|Tipo entero que proporciona valores de máscara de bits para denotar familias de facetas estándar.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[combinar](#locale__combine)|Inserta una faceta de una configuración regional especificada en una configuración regional de destino.|  
|[nombre](#locale__name)|Devuelve el nombre de configuración regional almacenado.|  
  
### <a name="static-functions"></a>Funciones estáticas  
  
|||  
|-|-|  
|[clásico](#locale__classic)|La función miembro static devuelve un objeto de configuración regional que representa la configuración regional clásica de C.|  
|[global](#locale__global)|Restablece la configuración regional predeterminada del programa.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador! =](#locale__operator_neq)|Comprueba si dos configuraciones regionales son distintas.|  
|[operador)](#locale__operator__)|Compara dos objetos `basic_string`.|  
|[operador ==](#locale__operator_eq_eq)|Comprueba si dos configuraciones regionales son iguales.|  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[faceta](#facet_class)|Clase que actúa como clase base para todas las facetas de configuración regional.|  
|[Id.](#id_class)|La clase miembro proporciona un identificador único de faceta que se usa como índice para buscar facetas en una configuración regional.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< configuración regional>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namelocalecategorya-localecategory"></a><a name="locale__category"></a>  Locale:: Category  
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
 El tipo es un sinónimo de una `int` tipo que puede representar un grupo de elementos distintos de una máscara de bits, escriba local de clase locale o puede utilizarse para representar cualquiera de las categorías de configuración regional de C correspondientes. Los elementos son:  
  
- **COLLATE**, que corresponde a la categoría de C LC_COLLATE  
  
- **CType**, que corresponde a la categoría de C LC_CTYPE  
  
- **moneda**, que corresponde a la categoría de C LC_MONETARY  
  
- **numérico**, que corresponde a la categoría de C LC_NUMERIC  
  
- **tiempo**, que corresponde a la categoría de C LC_TIME  
  
- **mensajes**, que corresponde a la categoría de Posix LC_MESSAGES  
  
 Además, dos valores útiles son:  
  
- **Ninguno**, que corresponde a ninguna de las categorías de C  
  
- **todos los**, que corresponde a la unión de C de todas las categorías LC_ALL  
  
 Puede representar un grupo de categorías arbitrario mediante `OR` con estas constantes, como en **monetario** &#124; **tiempo**.  
  
##  <a name="a-namelocaleclassica-localeclassic"></a><a name="locale__classic"></a>  Locale:: Classic  
 La función miembro static devuelve un objeto de configuración regional que representa la configuración regional clásica de C.  
  
```  
static const locale& classic();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la configuración regional de C.  
  
### <a name="remarks"></a>Comentarios  
 La configuración regional clásica de C es Estados Unidos. Configuración regional de inglés ASCII dentro de la biblioteca estándar de C que se utiliza de forma implícita en los programas que no están internacionalizados.  
  
### <a name="example"></a>Ejemplo  
  
```  
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
  
##  <a name="a-namelocalecombinea-localecombine"></a><a name="locale__combine"></a>  Locale:: combine  
 Inserta una faceta de una configuración regional especificada en una configuración regional de destino.  
  
```  
template <class Facet>  
locale combine(const locale& _Loc) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Loc`  
 La configuración regional que contiene la faceta que se va a insertar en la configuración regional de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro devuelve un objeto de configuración regional que se reemplaza en o agrega al **\*Esto** la faceta `Facet` enumerados en `_Loc`.  
  
### <a name="example"></a>Ejemplo  
  
```  
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
  
##  <a name="a-namefacetclassa-facet-class"></a><a name="facet_class"></a>  Facet (clase)  
 Clase que actúa como clase base para todas las facetas de configuración regional.  
  
faceta de la clase {protegido: faceta explícita (size_t _Refs = 0); virtual ~ facet(); private: facet(const facet&) / / no definido void (operador) =(const facet&) / / no definido};  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que no puede copiar o asignar un objeto de faceta de la clase. Puede crear y destruir objetos derivados de la clase `locale::facet` pero no los objetos de la clase base correcta. Normalmente, se construye un objeto `_Myfac` deriva de faceta al construir una configuración regional, como en **localeloc**( `locale::classic`(), **nueva**`_Myfac`);  
  
 En tales casos, el constructor de la faceta de la clase base debe tener un cero `_Refs` argumento. Cuando el objeto ya no es necesario, se elimina. Por lo tanto, proporcione un _ es distinto de cero *Refs* argumento sólo en los pocos casos donde asume la responsabilidad de la duración del objeto.  
  
##  <a name="a-namelocaleglobala-localeglobal"></a><a name="locale__global"></a>  Locale:: global  
 Restablece la configuración regional predeterminada para el programa. Esto afecta a la configuración regional global de C y C++.  
  
```  
static locale global(const locale& _Loc);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Loc`  
 La configuración regional que se usará como la configuración regional predeterminada por el programa.  
  
### <a name="return-value"></a>Valor devuelto  
 La configuración regional anterior antes de que se ha restablecido la configuración regional predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Al inicio del programa, la configuración regional global es el mismo que la configuración regional clásica. El `global()` llamadas a función `setlocale( LC_ALL, loc.name. c_str())` para establecer una configuración regional coincidente en la biblioteca estándar de C++.  
  
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
  
##  <a name="a-nameidclassa-id-class"></a><a name="id_class"></a>  Id. de clase  
 La clase miembro proporciona un identificador único de faceta que se usa como índice para buscar facetas en una configuración regional.  
  
Id. de clase {protegido: ID; private: id(const id&) / / no definido void (operador) =(const id&) / / no definido};  
  
### <a name="remarks"></a>Comentarios  
 La clase de miembro describe el objeto de miembro estático requerido por cada faceta de configuración regional único. Tenga en cuenta que no puede copiar o asignar un objeto de clase **id**.  
  
##  <a name="a-namelocalelocalea-localelocale"></a><a name="locale__locale"></a>  Locale:: Locale  
 Crea una configuración regional, una copia de una configuración regional o una copia de la configuración regional donde una faceta o una categoría se ha reemplazado por una faceta o una categoría de otra configuración regional.  
  
```  
locale();

explicit locale(
    const char* _Locname,  
    category _Cat = all);

explicit locale(
    const string& _Locname);

locale(
    const locale& _Loc);

locale(
    const locale& _Loc,   
    const locale& _Other,  
    category _Cat);

locale(
    const locale& _Loc,   
    const char* _Locname,  
    category _Cat);

template <class Facet>  
locale(
 const locale& _Loc,   
    const Facet* _Fac);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Locname`  
 Nombre de una configuración regional.  
  
 `_Loc`  
 Una configuración regional que se va a copiar en la construcción de la nueva configuración regional.  
  
 `_Other`  
 Una configuración regional para seleccionar una categoría.  
  
 `_Cat`  
 La categoría que se sustituirá en la configuración regional construida.  
  
 `_Fac`  
 La faceta que se sustituirá en la configuración regional construida.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor inicializa el objeto para que coincida con la configuración regional global. El segundo y tercer constructor inicializa todas las categorías de configuración regional para tener un comportamiento coherente con el nombre de la configuración regional `_Locname`. Copian los constructores restantes `_Loc`, con las excepciones que se indican:  
  
 `locale(const locale& _Loc, const locale& _Other, category _Cat);`  
  
 reemplaza desde `_Other` estas facetas correspondiente a una categoría de C para que C & `_Cat` es distinto de cero.  
  
 `locale(const locale& _Loc, const char* _Locname, category _Cat);`  
  
 `locale(const locale& _Loc, const string& _Locname, category _Cat);`  
  
 reemplaza desde `locale(_Locname, _All)` estas facetas correspondiente a una categoría de C para que C & `_Cat`es distinto de cero.  
  
 `template<class Facet> locale(const locale& _Loc, Facet* _Fac);`  
  
 sustituye en (o se agrega al) `_Loc` la faceta `_Fac`, Si `_Fac` no es un puntero nulo.  
  
 Si un nombre de configuración regional `_Locname` es un puntero nulo o no válido, la función produce [runtime_error](../standard-library/runtime-error-class.md).  
  
### <a name="example"></a>Ejemplo  
  
```  
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
  
##  <a name="a-namelocalenamea-localename"></a><a name="locale__name"></a>  Locale:: Name  
 Devuelve el nombre de configuración regional almacenado.  
  
```  
string name() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Cadena que proporciona el nombre de la configuración regional.  
  
### <a name="example"></a>Ejemplo  
  
```  
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
  
##  <a name="a-namelocaleoperatorneqa-localeoperator"></a><a name="locale__operator_neq"></a>  Locale:: operator! =  
 Comprueba si dos configuraciones regionales son distintas.  
  
```  
bool operator!=(const locale& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 Una de las configuraciones regionales que puede probar la desigualdad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor booleano que es **true** si las configuraciones regionales no son copias de la misma configuración regional; **false** si las configuraciones regionales son copias de la misma configuración regional.  
  
### <a name="remarks"></a>Comentarios  
 Dos configuraciones regionales son iguales si son la misma configuración regional, si uno es una copia de la otra, o si tienen nombres idénticos.  
  
### <a name="example"></a>Ejemplo  
  
```  
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
  
##  <a name="a-namelocaleoperatora-localeoperator"></a><a name="locale__operator__"></a>  Locale::operator()  
 Compara dos objetos `basic_string`.  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,  
    const basic_string<CharType, Traits, Allocator>& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
 ` left`  
 Cadena izquierda.  
  
 ` right`  
 Cadena derecha.  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro devuelve:  
  
-   -1 si la primera secuencia compara menor que la segunda secuencia.  
  
-   + 1 si la segunda secuencia compara menor que la primera secuencia.  
  
-   0 si las secuencias son equivalentes.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro ejecuta eficazmente:  
  
```  
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) <0);
```  
  
 Por lo tanto, puede utilizar un objeto de configuración regional como un objeto de función.  
  
### <a name="example"></a>Ejemplo  
  
```  
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
  
##  <a name="a-namelocaleoperatoreqeqa-localeoperator"></a><a name="locale__operator_eq_eq"></a>  Locale:: operator ==  
 Comprueba si dos configuraciones regionales son iguales.  
  
```  
bool operator==(const locale& right) const;
```  
  
### <a name="parameters"></a>Parámetros  
 ` right`  
 Una de las configuraciones regionales para las pruebas de igualdad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor booleano que es **true** si las configuraciones regionales son copias de la misma configuración regional; **false** si las configuraciones regionales no son copias de la misma configuración regional.  
  
### <a name="remarks"></a>Comentarios  
 Dos configuraciones regionales son iguales si son la misma configuración regional, si uno es una copia de la otra, o si tienen nombres idénticos.  
  
### <a name="example"></a>Ejemplo  
  
```  
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
 [\< configuración regional>](../standard-library/locale.md)   
 [Páginas de códigos](../c-runtime-library/code-pages.md)   
 [Nombres de configuración regional, idiomas y cadenas de país o región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

