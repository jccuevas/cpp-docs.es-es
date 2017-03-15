---
title: codecvt (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- codecvt
- std::codecvt
- std.codecvt
- xlocale/std::codecvt
dev_langs:
- C++
helpviewer_keywords:
- codecvt class
ms.assetid: 37d3efa1-2b7f-42b6-b04f-7a972c8c2c86
caps.latest.revision: 23
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
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 60b86a54be164e896a15ab46584aa6f4339c58ab
ms.lasthandoff: 02/24/2017

---
# <a name="codecvt-class"></a>codecvt (Clase)
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
 La clase de plantilla describe un objeto que puede actuar como [faceta de configuración regional](../standard-library/locale-class.md#facet_class), para controlar las conversiones entre una secuencia de valores de tipo `CharType` y una secuencia de valores de tipo `Byte`. La clase `StateType` caracteriza la transformación y un objeto de clase `StateType` almacena la información de estado necesaria durante una conversión.  
  
 La codificación interna emplea una representación con un número fijo de bytes por carácter, normalmente de tipo `char` o de tipo `wchar_t`.  
  
 Como ocurre con cualquier faceta de configuración regional, el `id` de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en `id`.  
  
 Las versiones de plantilla de [do_in](#codecvt__do_in) y [do_out](#codecvt__do_out) siempre devuelven `codecvt_base::noconv`.  
  
 La biblioteca estándar de C++ define varias especializaciones explícitas:  
  
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
  
### <a name="typedefs"></a>Definiciones de tipo  
  
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
|[encoding](#codecvt__encoding)|Comprueba si la codificación del flujo `Byte` depende del estado, si la relación entre los `Byte`s usados y los `CharType`s generados es constante y, en tal caso, determina el valor de esa relación.|  
|[in](#codecvt__in)|Convierte una representación externa de una secuencia de `Byte`s en una representación interna de una secuencia de `CharType`s.|  
|[length](#codecvt__length)|Determina cuántos `Byte`s de una secuencia dada de `Byte`s externos generan no más de un número determinado de `CharType`s internos y devuelve ese número de `Byte`s.|  
|[max_length](#codecvt__max_length)|Devuelve el número máximo de `Byte`s externos necesarios para generar un `CharType` interno.|  
|[out](#codecvt__out)|Convierte una secuencia de `CharType`s internos en una secuencia de `Byte`s externos.|  
|[unshift](#codecvt__unshift)|Proporciona los `Byte`s externos necesarios en una conversión dependiente del estado para completar el último carácter de la secuencia de `Byte`s.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<locale>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-namecodecvtalwaysnoconva--codecvtalwaysnoconv"></a><a name="codecvt__always_noconv"></a>  codecvt::always_noconv  
 Comprueba si no es necesario realizar ninguna conversión.  
  
```  
bool always_noconv() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor booleano que es **True** si es no necesario realizar ninguna conversión; **False** es que se debe realizar al menos una.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [do_always_noconv](#codecvt__do_always_noconv).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
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
  
##  <a name="a-namecodecvtcodecvta--codecvtcodecvt"></a><a name="codecvt__codecvt"></a>  codecvt::codecvt  
 Constructor de objetos de clase codecvt que actúa como faceta de configuración regional para controlar las conversiones.  
  
```  
explicit codecvt(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Refs`  
 Valor entero que se usa para especificar el tipo de administración de memoria del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Los valores posibles del parámetro `_Refs` y su importancia son:  
  
-   0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.  
  
-   1: la vigencia del objeto se debe administrar de manera manual.  
  
-   \> 0: estos valores no están definidos.  
  
 El constructor inicializa su objeto base `locale::facet` con **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`) *.*  
  
##  <a name="a-namecodecvtdoalwaysnoconva--codecvtdoalwaysnoconv"></a><a name="codecvt__do_always_noconv"></a>  codecvt::do_always_noconv  
 Función virtual a la que se llama para comprobar si no es necesario realizar ninguna conversión.  
  
```  
virtual bool do_always_noconv() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro virtual protegida devuelve **True** solo si todas las llamadas a [do_in](#codecvt__do_in) o [do_out](#codecvt__do_out) devuelven **noconv**.  
  
 La versión de plantilla devuelve siempre **True**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [always_noconv](#codecvt__always_noconv), que llama a `do_always_noconv`.  
  
##  <a name="a-namecodecvtdoencodinga--codecvtdoencoding"></a><a name="codecvt__do_encoding"></a>  codecvt::do_encoding  
 Función virtual que comprueba si la codificación del flujo **Byte** depende del estado, si la relación entre los **Byte**s usados y los **CharType**s generados es constante y, en tal caso, determina el valor de esa relación.  
  
```  
virtual int do_encoding() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro virtual protegida devuelve:  
  
-   -1, si la codificación de secuencias de tipo `extern_type` depende del estado.  
  
-   0, si la codificación implica secuencias de longitud variable.  
  
- *N*, si la codificación implica solo secuencias de longitud *N*  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [encoding](#codecvt__encoding), que llama a `do_encoding`.  
  
##  <a name="a-namecodecvtdoina--codecvtdoin"></a><a name="codecvt__do_in"></a>  codecvt::do_in  
 Función virtual a la que se llama para convertir una secuencia de **Byte**s externos en una secuencia de **CharType**s internos.  
  
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
 Puntero más allá del final de la secuencia convertida, al primer carácter sin convertir.  
  
 ` first2`  
 Puntero al principio de la secuencia convertida.  
  
 ` last2`  
 Puntero al final de la secuencia convertida.  
  
 ` next2`  
 Puntero al **CharType** que viene después del último **CharType** convertido, hasta el primer carácter sin modificaciones en la secuencia de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor devuelto que indica si la operación se ha realizado correctamente, parcialmente o no se ha realizado correctamente. La función devuelve:  
  
- **codecvt_base::error** si la secuencia de origen tiene un formato incorrecto.  
  
- `codecvt_base::noconv` si la función no realiza ninguna conversión.  
  
- **codecvt_base::ok** si la conversión se realiza correctamente.  
  
- **codecvt_base::partial** si el origen no es suficiente o si el destino no es lo suficientemente grande como para que la conversión se realice correctamente.  
  
### <a name="remarks"></a>Comentarios  
 `_State` debe representar el estado de conversión inicial al principio de una nueva secuencia de origen. La función modifica su valor almacenado según sea necesario para reflejar el estado actual de una conversión correcta. De lo contrario, su valor almacenado no se especifica.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [in](#codecvt__in), que llama a `do_in`.  
  
##  <a name="a-namecodecvtdolengtha--codecvtdolength"></a><a name="codecvt__do_length"></a>  codecvt::do_length  
 Función virtual que determina cuántos **Byte**s de una secuencia determinada de **Byte**s externos generan no más de un número determinado de **CharType**s internos y devuelve ese número de **Byte**s.  
  
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
 Puntero al principio de la secuencia externa.  
  
 ` last1`  
 Puntero al final de la secuencia externa.  
  
 `_Len2`  
 El número máximo de **Byte**s que puede devolver la función miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero que representa el número máximo de conversiones, no mayor que `_Len2`, definido por la secuencia de origen externo en [ ` first1`, ` last1`).  
  
### <a name="remarks"></a>Comentarios  
 La función miembro virtual protegida llama a `do_in`( `_State`, ` first1`, ` last1`, ` next1`, `_Buf`, `_Buf` + `_Len2`, ` next2`) para `_State` (una copia del estado), algún búfer `_Buf` y punteros ` next1` y ` next2`.  
  
 Después, devuelve ` next2` – **buf**. Por tanto, cuenta el número máximo de conversiones, no mayor que `_Len2`, definido por la secuencia de origen en [ ` first1`, ` last1`).  
  
 La versión de plantilla devuelve siempre el menor de ` last1` – ` first1` y `_Len2`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [length](#codecvt__length), que llama a **do_length**.  
  
##  <a name="a-namecodecvtdomaxlengtha--codecvtdomaxlength"></a><a name="codecvt__do_max_length"></a>  codecvt::do_max_length  
 Función virtual que devuelve el número máximo de **Byte**s externos necesarios para generar un **CharType** interno.  
  
```  
virtual int do_max_length() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número máximo de **bytes**s necesarios para generar un **CharType**.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro virtual protegida devuelve el mayor valor posible que puede devolver [do_length](#codecvt__do_length)( ` first1`, ` last1`, 1) para los valores válidos arbitrarios de ` first1` y ` last1`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [max_length](#codecvt__max_length), que llama a `do_max_length`.  
  
##  <a name="a-namecodecvtdoouta--codecvtdoout"></a><a name="codecvt__do_out"></a>  codecvt::do_out  
 Función virtual a la que se llama para convertir una secuencia de **CharType**s en una secuencia de **Byte**s externos.  
  
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
 Referencia a un puntero al primer **CharType** sin convertir, después del último **CharType** convertido.  
  
 ` first2`  
 Puntero al principio de la secuencia convertida.  
  
 ` last2`  
 Puntero al final de la secuencia convertida.  
  
 ` next2`  
 Referencia a un puntero al primer **Byte** sin convertir, después del último **Byte** convertido.  
  
### <a name="return-value"></a>Valor devuelto  
 La función devuelve:  
  
- **codecvt_base::error** si la secuencia de origen tiene un formato incorrecto.  
  
- `codecvt_base::noconv` si la función no realiza ninguna conversión.  
  
- **codecvt_base::ok** si la conversión se realiza correctamente.  
  
- **codecvt_base::partial** si el origen no es suficiente o si el destino no es lo suficientemente grande como para que la conversión se realice correctamente.  
  
### <a name="remarks"></a>Comentarios  
 `_State` debe representar el estado de conversión inicial al principio de una nueva secuencia de origen. La función modifica su valor almacenado según sea necesario para reflejar el estado actual de una conversión correcta. De lo contrario, su valor almacenado no se especifica.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [out](#codecvt__out), que llama a `do_out`.  
  
##  <a name="a-namecodecvtdounshifta--codecvtdounshift"></a><a name="codecvt__do_unshift"></a>  codecvt::do_unshift  
 Función virtual a la que se llama para proporcionar los **Byte**s necesarios en una conversión dependiente del estado para completar el último carácter de una secuencia de **Byte**s.  
  
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
 La función devuelve:  
  
- **codecvt_base::error** si _ *State* representa un estado no válido  
  
- `codecvt_base::noconv` si la función no realiza ninguna conversión  
  
- **codecvt_base::ok** si la conversión se realiza correctamente  
  
- **codecvt_base::partial** si el destino no es lo suficientemente grande como para que la conversión se realice correctamente  
  
### <a name="remarks"></a>Comentarios  
 La función miembro virtual protegida intenta convertir el elemento de origen **CharType**(0) en una secuencia de destino que almacena en [ ` first2`, ` last2`), excepto el elemento que finaliza **Byte**(0). Siempre almacena en ` next2` un puntero al primer elemento sin modificaciones en la secuencia de destino.  
  
 _ *State* debe representar el estado de conversión inicial al principio de una nueva secuencia de origen. La función modifica su valor almacenado según sea necesario para reflejar el estado actual de una conversión correcta. Normalmente, al convertir el elemento de origen **CharType**(0), el estado actual queda en el estado de conversión inicial.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [unshift](#codecvt__unshift), que llama a `do_unshift`.  
  
##  <a name="a-namecodecvtencodinga--codecvtencoding"></a><a name="codecvt__encoding"></a>  codecvt::encoding  
 Comprueba si la codificación del flujo **Byte** depende del estado, si la relación entre los **Byte**s usados y los **CharType**s generados es constante y, en tal caso, determina el valor de esa relación.  
  
```  
int encoding() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el valor devuelto es positivo, ese valor es el número constante de caracteres **Byte** necesarios para producir el carácter **CharType**.  
  
 La función miembro virtual protegida devuelve:  
  
-   -1, si la codificación de secuencias de tipo `extern_type` depende del estado.  
  
-   0, si la codificación implica secuencias de longitud variable.  
  
- *N*, si la codificación implica solo secuencias de longitud *N.*  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [do_encoding](#codecvt__do_encoding).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
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
  
##  <a name="a-namecodecvtexterntypea--codecvtexterntype"></a><a name="codecvt__extern_type"></a>  codecvt::extern_type  
 Tipo de carácter que se usa para las representaciones externas.  
  
```  
typedef Byte extern_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **Byte**.  
  
##  <a name="a-namecodecvtina--codecvtin"></a><a name="codecvt__in"></a>  codecvt::in  
 Convierte una representación externa de una secuencia de **Byte**s en una representación interna de una secuencia de **CharType**s.  
  
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
 Puntero más allá del final de la secuencia convertida, al primer carácter sin convertir.  
  
 ` first2`  
 Puntero al principio de la secuencia convertida.  
  
 ` last2`  
 Puntero al final de la secuencia convertida.  
  
 ` next2`  
 Puntero al **CharType** que viene después del último **CharType** convertido, hasta el primer carácter sin modificaciones en la secuencia de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor devuelto que indica si la operación se ha realizado correctamente, parcialmente o no se ha realizado correctamente. La función devuelve:  
  
- **codecvt_base::error** si la secuencia de origen tiene un formato incorrecto.  
  
- `codecvt_base::noconv` si la función no realiza ninguna conversión.  
  
- **codecvt_base::ok** si la conversión se realiza correctamente.  
  
- **codecvt_base::partial** si el origen no es suficiente o si el destino no es lo suficientemente grande como para que la conversión se realice correctamente.  
  
### <a name="remarks"></a>Comentarios  
 `_State` debe representar el estado de conversión inicial al principio de una nueva secuencia de origen. La función modifica su valor almacenado según sea necesario para reflejar el estado actual de una conversión correcta. Después de una conversión parcial, `_State` debe establecerse de tal modo que permita que la conversión se reanude cuando lleguen nuevos caracteres.  
  
 La función miembro devuelve [do_in](#codecvt__do_in)( `_State`, _ *First1,  last1,  next1, First2, _Llast2,  next2*).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
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
  
##  <a name="a-namecodecvtinterntypea--codecvtinterntype"></a><a name="codecvt__intern_type"></a>  codecvt::intern_type  
 Tipo de carácter que se usa para las representaciones internas.  
  
```  
typedef CharType intern_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **CharType**.  
  
##  <a name="a-namecodecvtlengtha--codecvtlength"></a><a name="codecvt__length"></a>  codecvt::length  
 Determina cuántos **Byte**s de una secuencia determinada de **Byte**s externos generan no más de un número determinado de **CharType**s internos y devuelve ese número de **Byte**s.  
  
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
 Puntero al principio de la secuencia externa.  
  
 ` last1`  
 Puntero al final de la secuencia externa.  
  
 `_Len2`  
 El número máximo de Bytes que puede devolver la función miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero que representa el número máximo de conversiones, no mayor que `_Len2`, definido por la secuencia de origen externo en [ ` first1`, ` last1`).  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [do_length](#codecvt__do_length)( *_State,  first1*, ` last1`, `_Len2`).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
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
  
##  <a name="a-namecodecvtmaxlengtha--codecvtmaxlength"></a><a name="codecvt__max_length"></a>  codecvt::max_length  
 Devuelve el número máximo de **Byte**s externos necesarios para generar un **CharType** interno.  
  
```  
int max_length() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número máximo de **bytes**s necesarios para generar un **CharType**.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [do_max_length](#codecvt__do_max_length).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
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
  
##  <a name="a-namecodecvtouta--codecvtout"></a><a name="codecvt__out"></a>  codecvt::out  
 Convierte una secuencia de **CharType**s internos en una secuencia de **Byte**s externos.  
  
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
 Referencia a un puntero al primer **CharType** sin convertir, después del último **CharType** convertido.  
  
 ` first2`  
 Puntero al principio de la secuencia convertida.  
  
 ` last2`  
 Puntero al final de la secuencia convertida.  
  
 ` next2`  
 Referencia a un puntero al primer **Byte** sin convertir, después del último **Byte** convertido.  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro devuelve [do_out](#codecvt__do_out)( `_State`, ` first1`, ` last1`, ` next1`, ` first2`, ` last2`, ` next2`).  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, vea [codecvt::do_out](#codecvt__do_out).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
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
  
##  <a name="a-namecodecvtstatetypea--codecvtstatetype"></a><a name="codecvt__state_type"></a>  codecvt::state_type  
 Tipo de carácter que se usa para representar los estados intermedios durante las conversiones entre las representaciones internas y externas.  
  
```  
typedef StateType state_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **StateType**.  
  
##  <a name="a-namecodecvtunshifta--codecvtunshift"></a><a name="codecvt__unshift"></a>  codecvt::unshift  
 Proporciona los **Byte**s necesarios en una conversión dependiente del estado para completar el último carácter de una secuencia de **Byte**s.  
  
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
 La función devuelve:  
  
- **codecvt_base::error** si el estado representa un estado no válido.  
  
- `codecvt_base::noconv` si la función no realiza ninguna conversión.  
  
- **codecvt_base::ok** si la conversión se realiza correctamente.  
  
- **codecvt_base::partial** si el destino no es lo suficientemente grande como para que la conversión se realice correctamente.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro virtual protegida intenta convertir el elemento de origen **CharType**(0) en una secuencia de destino que almacena en [ ` first2`, ` last2`), excepto el elemento que finaliza **Byte**(0). Siempre almacena en ` next2` un puntero al primer elemento sin modificaciones en la secuencia de destino.  
  
 `_State` debe representar el estado de conversión inicial al principio de una nueva secuencia de origen. La función modifica su valor almacenado según sea necesario para reflejar el estado actual de una conversión correcta. Normalmente, al convertir el elemento de origen **CharType**(0), el estado actual queda en el estado de conversión inicial.  
  
 La función miembro devuelve [do_unshift](#codecvt__do_unshift)( `_State`, ` first2`, ` last2`, ` next2` ).  
  
## <a name="see-also"></a>Vea también  
 [\<locale>](../standard-library/locale.md)   
 [Páginas de códigos](../c-runtime-library/code-pages.md)   
 [Nombres de configuración regional, idiomas y cadenas de país/región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)


