---
title: wstring_convert (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- wstring/stdext::cvt::wstring_convert
- locale/std::wstring_convert::byte_string
- locale/std::wstring_convert::wide_string
- locale/std::wstring_convert::state_type
- locale/std::wstring_convert::int_type
- locale/std::wstring_convert::from_bytes
- locale/std::wstring_convert::to_bytes
- locale/std::wstring_convert::converted
- locale/std::wstring_convert::state
dev_langs: C++
helpviewer_keywords:
- stdext::cvt [C++], wstring_convert
- std::wstring_convert [C++], byte_string
- std::wstring_convert [C++], wide_string
- std::wstring_convert [C++], state_type
- std::wstring_convert [C++], int_type
- std::wstring_convert [C++], from_bytes
- std::wstring_convert [C++], to_bytes
- std::wstring_convert [C++], converted
- std::wstring_convert [C++], state
ms.assetid: e34f5b65-d572-4bdc-ac69-20778712e376
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e7a37fd636d376f379503d1dd1b95f05ac1828cd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="wstringconvert-class"></a>wstring_convert (Clase)
La clase de plantilla `wstring_convert` realiza conversiones entre una cadena de caracteres anchos y una cadena de bytes.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Codecvt, class Elem = wchar_t>
class wstring_convert
```  
  
#### <a name="parameters"></a>Parámetros  
 Codecvt  
 La faceta [locale](../standard-library/locale-class.md) que representa el objeto de conversión.  
  
 Elem  
 Tipo de elemento de carácter ancho.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla describe un objeto que controla las conversiones entre objetos de cadena de caracteres anchos de la clase `std::basic_string<Elem>` y objetos de cadena de bytes de la clase `std::basic_string<char>` (también conocida como `std::string`). La clase de plantilla define los tipos `wide_string` y `byte_string` como sinónimos de estos dos tipos. La conversión entre una secuencia de valores `Elem` (almacenada en un objeto `wide_string`) y las secuencias multibyte (almacenadas en un objeto `byte_string`) se realiza con un objeto de clase `Codecvt<Elem, char, std::mbstate_t>`, que cumple los requisitos de la faceta de conversión de código estándar `std::codecvt<Elem, char, std::mbstate_t>`.  
  
 Un objeto de esta clase de plantilla almacena lo siguiente:  
  
-   Una cadena de bytes que se mostrará al producirse errores  
  
-   Una cadena caracteres anchos que se mostrará al producirse errores  
  
-   Un puntero al objeto de conversión asignado (que se libera cuando el objeto wbuffer_convert se destruye)  
  
-   Un objeto de estado de la conversión de tipo [state_type](#state_type)  
  
-   Un recuento de conversión  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[wstring_convert](#wstring_convert)|Construye un objeto de tipo `wstring_convert`.|  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[byte_string](#byte_string)|Tipo que representa una cadena de bytes.|  
|[wide_string](#wide_string)|Tipo que representa una cadena de caracteres anchos.|  
|[state_type](#state_type)|Tipo que representa el estado de la conversión.|  
|[int_type](#int_type)|Tipo que representa un número entero.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[from_bytes](#from_bytes)|Convierte una cadena de bytes en una cadena de caracteres anchos.|  
|[to_bytes](#to_bytes)|Convierte una cadena de caracteres anchos en una cadena de bytes.|  
|[converted](#converted)|Devuelve el número de conversiones correctas.|  
|[state](#state)|Devuelve un objeto que representa el estado de la conversión.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<locale>  
  
 **Espacio de nombres:** std  
  
##  <a name="byte_string"></a>  wstring_convert::byte_string  
 Tipo que representa una cadena de bytes.  
  
```
typedef std::basic_string<char> byte_string;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `std::basic_string<char>`.  
  
##  <a name="converted"></a>  wstring_convert::converted  
 Devuelve el número de conversiones correctas.  
  
```
size_t converted() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de conversiones correctas.  
  
### <a name="remarks"></a>Comentarios  
 El número de conversiones correctas se almacena en el objeto de recuento de conversión.  
  
##  <a name="from_bytes"></a>  wstring_convert::from_bytes  
 Convierte una cadena de bytes en una cadena de caracteres anchos.  
  
```
wide_string from_bytes(char Byte);
wide_string from_bytes(const char* ptr);
wide_string from_bytes(const byte_string& Bstr);
wide_string from_bytes(const char* first, const char* last);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Byte`|La secuencia de bytes de un solo elemento que se van a convertir.|  
|`ptr`|La secuencia de caracteres de estilo C terminada en null que se va a convertir.|  
|`Bstr`|La [byte_string](#byte_string) que se va a convertir.|  
|`first`|El primer carácter de un intervalo de caracteres que se va convertir.|  
|`last`|El último carácter de un intervalo de caracteres que se va convertir.|  
  
### <a name="return-value"></a>Valor devuelto  
 Un objeto de cadena de caracteres anchos resultante de la conversión.  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto de [estado de conversión](../standard-library/wstring-convert-class.md) se creó con `not` con un valor explícito, se configura con su valor predeterminado (el estado inicial de la conversión) antes de comenzar la conversión. En caso contrario, se deja sin modificar.  
  
 El número de elementos de entrada convertidos correctamente se almacena en el objeto de recuento de conversión. Si no se produce ningún error de conversión, la función miembro devuelve la cadena de caracteres anchos convertida. De lo contrario, si el objeto se construyó con un inicializador para el mensaje de error de la cadena de caracteres anchos, la función miembro devolverá el objeto de mensaje de error de cadena de caracteres anchos. De lo contrario, la función miembro producirá un objeto de la clase [range_error](../standard-library/range-error-class.md).  
  
##  <a name="int_type"></a>  wstring_convert::int_type  
 Tipo que representa un número entero.  
  
```
typedef typename wide_string::traits_type::int_type int_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `wide_string::traits_type::int_type`.  
  
##  <a name="state"></a>  wstring_convert::state  
 Devuelve un objeto que representa el estado de la conversión.  
  
```
state_type state() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto de [estado de la conversión](../standard-library/wstring-convert-class.md) que representa el estado de la conversión.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="state_type"></a>  wstring_convert::state_type  
 Tipo que representa el estado de la conversión.  
  
```
typedef typename Codecvt::state_type state_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un objeto que puede representar un estado de conversión. El tipo es un sinónimo de `Codecvt::state_type`.  
  
##  <a name="to_bytes"></a>  wstring_convert::to_bytes  
 Convierte una cadena de caracteres anchos en una cadena de bytes.  
  
```
byte_string to_bytes(Elem Char);
byte_string to_bytes(const Elem* Wptr);
byte_string to_bytes(const wide_string& Wstr);
byte_string to_bytes(const Elem* first, const Elem* last);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Char`|El carácter ancho que se va a convertir.|  
|`Wptr`|La secuencia de estilo C terminada en null que empieza en `wptr` y que se va a convertir.|  
|`Wstr`|La [wide_string](#wide_string) que se va a convertir.|  
|`first`|El primer elemento del intervalo de elementos que se va a convertir.|  
|`last`|El último elemento del intervalo de elementos que se va a convertir.|  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto de [estado de conversión](../standard-library/wstring-convert-class.md) se creó con `not` con un valor explícito, se configura con su valor predeterminado (el estado inicial de la conversión) antes de comenzar la conversión. En caso contrario, se deja sin modificar.  
  
 El número de elementos de entrada convertidos correctamente se almacena en el objeto de recuento de conversión. Si no se produce ningún error de conversión, la función miembro devuelve la cadena de bytes convertida. De lo contrario, si el objeto se construyó con un inicializador para el mensaje de error de la cadena de bytes, la función miembro devolverá el objeto de mensaje de error de cadena de bytes. De lo contrario, la función miembro producirá un objeto de la clase [range_error](../standard-library/range-error-class.md).  
  
##  <a name="wide_string"></a>  wstring_convert::wide_string  
 Tipo que representa una cadena de caracteres anchos.  
  
```
typedef std::basic_string<Elem> wide_string;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `std::basic_string<Elem>`.  
  
##  <a name="wstring_convert"></a>  wstring_convert::wstring_convert  
 Construye un objeto de tipo `wstring_convert`.  
  
```
wstring_convert(Codecvt *Pcvt = new Codecvt);
wstring_convert(Codecvt *Pcvt, state_type _State);
wstring_convert(const byte_string& _Berr, const wide_string& Werr = wide_string());
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`*Pcvt`|Objeto de tipo `Codecvt` que va a realizar la conversión.|  
|`_State`|El objeto de tipo [state_type](#state_type) que representa el estado de la conversión.|  
|`_Berr`|La [byte_string](#byte_string) que se mostrará al producirse errores.|  
|`Werr`|La [wide_string](#wide_string) que se mostrará al producirse errores.|  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor almacena *Pcvt_arg* en el [objeto de conversión](../standard-library/wstring-convert-class.md)
