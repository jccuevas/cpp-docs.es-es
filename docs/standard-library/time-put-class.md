---
title: time_put (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- time_put
- xloctime/std::time_put
- locale/std::time_put::char_type
- locale/std::time_put::iter_type
- locale/std::time_put::do_put
- locale/std::time_put::put
dev_langs:
- C++
helpviewer_keywords:
- time_put class
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
caps.latest.revision: 22
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
ms.openlocfilehash: 0331580941a30b8d6ab9468ce95182950478ddcb
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="timeput-class"></a>time_put (Clase)
La clase de plantilla describe un objeto que puede actuar como una faceta de la configuración regional para controlar las conversiones de valores de hora en secuencias de tipo `CharType`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class CharType,  
    class OutputIterator = ostreambuf_iterator<CharType>>  
class time_put : public locale::facet;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `CharType`  
 Tipo usado dentro de un programa para codificar caracteres.  
  
 `OutputIterator`  
 El tipo de iterador en el que las funciones time put escriben sus resultados.  
  
## <a name="remarks"></a>Comentarios  
 Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[time_put](#time_put)|Constructor para los objetos de tipo `time_put`.|  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[char_type](#char_type)|Tipo que se usa para describir un carácter empleado por una configuración regional.|  
|[iter_type](#iter_type)|Tipo que describe un iterador de salida.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[do_put](#do_put)|Una función virtual que genera información de hora y fecha como una secuencia de `CharType`s.|  
|[put](#put)|Genera información de hora y fecha como una secuencia de `CharType`s.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<locale>  
  
 **Espacio de nombres:** std  
  
##  <a name="char_type"></a>  time_put::char_type  
 Tipo que se usa para describir un carácter empleado por una configuración regional.  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **CharType**.  
  
##  <a name="do_put"></a>  time_put::do_put  
 Una función virtual que genera información de hora y fecha como una secuencia de elementos **CharType**.  
  
```  
virtual iter_type do_put(
    iter_type next,   
    ios_base& _Iosbase,  
    const tm* _Pt,   
    char _Fmt,   
    char _Mod = 0) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `next`  
 Un iterador de salida en el que se va a insertar la secuencia de caracteres que representan la fecha y la hora.  
  
 `_Iosbase`  
 Sin usar.  
  
 `_Pt`  
 La información de fecha y hora que se va a representar.  
  
 `_Fmt`  
 El formato de la salida. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.  
  
 `_Mod`  
 Un modificador para el formato. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador a la primera posición después del último elemento insertado.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro virtual protegida genera elementos secuenciales, empezando por `next` a partir de los valores de hora almacenados en el objeto \* `_Pt`, del tipo **tm**. La función devuelve un iterador que designa el lugar siguiente para insertar un elemento más allá de la salida generada.  
  
 La salida se genera por las mismas reglas usadas por `strftime`, con un último argumento de `_Pt`, para generar una serie de elementos `char` en una matriz. Se supone que cada uno de estos elementos `char` se asigna a un elemento equivalente de tipo **CharType** mediante una asignación simple, uno a uno. Si `_Mod` es igual a cero, el formato eficaz es "%F", donde F es reemplazado por `_Fmt`. De lo contrario, el formato eficaz es "%MF", donde M es reemplazado por `_Mod`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [put](#put), que llama a `do_put`.  
  
##  <a name="iter_type"></a>  time_put::iter_type  
 Tipo que describe un iterador de salida.  
  
```  
typedef OutputIterator iter_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **OutputIterator**.  
  
##  <a name="put"></a>  time_put::put  
 Genera información de hora y fecha como una secuencia de elementos **CharType**.  
  
```  
iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;

iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    const CharType* first,
    const CharType* last) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `next`  
 Un iterador de salida en el que se va a insertar la secuencia de caracteres que representan la fecha y la hora.  
  
 `_Iosbase`  
 Sin usar.  
  
 `_Fill`  
 El carácter de tipo **CharType** usado para el espaciado.  
  
 `_Pt`  
 La información de fecha y hora que se va a representar.  
  
 `_Fmt`  
 El formato de la salida. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.  
  
 `_Mod`  
 Un modificador para el formato. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.  
  
 `first`  
 El principio de la cadena de formato para la salida. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.  
  
 `last`  
 El final de la cadena de formato para la salida. Vea [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para conocer los valores válidos.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador a la primera posición después del último elemento insertado.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro devuelve [do_put](#do_put)( `next`, `_Iosbase`, `_Fill`, `_Pt`, `_Fmt`, `_Mod`). La segunda función miembro copia en \* `next` ++ cualquier elemento en el intervalo [ `first`, `last`) que no sea un porcentaje (%). Para un porcentaje seguido de un carácter *C* en el intervalo [ `first`, `last`), la función evalúa en su lugar `next` = `do_put`( `next`, `_Iosbase`, `_Fill`, `_Pt`, *C*, 0) y omite *C*. Pero si *C* es un carácter calificador del conjunto EOQ#, seguido por un carácter `C2` en el intervalo [ `first`, `last`), la función evalúa en su lugar `next` = `do_put`( `next`, `_Iosbase`, `_Fill`, `_Pt`, `C2`, *C*) y omite `C2`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// time_put_put.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
#include <time.h>  
using namespace std;  
int main( )  
{  
   locale loc;  
   basic_stringstream<char> pszPutI;  
   ios_base::iostate st = 0;  
   struct tm t;  
   memset( &t, 0, sizeof( struct tm ) );  
  
   t.tm_hour = 5;  
   t.tm_min = 30;  
   t.tm_sec = 40;  
   t.tm_year = 00;  
   t.tm_mday = 4;  
   t.tm_mon = 6;  
  
   pszPutI.imbue( loc );  
   char *pattern = "x: %X %x";  
   use_facet <time_put <char> >  
   (loc).put(basic_ostream<char>::_Iter(pszPutI.rdbuf( )),  
          pszPutI, ' ', &t, pattern, pattern+strlen(pattern));  
  
      cout << "num_put( ) = " << pszPutI.rdbuf( )->str( ) << endl;  
  
      char strftimebuf[255];  
      strftime(&strftimebuf[0], 255, pattern, &t);  
      cout << "strftime( ) = " << &strftimebuf[0] << endl;  
}  
```  
  
```Output  
num_put( ) = x: 05:30:40 07/04/00  
strftime( ) = x: 05:30:40 07/04/00  
```  
  
##  <a name="time_put"></a>  time_put::time_put  
 Constructor para los objetos de tipo `time_put`.  
  
```  
explicit time_put(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Refs`  
 Valor entero que se usa para especificar el tipo de administración de memoria del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Los valores posibles del parámetro `_Refs` y su importancia son:  
  
-   0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.  
  
-   1: la vigencia del objeto se debe administrar de manera manual.  
  
-   \>1: no se definen estos valores.  
  
 El constructor inicializa su objeto base con [locale::facet](../standard-library/locale-class.md#facet_class)(*_Refs*).  
  
## <a name="see-also"></a>Vea también  
 [\<locale>](../standard-library/locale.md)   
 [time_base (Clase)](../standard-library/time-base-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)


