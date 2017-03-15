---
title: "num_get (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "num_get"
  - "std::num_get"
  - "std.num_get"
  - "xlocnum/std::num_get"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "num_get (clase)"
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# num_get (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase de plantilla que describe un objeto que puede actuar como una faceta de la configuración regional para controlar las conversiones de las secuencias de tipo `CharType` en valores numéricos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>  
class num_get : public locale::facet;
```  
  
#### <a name="parameters"></a>Parámetros  
 `CharType`  
 Tipo usado dentro de un programa para codificar los caracteres de una configuración regional.  
  
 `InputIterator`  
 El tipo de iterador del que las funciones get numéricas leen su entrada.  
  
## <a name="remarks"></a>Comentarios  
 Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento para tener acceso a su valor almacenado almacena un valor positivo único en **id.**  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[num_get](#num_get__num_get)|Constructor para los objetos de tipo `num_get` que se usan para extraer valores numéricos de secuencias.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#num_get__char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|  
|[iter_type](#num_get__iter_type)|Tipo que describe un iterador de entrada.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[do_get](#num_get__do_get)|Función virtual a la que se llama para extraer un valor numérico o un valor booleano de una secuencia de caracteres.|  
|[Obtener](#num_get__get)|Extrae un valor numérico o un valor booleano de una secuencia de caracteres.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< configuración regional>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namenumgetchartypea-numgetchartype"></a><a name="num_get__char_type"></a>  num_get:: char_type  
 Tipo que se usa para describir un carácter empleado por una configuración regional.  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **CharType**.  
  
##  <a name="a-namenumgetdogeta-numgetdoget"></a><a name="num_get__do_get"></a>  num_get:: do_get  
 Función virtual a la que se llama para extraer un valor numérico o un valor booleano de una secuencia de caracteres.  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `first`  
 Principio del intervalo de caracteres que se lee el número.  
  
 `last`  
 El final del intervalo de caracteres que se lee el número.  
  
 `_Iosbase`  
 El [ios_base](../standard-library/ios-base-class.md) cuyos indicadores se utilizan por la conversión.  
  
 `_State`  
 El estado de a qué failbit (consulte [ios_base:: iostate](../standard-library/ios-base-class.md#ios_base__iostate)) se agrega un error.  
  
 `val`  
 Valor que se leyó.  
  
### <a name="return-value"></a>Valor devuelto  
 El iterador después de leer el valor.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro protegido virtual,  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `long& val`  
  
 `) const;`  
  
 coincide con los elementos secuenciales empezando por `first` en la secuencia de `[``first``,` `last``)` hasta que se reconoce una completa, el campo de entrada de enteros no vacío. Si tiene éxito, convierte este campo a su valor equivalente como tipo `long``,` y almacena el resultado en `val`. Devuelve un iterador que designa el primer elemento más allá del campo de entrada numérico. De lo contrario, la función almacena nada en `val` y establece `ios_base::failbit` en `state`. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de un campo de entrada de número entero válido. En cualquier caso, si el valor devuelto es igual a `last`, la función establece `ios_base::eofbit` en `state`.  
  
 El campo de entrada de entero se convierte las mismas reglas que utilizan las funciones de análisis para la búsqueda de coincidencias y convertir una serie de `char` elementos de un archivo. (Cada como `char` se supone que el elemento se asignan a un elemento de tipo equivalente `Elem` mediante un simple, uno a uno, asignación.) La especificación de conversión de examen equivalente se determina como sigue:  
  
 Si `iosbase.`[ios_base:: flags](../standard-library/ios-base-class.md#ios_base__flags)`() & ios_base::basefield == ios_base::`[oct](../Topic/%3Cios%3E%20functions.md#oct), la especificación de conversión es `lo`.  
  
 Si `iosbase.flags() & ios_base::basefield == ios_base::`[hexadecimal](../Topic/%3Cios%3E%20functions.md#hex), la especificación de conversión es `lx`.  
  
 Si `iosbase.flags() & ios_base::basefield == 0`, la especificación de conversión es `li`.  
  
 De lo contrario, la especificación de conversión es `ld`.  
  
 El formato de un campo de entrada de entero se determina por la [faceta de configuración regional](../standard-library/locale-class.md#facet_class)`fac` devuelto por la llamada [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) `<`[numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.` [ios_base:: getloc](../standard-library/ios-base-class.md#ios_base__getloc)`())`. De manera específica:  
  
 `fac.` [numpunct:: Grouping](../standard-library/numpunct-class.md#numpunct__grouping) `()` Determina cómo se agrupan los dígitos a la izquierda del separador decimal  
  
 `fac.` [numpunct:: thousands_sep](../standard-library/numpunct-class.md#numpunct__thousands_sep) `()` Determina la secuencia que separa grupos de dígitos a la izquierda del separador decimal.  
  
 Si no hay instancias de `fac.thousands_sep()` se producen en el campo de entrada numérico, no se impone ninguna restricción de agrupación. De lo contrario, cualquier agrupación de restricciones impuestas por `fac.grouping()` se aplican y los separadores se quitan antes de que se produce la conversión de examen.  
  
 La cuarta función miembro protegido virtual:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `unsigned long& val`  
  
 `) const;`  
  
 se comporta igual que la primera, salvo que reemplaza una especificación de conversión de `ld` con `lu`. Si correcta convierte el campo de entrada numérico en un valor de tipo `unsigned long` y almacena ese valor en `val`.  
  
 La función miembro protegido virtual quinta:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `long long& val`  
  
 `) const;`  
  
 se comporta igual que la primera, salvo que reemplaza una especificación de conversión de `ld` con `lld`. Si correcta convierte el campo de entrada numérico en un valor de tipo `long long` y almacena ese valor en `val`.  
  
 La función miembro protegido virtual sexta:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `unsigned long long& val`  
  
 `) const;`  
  
 se comporta igual que la primera, salvo que reemplaza una especificación de conversión de `ld` con `llu`. Si correcta convierte el campo de entrada numérico en un valor de tipo `unsigned long long` y almacena ese valor en `val`.  
  
 La función miembro protegido virtual séptima:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `float& val`  
  
 `) const;`  
  
 se comporta igual que la primera, excepto en que intenta coincidir con un campo de entrada punto flotante completando, no está vacío. `fac.`[numpunct:: decimal_point](../standard-library/numpunct-class.md#numpunct__decimal_point)`()` determina la secuencia que separa los dígitos enteros de los dígitos de fracción. El especificador de conversión de examen equivalente es `lf`.  
  
 La función miembro protegido virtual octava:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `double& val`  
  
 `) const;`  
  
 se comporta igual que la primera, excepto en que intenta coincidir con un campo de entrada punto flotante completando, no está vacío. `fac.`[numpunct:: decimal_point](../standard-library/numpunct-class.md#numpunct__decimal_point)`()` determina la secuencia que separa los dígitos enteros de los dígitos de fracción. El especificador de conversión de examen equivalente es `lf`.  
  
 La función miembro protegido virtual novena:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `long double& val`  
  
 `) const;`  
  
 se comporta como la octava, salvo que el especificador de conversión de examen equivalente es `Lf`.  
  
 La función miembro protegido virtual novena:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `void *& val`  
  
 `) const;`  
  
 se comporta igual la primera, salvo que el especificador de conversión de examen equivalente es `p`.  
  
 La última función miembro protegido (undécima) virtual:  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `bool& val`  
  
 `) const;`  
  
 se comporta igual que la primera, excepto en que intenta coincidir con un campo de entrada booleano completando, no está vacío. Si correcta convierte el campo de entrada booleano a un valor de tipo `bool` y almacena ese valor en `val`.  
  
 Un campo de entrada booleano adopta una de dos formas. Si `iosbase.flags() & ios_base::`[boolalpha](../Topic/%3Cios%3E%20functions.md#boolalpha) es false, es el mismo que un campo de entrada de enteros, excepto que el valor convertido debe ser 0 (falso) o 1 (para true). De lo contrario, la secuencia debe coincidan con `fac.`[numpunct:: falsename](../standard-library/numpunct-class.md#numpunct__falsename)`()` (para false), o `fac.`[numpunct:: truename](../standard-library/numpunct-class.md#numpunct__truename)`()` (para true).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [obtener](#num_get__get), donde se llama a la función miembro virtual `do_get`.  
  
##  <a name="a-namenumgetgeta-numgetget"></a><a name="num_get__get"></a>  num_get:: Get  
 Extrae un valor numérico o un valor booleano de una secuencia de caracteres.  
  
```
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `first`  
 Principio del intervalo de caracteres que se lee el número.  
  
 `last`  
 El final del intervalo de caracteres que se lee el número.  
  
 `_Iosbase`  
 El [ios_base](../standard-library/ios-base-class.md) cuyos indicadores se utilizan por la conversión.  
  
 `_State`  
 El estado de a qué failbit (consulte [ios_base:: iostate](../standard-library/ios-base-class.md#ios_base__iostate)) se agrega un error.  
  
 `val`  
 Valor que se leyó.  
  
### <a name="return-value"></a>Valor devuelto  
 El iterador después de leer el valor.  
  
### <a name="remarks"></a>Comentarios  
 Devuelven todas las funciones miembro [do_get](#num_get__do_get)( `first`, `last`, `_Iosbase`, `_State`, `val`).  
  
 La primera función miembro protegido virtual intenta hacer coincidir elementos secuenciales, empezando al principio de la secuencia [ `first`, `last`) hasta que se reconoce una completa, el campo de entrada de enteros no vacío. Si tiene éxito, convierte este campo a su valor equivalente como tipo **largo** y almacena el resultado en `val`. Devuelve un iterador que designa el primer elemento más allá del campo de entrada numérico. De lo contrario, la función almacena nada en `val` y establece `ios_base::failbit` en _ *estado*. Devuelve un iterador que designa el primer elemento más allá de cualquier prefijo de un campo de entrada de número entero válido. En cualquier caso, si el valor devuelto es igual a **última**, la función establece `ios_base::eofbit` en `_State`.  
  
 El campo de entrada de entero se convierte las mismas reglas que utilizan las funciones de análisis para la búsqueda de coincidencias y convertir una serie de `char` elementos de un archivo. Cada como `char` se supone que el elemento se asignan a un elemento de tipo equivalente **CharType** mediante una asignación simple, uno a uno. La especificación de conversión de examen equivalente se determina como sigue:  
  
-   Si **iosbase**. [marcas de](../standard-library/ios-base-class.md#ios_base__flags) & `ios_base::basefield` == `ios_base::`[oct](../Topic/%3Cios%3E%20functions.md#oct), la especificación de conversión es **lo**.  
  
-   Si **iosbase.flags** & **ios_base:: basefield** == `ios_base::`[hexadecimal](../Topic/%3Cios%3E%20functions.md#hex), la especificación de conversión es **lx**.  
  
-   Si **iosbase.flags** & **ios_base:: basefield** == 0, la especificación de conversión es `li`.  
  
-   De lo contrario, es la especificación de conversión **ld**.  
  
 El formato de un campo de entrada de entero se determina por la [faceta de configuración regional](../standard-library/locale-class.md#facet_class)**servicio** devuelto por la llamada [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#ios_base__getloc)). De manera específica:  
  
- **servicio**. [agrupar](../standard-library/numpunct-class.md#numpunct__grouping) determina cómo se agrupan los dígitos a la izquierda del separador decimal.  
  
- **servicio**. [thousands_sep](../standard-library/numpunct-class.md#numpunct__thousands_sep) determina la secuencia que separa grupos de dígitos a la izquierda del separador decimal.  
  
 Si no hay instancias de **servicio**. `thousands_sep` se producen en el campo de entrada numérico, no se impone ninguna restricción de agrupación. De lo contrario, cualquier agrupación de restricciones impuestas por **servicio**. **agrupación de** se aplica y los separadores se quitan antes de que se produce la conversión de examen.  
  
 La segunda función miembro protegido virtual:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```  
  
 se comporta igual que la primera, salvo que reemplaza una especificación de conversión de **ld** con **lu**. Si tiene éxito, convierte el campo de entrada numérico en un valor de tipo `unsigned long` y almacena ese valor en `val`.  
  
 La tercera función miembro protegido virtual:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```  
  
 se comporta igual que la primera, salvo que intenta hacer coincidir un campo de entrada punto flotante completando, no está vacío. **servicio**. [decimal_point](../standard-library/numpunct-class.md#numpunct__decimal_point) determina la secuencia que separa los dígitos enteros de los dígitos de fracción. El especificador de conversión de examen equivalente es **lf**.  
  
 La cuarta función miembro protegido virtual:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```  
  
 se comporta igual la tercera, salvo que el especificador de conversión de examen equivalente es **Lf**.  
  
 La función miembro protegido virtual quinta:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
 se comporta igual la primera, salvo que el especificador de conversión de examen equivalente es **p**.  
  
 La función miembro protegido virtual sexta:  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
 se comporta igual que la primera, salvo que intenta hacer coincidir un campo de entrada booleano completando, no está vacío. Si correcta convierte el campo de entrada booleano a un valor de tipo `bool` y almacena ese valor en `val`.  
  
 Un campo de entrada booleano adopta una de dos formas. Si **iosbase**. **marcas de** & `ios_base::`[boolalpha](../Topic/%3Cios%3E%20functions.md#boolalpha) es **false**, es el mismo que un campo de entrada de enteros, excepto en que el valor convertido debe ser 0 (para **false**) o 1 (para **true**). De lo contrario, la secuencia debe coincidan con **servicio**. [falsename](../standard-library/numpunct-class.md#numpunct__falsename) (para **false**), o **servicio**. [truename](../standard-library/numpunct-class.md#numpunct__truename) (para **true**).  
  
### <a name="example"></a>Ejemplo  
  
```  
// num_get_get.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
  
   basic_stringstream<char> psz, psz2;  
   psz << "-1000,56";  
  
   ios_base::iostate st = 0;  
   long double fVal;  
   cout << use_facet <numpunct <char> >(loc).thousands_sep( ) << endl;  
  
   psz.imbue( loc );  
   use_facet <num_get <char> >  
   (loc).get( basic_istream<char>::_Iter( psz.rdbuf( ) ),  
           basic_istream<char>::_Iter(0), psz, st, fVal );  
  
   if ( st & ios_base::failbit )  
      cout << "money_get( ) FAILED" << endl;  
   else  
      cout << "money_get( ) = " << fVal << endl;  
}  
```  
  
##  <a name="a-namenumgetitertypea-numgetitertype"></a><a name="num_get__iter_type"></a>  num_get:: iter_type  
 Tipo que describe un iterador de entrada.  
  
```
typedef InputIterator iter_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **InputIterator**.  
  
##  <a name="a-namenumgetnumgeta-numgetnumget"></a><a name="num_get__num_get"></a>  num_get:: num_get  
 Constructor para los objetos de tipo `num_get` que se usan para extraer valores numéricos de secuencias.  
  
```
explicit num_get(size_t _Refs = 0);
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
  
## <a name="see-also"></a>Vea también  
 [\< configuración regional>](../standard-library/locale.md)   
 [Facet (clase)](../standard-library/locale-class.md#facet_class)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



