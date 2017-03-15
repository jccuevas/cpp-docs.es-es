---
title: "num_put (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::num_put"
  - "xlocnum/std::num_put"
  - "num_put"
  - "std.num_put"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "num_put (clase)"
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# num_put (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de plantilla que describe un objeto que puede actuar como una faceta de la configuración regional para controlar las conversiones de valores numéricos en secuencias de tipo `CharType`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class CharType,  
    class OutputIterator = ostreambuf_iterator<CharType>>  
class num_put : public locale::facet;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `CharType`  
 Tipo usado dentro de un programa para codificar los caracteres de una configuración regional.  
  
 `OutputIterator`  
 Tipo de iterador en el que las funciones numeric put escriben sus resultados.  
  
## <a name="remarks"></a>Comentarios  
 Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento para tener acceso a su valor almacenado almacena un valor positivo único en **id.**  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[num_put](#num_put__num_put)|Constructor para los objetos de tipo `num_put`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#num_put__char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|  
|[iter_type](#num_put__iter_type)|Tipo que describe un iterador de salida.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[do_put](#num_put__do_put)|Función virtual a la que se llama a para convertir un número en una secuencia de `CharType` que representa el número con formato para una configuración regional especificada.|  
|[PUT](#num_put__put)|Convierte un número en una secuencia de `CharType` que representa el número con formato para una configuración regional especificada.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< configuración regional>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namenumputchartypea-numputchartype"></a><a name="num_put__char_type"></a>  num_put:: char_type  
 Tipo que se usa para describir un carácter empleado por una configuración regional.  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **CharType**.  
  
##  <a name="a-namenumputdoputa-numputdoput"></a><a name="num_put__do_put"></a>  num_put:: do_put  
 Una función virtual que se llama para convertir un número en una secuencia de **CharType**que representa el número con formato para una configuración regional concreta.  
  
```  
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    bool val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    unsigned long val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    double val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long double val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const void* val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const long long val) const;

virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const unsigned long long val) const;
```  
  
### <a name="parameters"></a>Parámetros  
 ` next`  
 Un iterador que direcciona el primer elemento de la cadena insertada.  
  
 `_Iosbase`  
 Especifica la secuencia que contiene la configuración regional con la faceta de numpunct usa para enfatice los resultados y las marcas para dar formato a la salida.  
  
 `_Fill`  
 Carácter que se utiliza para el espaciado.  
  
 ` val`  
 El número o tipo booleano que se va de salida.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de salida generado de la posición más allá del último elemento de las direcciones.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro protegido virtual genera elementos secuenciales, empezando por ` next` para producir un campo de salida entero del valor de ` val`. La función devuelve un iterador que designa el lugar siguiente para insertar un elemento más allá del campo de salida entero generado.  
  
 El campo de salida entero generado por las mismas reglas usadas por las funciones de impresión para generar una serie de `char` elementos en un archivo. Se supone que cada elemento char se asignan a un elemento de tipo equivalente **CharType** mediante una asignación simple, uno a uno. Cuando una función de impresión rellena un campo con espacios o los dígitos 0, sin embargo, `do_put` en su lugar utiliza **relleno**. La especificación de conversión de impresión equivalente se determina como sigue:  
  
-   Si **iosbase**. [marcas de](../standard-library/ios-base-class.md#ios_base__flags) & `ios_base::basefield` == `ios_base::`[oct](../Topic/%3Cios%3E%20functions.md#oct), la especificación de conversión es **lo**.  
  
-   Si **iosbase.flags** & **ios_base:: basefield** == `ios_base::`[hexadecimal](../Topic/%3Cios%3E%20functions.md#hex), la especificación de conversión es **lx**.  
  
-   De lo contrario, es la especificación de conversión **ld**.  
  
 Si **iosbase**. [ancho](../standard-library/ios-base-class.md#ios_base__width) es distinto de cero, se antepone un ancho de campo de este valor. A continuación, llama a la función **iosbase**. **ancho**(0) para restablecer el ancho de campo a cero.  
  
 Relleno solo se produce si el número mínimo de elementos *N* necesario para especificar el campo de salida es menor que **iosbase**. [ancho](../standard-library/ios-base-class.md#ios_base__width). Tal relleno consta de una secuencia de *N* – **ancho** copia de **relleno**. Relleno, a continuación, ocurre lo siguiente:  
  
-   Si **iosbase**. **marcas de** & `ios_base::adjustfield` == `ios_base::`[izquierdo](../Topic/%3Cios%3E%20functions.md#left), la marca **–** se antepone. (Relleno se produce después del texto generado).  
  
-   Si **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[interno](../Topic/%3Cios%3E%20functions.md#internal), la marca **0** se antepone. (Para un campo numérico de salida, relleno se produce cuando las funciones de impresión de relleno 0.)  
  
-   De lo contrario, no se antepone ninguna marca adicional. (Relleno se produce antes de la secuencia generada.)  
  
 Por último:  
  
-   Si **iosbase**. **marcas de** & `ios_base::`[showpos](../Topic/%3Cios%3E%20functions.md#showpos) es distinto de cero, el indicador **+** se antepone a la especificación de conversión.  
  
-   Si **iosbase**. **marcas de** & **ios_base::**[showbase](../Topic/%3Cios%3E%20functions.md#showbase) es distinto de cero, el indicador **#** se antepone a la especificación de conversión.  
  
 El formato de un entero de salida campo viene dado por la [faceta de configuración regional](../standard-library/locale-class.md#facet_class)**servicio** devuelto por la llamada [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#ios_base__getloc)). De manera específica:  
  
- **servicio**. [agrupar](../standard-library/numpunct-class.md#numpunct__grouping) determina cómo se agrupan los dígitos a la izquierda del separador decimal  
  
- **servicio**. [thousands_sep](../standard-library/numpunct-class.md#numpunct__thousands_sep) determina la secuencia que separa grupos de dígitos a la izquierda del separador decimal  
  
 Si no hay ninguna restricción de agrupación se imponen por **servicio**. **agrupar** (el primer elemento tiene el valor CHAR_MAX), a continuación, no hay instancias de **servicio**. `thousands_sep` se generan en el campo de salida. De lo contrario, los separadores se insertan después de la conversión de impresión.  
  
 La segunda función miembro protegido virtual:  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    unsigned long val) const;
```  
  
 se comporta igual que la primera, salvo que reemplaza una especificación de conversión de **ld** con **lu**.  
  
 La tercera función miembro protegido virtual:  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    double val) const;
```  
  
 se comporta igual que la primera, salvo que crea un campo de salida de punto flotante del valor de **val**. **servicio**. [decimal_point](../standard-library/numpunct-class.md#numpunct__decimal_point) determina la secuencia que separa los dígitos enteros de los dígitos de fracción. La especificación de conversión de impresión equivalente se determina como sigue:  
  
-   Si **iosbase**. **marcas de** & `ios_base::floatfield` == `ios_base::`[fijo](../Topic/%3Cios%3E%20functions.md#fixed), la especificación de conversión es **lf**.  
  
-   Si **iosbase**. **marcas de** & **ios_base::floatfield** == `ios_base::`[científico](../Topic/%3Cios%3E%20functions.md#scientific), la especificación de conversión es `le`. Si **iosbase**. **marcas de** & `ios_base::`[mayúsculas](../Topic/%3Cios%3E%20functions.md#uppercase) es distinto de cero, **e** se sustituye por **E**.  
  
-   De lo contrario, es la especificación de conversión **lg**. Si **iosbase**. **marcas de** & **ios_base::uppercase** es distinto de cero, **g** se sustituye por **G**.  
  
 Si **iosbase**. **marcas de** & **ios_base::fixed** es distinto de cero o si **iosbase**. [precisión](../standard-library/ios-base-class.md#ios_base__precision) es mayor que cero, una precisión con el valor **iosbase**. **precisión** se antepone a la especificación de conversión. Relleno comporta igual que un campo de salida entero. El carácter de relleno es **relleno**. Por último:  
  
-   Si **iosbase**. **marcas de** & `ios_base::`[showpos](../Topic/%3Cios%3E%20functions.md#showpos) es distinto de cero, el indicador **+** se antepone a la especificación de conversión.  
  
-   Si **iosbase**. **marcas de** & `ios_base::`[showpoint](../Topic/%3Cios%3E%20functions.md#showpoint) es distinto de cero, el indicador **#** se antepone a la especificación de conversión.  
  
 La cuarta función miembro protegido virtual:  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    long double val) const;
```  
  
 se comporta igual que la tercera, salvo que el calificador **l** en la conversión de especificación se reemplaza con **L**.  
  
 La función miembro protegido virtual quinta:  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    const void* val) const;
```  
  
 se comporta igual la primera, salvo que la especificación de conversión es `p`**,** más cualquier calificador necesario para especificar el relleno.  
  
 La función miembro protegido virtual sexta:  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    bool val) const;
```  
  
 se comporta igual que la primera, salvo que genera un campo de resultado booleano de ` val`.  
  
 Un campo booleano de salida adopta una de dos formas. Si **iosbase**. **marcas de** & `ios_base::`[boolalpha](../Topic/%3Cios%3E%20functions.md#boolalpha) es **false**, la función miembro devuelve `do_put`(_ *siguiente*, \_ *Iosbase*, \_ *rellenar*, ( **largo**) ` val`), que normalmente genera una secuencia generada de 0 (para **false**) o 1 (para **true**). De lo contrario, la secuencia generada sea **servicio**. [falsename](../standard-library/numpunct-class.md#numpunct__falsename)`)` (para **false**), o **servicio**. [truename](../standard-library/numpunct-class.md#numpunct__truename) (para **true**).  
  
 La función miembro protegido virtual séptima:  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,  
    Elem fill,
    long long val) const;
```  
  
 se comporta igual que la primera, salvo que reemplaza una especificación de conversión de **ld** con **lld**.  
  
 La función miembro protegido virtual octava:  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,  
    Elem fill,
    unsigned long long val) const;
```  
  
 se comporta igual que la primera, salvo que reemplaza una especificación de conversión de `ld` con `llu`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [colocar](#num_put__put), que llama `do_put`.  
  
##  <a name="a-namenumputitertypea-numputitertype"></a><a name="num_put__iter_type"></a>  num_put:: iter_type  
 Tipo que describe un iterador de salida.  
  
```  
typedef OutputIterator iter_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **OutputIterator.**  
  
##  <a name="a-namenumputnumputa-numputnumput"></a><a name="num_put__num_put"></a>  num_put:: num_put  
 Constructor para los objetos de tipo `num_put`.  
  
```  
explicit num_put(size_t _Refs = 0);
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
  
 El constructor inicializa su objeto base con **locale::**[faceta](../standard-library/locale-class.md#facet_class)(_ *Refs*).  
  
##  <a name="a-namenumputputa-numputput"></a><a name="num_put__put"></a>  num_put:: Put  
 Convierte un número en una secuencia de **CharType**que representa el número con formato para una configuración regional concreta.  
  
```  
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    bool val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    unsigned long val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    Long long val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    Unsigned long long val) const;

 
 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    double val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long double val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const void* val) const;
```  
  
### <a name="parameters"></a>Parámetros  
 ` dest`  
 Un iterador que direcciona el primer elemento de la cadena insertada.  
  
 `_Iosbase`  
 Especifica la secuencia que contiene la configuración regional con la faceta de numpunct usa para enfatice los resultados y las marcas para dar formato a la salida.  
  
 `_Fill`  
 Carácter que se utiliza para el espaciado.  
  
 ` val`  
 El número o tipo booleano que se va de salida.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador de salida generado de la posición más allá del último elemento de las direcciones.  
  
### <a name="remarks"></a>Comentarios  
 Devuelven todas las funciones miembro [do_put](#num_put__do_put)( ` next`, `_Iosbase`, `_Fill`, ` val`).  
  
### <a name="example"></a>Ejemplo  
  
```  
// num_put_put.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
   basic_stringstream<char> psz2;  
   ios_base::iostate st = 0;  
   long double fVal;  
   cout << "The thousands separator is: "   
        << use_facet < numpunct <char> >(loc).thousands_sep( )   
        << endl;  
  
   psz2.imbue( loc );  
   use_facet < num_put < char > >  
      ( loc ).put(basic_ostream<char>::_Iter(psz2.rdbuf( ) ),  
                    psz2, ' ', fVal=1000.67);  
  
   if ( st & ios_base::failbit )  
      cout << "num_put( ) FAILED" << endl;  
   else  
      cout << "num_put( ) = " << psz2.rdbuf( )->str( ) << endl;  
}  
```  
  
```Output  
The thousands separator is: .  
num_put( ) = 1.000,67  
```  
  
## <a name="see-also"></a>Vea también  
 [\< configuración regional>](../standard-library/locale.md)   
 [Facet (clase)](../standard-library/locale-class.md#facet_class)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

