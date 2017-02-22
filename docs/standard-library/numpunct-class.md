---
title: "numpunct (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xlocnum/std::numpunct"
  - "std::numpunct"
  - "numpunct"
  - "std.numpunct"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "numpunct (clase)"
ms.assetid: 73fb93cc-ac11-4c98-987c-bfa6267df596
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# numpunct (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de plantilla que describe un objeto que puede actuar como faceta de la configuración regional para describir las secuencias de tipo `CharType` usadas para representar información sobre el formato y la puntuación de expresiones numéricas y booleanas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class CharType>  
class numpunct : public locale::facet;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `CharType`  
 Tipo usado dentro de un programa para codificar los caracteres de una configuración regional.  
  
## <a name="remarks"></a>Comentarios  
 Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento para tener acceso a su valor almacenado almacena un valor positivo único en **id.**  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[numpunct](#numpunct__numpunct)|Constructor para los objetos de tipo `numpunct`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#numpunct__char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|  
|[STRING_TYPE](#numpunct__string_type)|Tipo que describe una cadena que contiene caracteres de tipo `CharType`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[decimal_point](#numpunct__decimal_point)|Devuelve un elemento específico de la configuración regional que se va a usar como separador decimal.|  
|[do_decimal_point](#numpunct__do_decimal_point)|Función miembro virtual protegida a la que se llama para devolver un elemento específico de la configuración regional que se va a usar como separador decimal.|  
|[do_falsename](#numpunct__do_falsename)|Función miembro virtual protegida a la que se llama para devolver una cadena que se va a usar como representación de texto del valor `false`.|  
|[do_grouping](#numpunct__do_grouping)|Función miembro virtual protegida a la que se llama para devolver una regla específica de la configuración regional con el fin de determinar cómo se agrupan los dígitos a la izquierda de cualquier separador decimal.|  
|[do_thousands_sep](#numpunct__do_thousands_sep)|Función miembro virtual protegida a la que se llama para devolver un elemento específico de la configuración regional que se va a usar como separador de miles.|  
|[do_truename](#numpunct__do_truename)|Función miembro virtual protegida a la que se llama para devolver una cadena que se va a usar como representación de texto del valor `true`.|  
|[falsename](#numpunct__falsename)|Devuelve una cadena que se va a usar como representación de texto del valor `false`.|  
|[agrupación](#numpunct__grouping)|Devuelve una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda del separador decimal.|  
|[thousands_sep](#numpunct__thousands_sep)|Devuelve un elemento específico de la configuración regional que se va a usar como separador de miles.|  
|[truename](#numpunct__truename)|Devuelve una cadena que se va a usar como representación de texto del valor `true`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< configuración regional>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namenumpunctchartypea-numpunctchartype"></a><a name="numpunct__char_type"></a>  numpunct:: char_type  
 Tipo que se usa para describir un carácter empleado por una configuración regional.  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **CharType.**  
  
##  <a name="a-namenumpunctdecimalpointa-numpunctdecimalpoint"></a><a name="numpunct__decimal_point"></a>  numpunct:: decimal_point  
 Devuelve un elemento específico de la configuración regional que se va a usar como separador decimal.  
  
```  
CharType decimal_point() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un elemento de configuración regional a usar como separador decimal.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [do_decimal_point](#numpunct__do_decimal_point).  
  
### <a name="example"></a>Ejemplo  
  
```  
// numpunct_decimal_point.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const numpunct <char> &npunct =   
   use_facet <numpunct <char> >( loc);  
   cout << loc.name( ) << " decimal point "<<   
   npunct.decimal_point( ) << endl;  
   cout << loc.name( ) << " thousands separator "   
   << npunct.thousands_sep( ) << endl;  
};  
```  
  
```Output  
German_Germany.1252 decimal point ,  
German_Germany.1252 thousands separator .  
```  
  
##  <a name="a-namenumpunctdodecimalpointa-numpunctdodecimalpoint"></a><a name="numpunct__do_decimal_point"></a>  numpunct:: do_decimal_point  
 Función miembro virtual protegida a la que se llama para devolver un elemento específico de la configuración regional que se va a usar como separador decimal.  
  
```  
virtual CharType do_decimal_point() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un elemento de configuración regional a usar como separador decimal.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [decimal_point](#numpunct__decimal_point), donde se llama a la función miembro virtual `decimal_point`.  
  
##  <a name="a-namenumpunctdofalsenamea-numpunctdofalsename"></a><a name="numpunct__do_falsename"></a>  numpunct:: do_falsename  
 La función miembro virtual protegida devuelve una secuencia que se utilizará como una representación de texto del valor **false**.  
  
```  
virtual string_type do_falsename() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una cadena que contiene una secuencia que se utilizará como una representación de texto del valor **false**.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve la cadena "false" para representar el valor **false** en todas las configuraciones regionales.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [falsename](#numpunct__falsename), donde se llama a la función miembro virtual `falsename`.  
  
##  <a name="a-namenumpunctdogroupinga-numpunctdogrouping"></a><a name="numpunct__do_grouping"></a>  numpunct:: do_grouping  
 Función miembro virtual protegida a la que se llama para devolver una regla específica de la configuración regional con el fin de determinar cómo se agrupan los dígitos a la izquierda de cualquier separador decimal.  
  
```  
virtual string do_grouping() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda del separador decimal.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro virtual protegida devuelve una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda de cualquier separador decimal. La codificación es el mismo que para **lconv::grouping**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [agrupación](#numpunct__grouping), donde se llama a la función miembro virtual **agrupación**.  
  
##  <a name="a-namenumpunctdothousandssepa-numpunctdothousandssep"></a><a name="numpunct__do_thousands_sep"></a>  numpunct:: do_thousands_sep  
 Función miembro virtual protegida a la que se llama para devolver un elemento específico de la configuración regional que se va a usar como separador de miles.  
  
```  
virtual CharType do_thousands_sep() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un elemento específico de la configuración regional que se va a usar como separador de miles.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro virtual protegida devuelve un elemento específico de la configuración regional de tipo **CharType** a utilizar como separador de grupos a la izquierda del separador decimal.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [thousands_sep](#numpunct__thousands_sep), donde se llama a la función miembro virtual `thousands_sep`.  
  
##  <a name="a-namenumpunctdotruenamea-numpunctdotruename"></a><a name="numpunct__do_truename"></a>  numpunct:: do_truename  
 Una función miembro virtual que se llama para devolver una cadena que se utiliza como una representación de texto del valor protegida **true**.  
  
```  
virtual string_type do_truename() const;
```  
  
### <a name="remarks"></a>Comentarios  
 Una cadena que se utiliza como una representación de texto del valor **true**.  
  
 Todas las configuraciones regionales devuelven una cadena "true" para representar el valor **true**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [truename](#numpunct__truename), donde se llama a la función miembro virtual `truename`.  
  
##  <a name="a-namenumpunctfalsenamea-numpunctfalsename"></a><a name="numpunct__falsename"></a>  numpunct:: falsename  
 Devuelve una cadena que se utiliza como una representación de texto del valor **false**.  
  
```  
string_type falsename() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una cadena que contiene una secuencia de **CharType**para utilizar como una representación de texto del valor **false**.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve la cadena "false" para representar el valor **false** en todas las configuraciones regionales.  
  
 La función miembro devuelve [do_falsename](#numpunct__do_falsename).  
  
### <a name="example"></a>Ejemplo  
  
```  
// numpunct_falsename.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "English" );  
  
   const numpunct <char> &npunct = use_facet <numpunct <char> >( loc );  
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;  
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;  
  
   locale loc2( "French" );  
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >(loc2);  
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;  
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;  
}  
```  
  
```Output  
English_United States.1252 truename true  
English_United States.1252 falsename false  
French_France.1252 truename true  
French_France.1252 falsename false  
```  
  
##  <a name="a-namenumpunctgroupinga-numpunctgrouping"></a><a name="numpunct__grouping"></a>  numpunct:: Grouping  
 Devuelve una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda del separador decimal.  
  
```  
string grouping() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una regla específica de la configuración regional para determinar cómo se agrupan los dígitos a la izquierda del separador decimal.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [do_grouping](#numpunct__do_grouping).  
  
### <a name="example"></a>Ejemplo  
  
```  
// numpunct_grouping.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany");  
  
   const numpunct <char> &npunct =   
       use_facet < numpunct <char> >( loc );  
   for (unsigned int i = 0; i < npunct.grouping( ).length( ); i++)  
   {  
      cout << loc.name( ) << " international grouping:\n the "  
           << i <<"th group to the left of the radix character "  
           << "is of size " << (int)(npunct.grouping ( )[i])   
           << endl;  
   }  
}  
```  
  
```Output  
German_Germany.1252 international grouping:  
 the 0th group to the left of the radix character is of size 3  
```  
  
##  <a name="a-namenumpunctnumpuncta-numpunctnumpunct"></a><a name="numpunct__numpunct"></a>  numpunct:: numpunct  
 Constructor para los objetos de tipo `numpunct`.  
  
```  
explicit numpunct(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Refs`  
 Valor entero que se utiliza para especificar el tipo de administración de memoria para el objeto.  
  
### <a name="remarks"></a>Comentarios  
 Los valores posibles de la `_Refs` parámetro y su importancia son:  
  
-   0: la duración del objeto administra las configuraciones regionales que lo contienen.  
  
-   1: se debe administrar manualmente la duración del objeto.  
  
-   \> 0: no se definen estos valores.  
  
 No hay ejemplos directos son posibles, porque está protegido el destructor.  
  
 El constructor inicializa su objeto base con **locale::**[faceta](../standard-library/locale-class.md#facet_class)( `_Refs`).  
  
##  <a name="a-namenumpunctstringtypea-numpunctstringtype"></a><a name="numpunct__string_type"></a>  numpunct:: STRING_TYPE  
 Un tipo que describe una cadena que contiene caracteres de tipo **CharType**.  
  
```  
typedef basic_string<CharType, Traits, Allocator> string_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [basic_string](../standard-library/basic-string-class.md) cuyos objetos pueden almacenar copias de las secuencias de puntuación.  
  
##  <a name="a-namenumpunctthousandssepa-numpunctthousandssep"></a><a name="numpunct__thousands_sep"></a>  numpunct:: thousands_sep  
 Devuelve un elemento específico de la configuración regional que se va a usar como separador de miles.  
  
```  
CharType thousands_sep() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un elemento de configuración regional que se usará como miles separador.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [do_thousands_sep](#numpunct__do_thousands_sep).  
  
### <a name="example"></a>Ejemplo  
  
```  
// numpunct_thou_sep.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   const numpunct <char> &npunct =   
   use_facet < numpunct < char > >( loc );  
   cout << loc.name( ) << " decimal point "<<   
   npunct.decimal_point( ) << endl;  
   cout << loc.name( ) << " thousands separator "   
   << npunct.thousands_sep( ) << endl;  
};  
```  
  
```Output  
German_Germany.1252 decimal point ,  
German_Germany.1252 thousands separator .  
```  
  
##  <a name="a-namenumpuncttruenamea-numpuncttruename"></a><a name="numpunct__truename"></a>  numpunct:: truename  
 Devuelve una cadena que se utiliza como una representación de texto del valor **true**.  
  
```  
string_type falsename() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una cadena que se utiliza como una representación de texto del valor **true**.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [do_truename](#numpunct__do_truename).  
  
 Todas las configuraciones regionales devuelven una cadena "true" para representar el valor **true**.  
  
### <a name="example"></a>Ejemplo  
  
```  
// numpunct_truename.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "English" );  
  
   const numpunct < char> &npunct = use_facet <numpunct <char> >( loc );  
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;  
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;  
  
   locale loc2("French");  
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >( loc2 );  
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;  
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;  
}  
```  
  
```Output  
English_United States.1252 truename true  
English_United States.1252 falsename false  
French_France.1252 truename true  
French_France.1252 falsename false  
```  
  
## <a name="see-also"></a>Vea también  
 [\< configuración regional>](../standard-library/locale.md)   
 [Facet (clase)](../standard-library/locale-class.md#facet_class)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

