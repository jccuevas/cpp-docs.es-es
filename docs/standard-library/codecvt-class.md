---
title: "codecvt (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "codecvt"
  - "std::codecvt"
  - "std.codecvt"
  - "xlocale/std::codecvt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt (clase)"
ms.assetid: 37d3efa1-2b7f-42b6-b04f-7a972c8c2c86
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de plantilla que describe un objeto que puede actuar como faceta de configuración regional. Puede controlar las conversiones entre una secuencia de valores usados para codificar caracteres dentro del programa y una secuencia de valores usados para codificar caracteres fuera del programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class CharType, class Byte, class StateType>  
class codecvt : public locale::facet, codecvt_base;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `CharType`  
 Tipo usado dentro de un programa para codificar caracteres.  
  
 `Byte`  
 Tipo usado para codificar caracteres fuera de un programa.  
  
 `StateType`  
 Tipo que se puede usar para representar los estados intermedios de una conversión entre los tipos internos y externos de representaciones de caracteres.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla describe un objeto que puede actuar como un [faceta de configuración regional](../standard-library/locale-class.md#facet_class), para controlar las conversiones entre una secuencia de valores de tipo `CharType` y una secuencia de valores de tipo `Byte`. La clase `StateType` caracteriza la transformación y un objeto de clase `StateType` almacena la información de estado necesaria durante una conversión.  
  
 La codificación interna emplea una representación con un número fijo de bytes por carácter, normalmente de tipo `char` o de tipo `wchar_t`.  
  
 Como ocurre con cualquier faceta de configuración regional, el `id` de objeto estático tiene un valor almacenado inicial de cero. El primer intento para tener acceso a su valor almacenado almacena un valor positivo único en `id`.  
  
 Las versiones de la plantilla de [do_in](#codecvt__do_in) y [do_out](#codecvt__do_out) siempre devuelven `codecvt_base::noconv`.  
  
 La Biblioteca estándar de C++ define varias especializaciones explícitas:  
  
 `template<>`  
  
 `codecvt<wchar_t, char, mbstate_t>`  
  
 convierte entre secuencias `wchar_t` y `char`.  
  
 `template<>`  
  
 `codecvt<char16_t, char, mbstate_t>`  
  
 convierte entre secuencias `char16_t` codificadas como UTF-16 y secuencias `char` codificadas como UTF-8.  
  
 `template<>`  
  
 `codecvt<char32_t, char, mbstate_t>`  
  
 convierte entre secuencias `char32_t` codificadas como UTF-32 (UCS-4) y secuencias `char` codificadas como UTF-8.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[codecvt](#codecvt__codecvt)|Constructor de objetos de clase `codecvt` que actúa como faceta de configuración regional para controlar las conversiones.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[extern_type](#codecvt__extern_type)|Tipo de carácter que se usa para las representaciones externas.|  
|[intern_type](#codecvt__intern_type)|Tipo de carácter que se usa para las representaciones internas.|  
|[state_type](#codecvt__state_type)|Tipo de carácter que se usa para representar los estados intermedios durante las conversiones entre las representaciones internas y externas.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[always_noconv](#codecvt__always_noconv)|Comprueba si no es necesario realizar ninguna conversión.|  
|[do_always_noconv](#codecvt__do_always_noconv)|Función virtual a la que se llama para comprobar si no es necesario realizar ninguna conversión.|  
|[do_encoding](#codecvt__do_encoding)|Función virtual que comprueba si la codificación del flujo `Byte` depende del estado, si la relación entre los `Byte`s usados y los `CharType`s generados es constante y, en tal caso, determina el valor de esa relación.|  
|[do_in](#codecvt__do_in)|Función virtual a la que se llama para convertir una secuencia de `Byte`s internos en una secuencia de `CharType`s externos.|  
|[do_length](#codecvt__do_length)|Función virtual que determina cuántos `Byte`s de una secuencia determinada de `Byte`s externos generan no más de un número determinado de `CharType`s internos y devuelve ese número de `Byte`s.|  
|[do_max_length](#codecvt__do_max_length)|Función virtual que devuelve el número máximo de bytes externos necesarios para generar un `CharType` interno.|  
|[do_out](#codecvt__do_out)|Función virtual a la que se llama para convertir una secuencia de `CharType`s internos en una secuencia de Bytes externos.|  
|[do_unshift](#codecvt__do_unshift)|Función virtual a la que se llama para proporcionar los `Byte`s necesarios en una conversión dependiente del estado para completar el último carácter de una secuencia de `Byte`s.|  
|[codificación](#codecvt__encoding)|Comprueba si la codificación del flujo `Byte` depende del estado, si la relación entre los `Byte`s usados y los `CharType`s generados es constante y, en tal caso, determina el valor de esa relación.|  
|[en](#codecvt__in)|Convierte una representación externa de una secuencia de `Byte`s en una representación interna de una secuencia de `CharType`s.|  
|[longitud](#codecvt__length)|Determina cuántos `Byte`s de una secuencia dada de `Byte`s externos generan no más de un número determinado de `CharType`s internos y devuelve ese número de `Byte`s.|  
|[max_length](#codecvt__max_length)|Devuelve el número máximo de `Byte`s externos necesarios para generar un `CharType` interno.|  
|[horizontal](#codecvt__out)|Convierte una secuencia de `CharType`s internos en una secuencia de `Byte`s externos.|  
|[unshift](#codecvt__unshift)|Proporciona los `Byte`s externos necesarios en una conversión dependiente del estado para completar el último carácter de la secuencia de `Byte`s.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< configuración regional>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namecodecvtalwaysnoconva-codecvtalwaysnoconv"></a><a name="codecvt__always_noconv"></a>  codecvt:: always_noconv  
 Comprueba si no es necesario realizar ninguna conversión.  
  
```  
bool always_noconv() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor booleano que es **true** Si es no necesario realizar ninguna conversión; **false** es al menos uno debe hacerse.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [do_always_noconv](#codecvt__do_always_noconv).  
  
### <a name="example"></a>Ejemplo  
  
```  
// codecvt_always_noconv.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = use_facet<codecvt<char, char, mbstate_t> >   
      ( loc ).always_noconv( );  
  
   if ( result1 )  
      cout << "No conversion is needed." << endl;  
   else  
      cout << "At least one conversion is required." << endl;  
  
   bool result2 = use_facet<codecvt<wchar_t, char, mbstate_t> >   
      ( loc ).always_noconv( );  
  
   if ( result2 )  
      cout << "No conversion is needed." << endl;  
   else  
      cout << "At least one conversion is required." << endl;  
}  
```  
  
```Output  
No conversion is needed.  
At least one conversion is required.  
```  
  
##  <a name="a-namecodecvtcodecvta-codecvtcodecvt"></a><a name="codecvt__codecvt"></a>  codecvt:: codecvt  
 El constructor de objetos de codecvt de clase que actúa como una faceta de configuración regional para controlar las conversiones.  
  
```  
explicit codecvt(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Refs`  
 Valor entero que se utiliza para especificar el tipo de administración de memoria para el objeto.  
  
### <a name="remarks"></a>Comentarios  
 Los valores posibles de la `_Refs` parámetro y su importancia son:  
  
-   0: la duración del objeto administra las configuraciones regionales que lo contienen.  
  
-   1: se debe administrar manualmente la duración del objeto.  
  
-   \> 0: no se definen estos valores.  
  
 El constructor inicializa su `locale::facet` objeto base con **locale::**[faceta](../standard-library/locale-class.md#facet_class)( `_Refs`) *.*  
  
##  <a name="a-namecodecvtdoalwaysnoconva-codecvtdoalwaysnoconv"></a><a name="codecvt__do_always_noconv"></a>  codecvt:: do_always_noconv  
 Función virtual a la que se llama para comprobar si no es necesario realizar ninguna conversión.  
  
```  
virtual bool do_always_noconv() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro virtual protegida devuelve **true** sólo si todas las llamadas a [do_in](#codecvt__do_in) o [do_out](#codecvt__do_out) devuelve **noconv**.  
  
 Siempre devuelve la versión de plantilla **true**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [always_noconv](#codecvt__always_noconv), que llama `do_always_noconv`.  
  
##  <a name="a-namecodecvtdoencodinga-codecvtdoencoding"></a><a name="codecvt__do_encoding"></a>  codecvt:: do_encoding  
 Una función virtual que comprueba si la codificación de la **bytes** secuencia es depende del estado, si la relación entre el **bytes**s usados y el **CharType**s generados es constante y, si es así, determina el valor de esa relación.  
  
```  
virtual int do_encoding() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro virtual protegida devuelve:  
  
-   -1, si la codificación de secuencias de tipo `extern_type` depende del estado.  
  
-   0, si trata de la codificación de secuencias de longitud variable.  
  
- *N*, si la codificación implica sólo secuencias de longitud *N*  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [codificación](#codecvt__encoding), que llama `do_encoding`.  
  
##  <a name="a-namecodecvtdoina-codecvtdoin"></a><a name="codecvt__do_in"></a>  codecvt:: do_in  
 Llama a una función virtual para convertir una secuencia de externo **bytes**s en una secuencia de interno **CharType**s.  
  
```  
virtual result do_in(
    StateType& _State,  
    const Byte* first1,   
    const Byte* last1,   
    const Byte*& next1,  
    CharType* first2,  
    CharType* last2,  
    CharType*& next2,) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_State`  
 El estado de conversión que se mantiene entre las llamadas a la función miembro.  
  
 ` first1`  
 Puntero al principio de la secuencia que se va a convertir.  
  
 ` last1`  
 Puntero al final de la secuencia que se va a convertir.  
  
 ` next1`  
 Puntero más allá del final de la secuencia de convertir el primer carácter no se convertirá.  
  
 ` first2`  
 Puntero al principio de la secuencia convertida.  
  
 ` last2`  
 Puntero al final de la secuencia convertida.  
  
 ` next2`  
 Puntero a la **CharType** que viene después de convertir la última **CharType**, hasta el primer carácter sin modificaciones en la secuencia de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor devuelto que indica el éxito, parcialmente correcta o error de la operación. Devuelve la función:  
  
- **codecvt_base::error** Si la secuencia de origen está ill formado.  
  
- `codecvt_base::noconv` Si la función realiza ninguna conversión.  
  
- **codecvt_base::OK** Si la conversión se realiza correctamente.  
  
- **codecvt_base::Partial** Si el origen no es suficiente o si el destino no es suficiente, la conversión se realice correctamente.  
  
### <a name="remarks"></a>Comentarios  
 `_State` debe representar el estado de la conversión inicial al principio de una nueva secuencia de origen. La función modifica su valor almacenado según sea necesario para reflejar el estado actual de una conversión correcta. De lo contrario, se especifica su valor almacenado.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [en](#codecvt__in), que llama `do_in`.  
  
##  <a name="a-namecodecvtdolengtha-codecvtdolength"></a><a name="codecvt__do_length"></a>  codecvt:: do_length  
 Una función virtual que determina cuántos **bytes**s de una secuencia determinada de externo **bytes**s generan no más de un número determinado de interno **CharType**s y devuelve ese número de **bytes**s.  
  
```  
virtual int do_length(
    const StateType& _State,  
    const Byte* first1,   
    const Byte* last1,  
    size_t _Len2) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_State`  
 El estado de conversión que se mantiene entre las llamadas a la función miembro.  
  
 ` first1`  
 Puntero al principio de la secuencia externo.  
  
 ` last1`  
 Puntero al final de la secuencia externo.  
  
 `_Len2`  
 El número máximo de **bytes**s que se pueden devolver a la función miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero que representa el número máximo de conversiones, no es mayores que `_Len2`, definido en la secuencia de origen externo [ ` first1`, ` last1`).  
  
### <a name="remarks"></a>Comentarios  
 Realmente, llama a la función miembro virtual protegida `do_in`( `_State`, ` first1`, ` last1`, ` next1`, `_Buf`, `_Buf` + `_Len2`, ` next2`) para `_State` (una copia del estado), un búfer `_Buf`, y punteros ` next1`y ` next2`.  
  
 A continuación, devuelve ` next2` – **buf**. Por lo tanto, cuente el número máximo de conversiones, no es mayores que `_Len2`, definido en la secuencia de origen [ ` first1`, ` last1`).  
  
 La versión de plantilla siempre devuelve el menor de ` last1` : ` first1` y `_Len2`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [longitud](#codecvt__length), que llama **do_length**.  
  
##  <a name="a-namecodecvtdomaxlengtha-codecvtdomaxlength"></a><a name="codecvt__do_max_length"></a>  codecvt:: do_max_length  
 Una función virtual que devuelve el número máximo de externo **bytes**s necesarios para generar un interno **CharType**.  
  
```  
virtual int do_max_length() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número máximo de **bytes**s necesarios para generar un **CharType**.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro virtual protegida devuelve el mayor valor posibles que puede ser devueltos por [do_length](#codecvt__do_length)( ` first1`, ` last1`, 1) para los valores válidos arbitrarios de ` first1` y ` last1`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [max_length](#codecvt__max_length), que llama `do_max_length`.  
  
##  <a name="a-namecodecvtdoouta-codecvtdoout"></a><a name="codecvt__do_out"></a>  codecvt:: do_out  
 Llama a una función virtual para convertir una secuencia interna **CharType**s a una secuencia de externo **bytes**s.  
  
```  
virtual result do_out(
    StateType& _State,  
    const CharType* first1,   
    const CharType* last1,  
    const CharType*& next1,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_State`  
 El estado de conversión que se mantiene entre las llamadas a la función miembro.  
  
 ` first1`  
 Puntero al principio de la secuencia que se va a convertir.  
  
 ` last1`  
 Puntero al final de la secuencia que se va a convertir.  
  
 ` next1`  
 Referencia a un puntero al primer sin convertir **CharType**, después de la última **CharType** convertir.  
  
 ` first2`  
 Puntero al principio de la secuencia convertida.  
  
 ` last2`  
 Puntero al final de la secuencia convertida.  
  
 ` next2`  
 Referencia a un puntero al primer sin convertir **bytes**, después de la última **bytes** convertir.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función:  
  
- **codecvt_base::error** Si la secuencia de origen está ill formado.  
  
- `codecvt_base::noconv` Si la función realiza ninguna conversión.  
  
- **codecvt_base::OK** Si la conversión se realiza correctamente.  
  
- **codecvt_base::Partial** Si el origen no es suficiente o si el destino no es lo suficientemente grande como para la conversión se realice correctamente.  
  
### <a name="remarks"></a>Comentarios  
 `_State` debe representar el estado de la conversión inicial al principio de una nueva secuencia de origen. La función modifica su valor almacenado según sea necesario para reflejar el estado actual de una conversión correcta. De lo contrario, se especifica su valor almacenado.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [a](#codecvt__out), que llama `do_out`.  
  
##  <a name="a-namecodecvtdounshifta-codecvtdounshift"></a><a name="codecvt__do_unshift"></a>  codecvt:: do_unshift  
 Llama a una función virtual para proporcionar la **bytes**s necesarios en una conversión dependiente del estado para completar el último carácter de una secuencia de **bytes**s.  
  
```  
virtual result do_unshift(
    StateType& _State,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_State`  
 El estado de conversión que se mantiene entre las llamadas a la función miembro.  
  
 ` first2`  
 Puntero a la primera posición del intervalo de destino.  
  
 ` last2`  
 Puntero a la última posición del intervalo de destino.  
  
 ` next2`  
 Puntero al primer elemento sin modificaciones en la secuencia de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función:  
  
- **codecvt_base::error** Si _ *estado* representa un estado no válido  
  
- `codecvt_base::noconv` Si la función realiza ninguna conversión  
  
- **codecvt_base::OK** Si la conversión se realiza correctamente  
  
- **codecvt_base::Partial** Si el destino no es lo suficientemente grande como para la conversión se realice correctamente  
  
### <a name="remarks"></a>Comentarios  
 La función miembro virtual protegida intenta convertir el elemento de origen **CharType**(0) en una secuencia de destino que almacena en [ ` first2`, ` last2`), excepto el elemento terminación **bytes**(0). Siempre se almacena en ` next2` un puntero al primer elemento sin modificaciones en la secuencia de destino.  
  
 _ *Estado* debe representar el estado de conversión inicial al principio de una nueva secuencia de origen. La función modifica su valor almacenado según sea necesario para reflejar el estado actual de una conversión correcta. Normalmente, convertir el elemento de origen **CharType**(0) deja el estado actual en el estado de la conversión inicial.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [unshift](#codecvt__unshift), que llama `do_unshift`.  
  
##  <a name="a-namecodecvtencodinga-codecvtencoding"></a><a name="codecvt__encoding"></a>  codecvt:: Encoding  
 Comprueba si la codificación de la **bytes** secuencia es depende del estado, si la relación entre el **bytes**s usados y el **CharType**s generados es constante y, si es así, determina el valor de esa relación.  
  
```  
int encoding() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el valor devuelto es positivo, ese valor es el número constante de **bytes** caracteres necesarios para producir el **CharType** caracteres.  
  
 La función miembro virtual protegida devuelve:  
  
-   -1, si la codificación de secuencias de tipo `extern_type` depende del estado.  
  
-   0, si trata de la codificación de secuencias de longitud variable.  
  
- *N*, si la codificación implica sólo secuencias de longitud *N.*  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [do_encoding](#codecvt__do_encoding).  
  
### <a name="example"></a>Ejemplo  
  
```  
// codecvt_encoding.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   int result1 = use_facet<codecvt<char, char, mbstate_t> > ( loc ).encoding ( );  
   cout << result1 << endl;  
   result1 = use_facet<codecvt<wchar_t, char, mbstate_t> > ( loc ).encoding( );  
   cout << result1 << endl;  
   result1 = use_facet<codecvt<char, wchar_t, mbstate_t> > ( loc ).encoding( );  
   cout << result1 << endl;  
}  
```  
  
```Output  
1  
1  
1  
```  
  
##  <a name="a-namecodecvtexterntypea-codecvtexterntype"></a><a name="codecvt__extern_type"></a>  codecvt:: extern_type  
 Tipo de carácter que se usa para las representaciones externas.  
  
```  
typedef Byte extern_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **bytes**.  
  
##  <a name="a-namecodecvtina-codecvtin"></a><a name="codecvt__in"></a>  codecvt:: in  
 Convierte una representación externa de una secuencia de **bytes**s en una representación interna de una secuencia de **CharType**s.  
  
```  
result in(
    StateType& _State,  
    const Byte* first1,   
    const Byte* last1,   
    const Byte*& next1,  
    CharType* first2,  
    CharType* last2,  
    CharType*& next2,) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_State`  
 El estado de conversión que se mantiene entre las llamadas a la función miembro.  
  
 ` first1`  
 Puntero al principio de la secuencia que se va a convertir.  
  
 ` last1`  
 Puntero al final de la secuencia que se va a convertir.  
  
 ` next1`  
 Puntero más allá del final de la secuencia convertido en el primer carácter no se convertirá.  
  
 ` first2`  
 Puntero al principio de la secuencia convertida.  
  
 ` last2`  
 Puntero al final de la secuencia convertida.  
  
 ` next2`  
 Puntero a la **CharType** que viene después de convertir la última **Chartype** hasta el primer carácter sin modificaciones en la secuencia de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor devuelto que indica el éxito, parcialmente correcta o error de la operación. Devuelve la función:  
  
- **codecvt_base::error** Si la secuencia de origen está ill formado.  
  
- `codecvt_base::noconv` Si la función realiza ninguna conversión.  
  
- **codecvt_base::OK** Si la conversión se realiza correctamente.  
  
- **codecvt_base::Partial** Si el origen no es suficiente o si el destino no es lo suficientemente grande como para la conversión se realice correctamente.  
  
### <a name="remarks"></a>Comentarios  
 `_State` debe representar el estado de la conversión inicial al principio de una nueva secuencia de origen. La función modifica su valor almacenado, según sea necesario, para reflejar el estado actual de una conversión correcta. Después de una conversión parcial, `_State` debe establecerse para permitir la conversión a reanudar cuando llegan nuevos caracteres.  
  
 La función miembro devuelve [do_in](#codecvt__do_in)( `_State`, _ *First1 Nombre Apellido1, next1, First2, _Llast2, next2*).  
  
### <a name="example"></a>Ejemplo  
  
```  
// codecvt_in.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
using namespace std;  
#define LEN 90  
int main( )     
{  
   char* pszExt = "This is the string to be converted!";  
   wchar_t pwszInt [LEN+1];  
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));  
   const char* pszNext;  
   wchar_t* pwszNext;  
   mbstate_t state = {0};  
   locale loc("C");//English_Britain");//German_Germany  
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >  
     ( loc ).in( state,  
          pszExt, &pszExt[strlen(pszExt)], pszNext,  
          pwszInt, &pwszInt[strlen(pszExt)], pwszNext );  
   pwszInt[strlen(pszExt)] = 0;  
   wcout << ( (res!=codecvt_base::error)  L"It worked! " : L"It didn't work! " )  
   << L"The converted string is:\n ["  
   << &pwszInt[0]  
   << L"]" << endl;  
   exit(-1);  
}  
```  
  
```Output  
It worked! The converted string is:  
 [This is the string to be converted!]  
```  
  
##  <a name="a-namecodecvtinterntypea-codecvtinterntype"></a><a name="codecvt__intern_type"></a>  codecvt:: intern_type  
 Tipo de carácter que se usa para las representaciones internas.  
  
```  
typedef CharType intern_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **CharType**.  
  
##  <a name="a-namecodecvtlengtha-codecvtlength"></a><a name="codecvt__length"></a>  codecvt:: Length  
 Determina cuántos **bytes**s de una secuencia determinada de externo **bytes**s generan no más de un número determinado de interno **CharType**s y devuelve ese número de **bytes**s.  
  
```  
int length(
    const StateType& _State,  
    const Byte* first1,   
    const Byte* last1,  
    size_t _Len2) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_State`  
 El estado de conversión que se mantiene entre las llamadas a la función miembro.  
  
 ` first1`  
 Puntero al principio de la secuencia externo.  
  
 ` last1`  
 Puntero al final de la secuencia externo.  
  
 `_Len2`  
 El número máximo de Bytes que se pueden devolver a la función miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero que representa el número máximo de conversiones, no es mayores que `_Len2`, definido en la secuencia de origen externo [ ` first1`, ` last1`).  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [do_length](#codecvt__do_length)( *_State, first1*, ` last1`, `_Len2`).  
  
### <a name="example"></a>Ejemplo  
  
```  
// codecvt_length.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
using namespace std;  
#define LEN 90  
int main( )     
{  
   char* pszExt = "This is the string whose length is to be measured!";  
   mbstate_t state = {0};  
   locale loc("C");//English_Britain");//German_Germany  
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >  
     ( loc ).length( state,  
          pszExt, &pszExt[strlen(pszExt)], LEN );  
   cout << "The length of the string is: ";  
   wcout << res;  
   cout << "." << endl;  
   exit(-1);  
}  
```  
  
```Output  
The length of the string is: 50.  
```  
  
##  <a name="a-namecodecvtmaxlengtha-codecvtmaxlength"></a><a name="codecvt__max_length"></a>  codecvt:: max_length  
 Devuelve el número máximo de externo **bytes**s necesarios para generar un interno **CharType**.  
  
```  
int max_length() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número máximo de **bytes**s necesarios para generar un **CharType**.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [do_max_length](#codecvt__do_max_length).  
  
### <a name="example"></a>Ejemplo  
  
```  
// codecvt_max_length.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc( "C");//English_Britain" );//German_Germany  
   int res = use_facet<codecvt<char, char, mbstate_t> >  
     ( loc ).max_length( );  
   wcout << res << endl;  
}  
```  
  
```Output  
1  
```  
  
##  <a name="a-namecodecvtouta-codecvtout"></a><a name="codecvt__out"></a>  codecvt:: out  
 Convierte una secuencia de interno **CharType**s a una secuencia de externo **bytes**s.  
  
```  
result out(
    StateType& _State,  
    const CharType* first1,   
    const CharType* last1,  
    const CharType*& next1,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_State`  
 El estado de conversión que se mantiene entre las llamadas a la función miembro.  
  
 ` first1`  
 Puntero al principio de la secuencia que se va a convertir.  
  
 ` last1`  
 Puntero al final de la secuencia que se va a convertir.  
  
 ` next1`  
 Referencia a un puntero al primer sin convertir **CharType** después de la última **CharType** convertir.  
  
 ` first2`  
 Puntero al principio de la secuencia convertida.  
  
 ` last2`  
 Puntero al final de la secuencia convertida.  
  
 ` next2`  
 Referencia a un puntero al primer sin convertir **bytes** después de convertir la última **bytes**.  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro devuelve [do_out](#codecvt__do_out)( `_State`, ` first1`, ` last1`, ` next1`, ` first2`, ` last2`, ` next2`).  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [codecvt:: do_out](#codecvt__do_out).  
  
### <a name="example"></a>Ejemplo  
  
```  
// codecvt_out.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
#include <wchar.h>  
using namespace std;  
#define LEN 90  
int main( )     
{  
   char pszExt[LEN+1];  
   wchar_t *pwszInt = L"This is the wchar_t string to be converted.";  
   memset( &pszExt[0], 0, ( sizeof( char ) )*( LEN+1 ) );  
   char* pszNext;  
   const wchar_t* pwszNext;  
   mbstate_t state;  
   locale loc("C");//English_Britain");//German_Germany  
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >  
      ( loc ).out( state,  
      pwszInt, &pwszInt[wcslen( pwszInt )], pwszNext ,  
      pszExt, &pszExt[wcslen( pwszInt )], pszNext );  
   pszExt[wcslen( pwszInt )] = 0;  
   cout << ( ( res!=codecvt_base::error )  "It worked: " : "It didn't work: " )  
   << "The converted string is:\n ["  
   << &pszExt[0]  
   << "]" << endl;  
}  
```  
  
```Output  
It worked: The converted string is:  
 [This is the wchar_t string to be converted.]  
```  
  
##  <a name="a-namecodecvtstatetypea-codecvtstatetype"></a><a name="codecvt__state_type"></a>  codecvt:: state_type  
 Tipo de carácter que se usa para representar los estados intermedios durante las conversiones entre las representaciones internas y externas.  
  
```  
typedef StateType state_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **StateType**.  
  
##  <a name="a-namecodecvtunshifta-codecvtunshift"></a><a name="codecvt__unshift"></a>  codecvt:: unshift  
 Proporciona el **bytes**s necesarios en una conversión dependiente del estado para completar el último carácter de una secuencia de **bytes**s.  
  
```  
result unshift(
    StateType& _State,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_State`  
 El estado de conversión que se mantiene entre las llamadas a la función miembro.  
  
 ` first2`  
 Puntero a la primera posición del intervalo de destino.  
  
 ` last2`  
 Puntero a la última posición del intervalo de destino.  
  
 ` next2`  
 Puntero al primer elemento sin modificaciones en la secuencia de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la función:  
  
- **codecvt_base::error** Si estado representa un estado no válido.  
  
- `codecvt_base::noconv` Si la función realiza ninguna conversión.  
  
- **codecvt_base::OK** Si la conversión se realiza correctamente.  
  
- **codecvt_base::Partial** Si el destino no es lo suficientemente grande como para la conversión se realice correctamente.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro virtual protegida intenta convertir el elemento de origen **CharType**(0) en una secuencia de destino que almacena en [ ` first2`, ` last2`), excepto el elemento terminación **bytes**(0). Siempre se almacena en ` next2` un puntero al primer elemento sin modificaciones en la secuencia de destino.  
  
 `_State` debe representar el estado de la conversión inicial al principio de una nueva secuencia de origen. La función modifica su valor almacenado, según sea necesario, para reflejar el estado actual de una conversión correcta. Normalmente, convertir el elemento de origen **CharType**(0) deja el estado actual en el estado de la conversión inicial.  
  
 La función miembro devuelve [do_unshift](#codecvt__do_unshift)( `_State`, ` first2`, ` last2`, ` next2` ).  
  
## <a name="see-also"></a>Vea también  
 [\< configuración regional>](../standard-library/locale.md)   
 [Páginas de códigos](../c-runtime-library/code-pages.md)   
 [Nombres de configuración regional, idiomas y cadenas de país o región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

