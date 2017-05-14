---
title: messages (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- messages
- xlocmes/std::messages
- locale/std::messages::char_type
- locale/std::messages::string_type
- locale/std::messages::close
- locale/std::messages::do_close
- locale/std::messages::do_get
- locale/std::messages::do_open
- locale/std::messages::get
- locale/std::messages::open
dev_langs:
- C++
helpviewer_keywords:
- messages class
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: 8a3c647c9c64f2783bf2bc6d2eee86d7107af8d2
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="messages-class"></a>messages (Clase)
La clase de plantilla describe un objeto que puede actuar como una faceta de configuración regional para recuperar mensajes traducidos y adaptados de un catálogo de mensajes internacionalizados para una configuración regional concreta.  
  
 Actualmente, mientras se implementa la clase messages, no hay mensajes.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class CharType>  
class messages : public messages_base;
```  
  
#### <a name="parameters"></a>Parámetros  
 `CharType`  
 Tipo usado dentro de un programa para codificar los caracteres de una configuración regional.  
  
## <a name="remarks"></a>Comentarios  
 Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**  
  
 Básicamente esta faceta abre un catálogo de mensajes definidos en la clase base messages_base, recupera la información necesaria y cierra el catálogo.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[messages](#messages)|Función constructor de la faceta de mensajes.|  
  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[char_type](#char_type)|Tipo de carácter usado para mostrar mensajes.|  
|[string_type](#string_type)|Un tipo que describe una cadena de tipo `basic_string` que contiene caracteres de tipo `CharType`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[close](#close)|Cierra el catálogo de mensajes.|  
|[do_close](#do_close)|Una función virtual llamada para perder el catálogo de mensajes.|  
|[do_get](#do_get)|Una función virtual llamada para recuperar el catálogo de mensajes.|  
|[do_open](#do_open)|Una función virtual llamada para abrir el catálogo de mensajes.|  
|[get](#get)|Recupera el catálogo de mensajes.|  
|[open](#open)|Abre el catálogo de mensajes.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<locale>  
  
 **Espacio de nombres:** std  
  
##  <a name="char_type"></a> messages::char_type  
 Tipo de carácter usado para mostrar mensajes.  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla **CharType**.  
  
##  <a name="close"></a> messages::close  
 Cierra el catálogo de mensajes.  
  
```
void close(catalog _Catval) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Catval`  
 El catálogo que se va a cerrar.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro llama a [do_close](#do_close)(_ *Catval*).  
  
##  <a name="do_close"></a> messages::do_close  
 Una función virtual llamada para perder el catálogo de mensajes.  
  
```
virtual void do_close(catalog _Catval) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Catval`  
 El catálogo que se va a cerrar.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro protegida cierra el catálogo de mensajes `_Catval`, que debe haberse abierto mediante una llamada anterior a [do_open](#do_open).  
  
 *_Catval* debe obtenerse de un catálogo abierto anteriormente que no esté cerrado.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [close](#close), que llama a `do_close`.  
  
##  <a name="do_get"></a> messages::do_get  
 Una función virtual llamada para recuperar el catálogo de mensajes.  
  
```
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Catval`  
 El valor de identificación que especifica el catálogo de mensajes que se va a buscar.  
  
 `_Set`  
 El primer identificado localizaba un mensaje en un catálogo de mensajes.  
  
 `_Message`  
 El segundo identificado localizaba un mensaje en un catálogo de mensajes.  
  
 `_Dfault`  
 La cadena que se va a devolver en caso de error.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una copia de `_Dfault` en caso de error. De otro modo, devuelve una copia de la secuencia de mensajes especificada.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro protegida intenta obtener una secuencia de mensajes del catálogo de mensajes `_Catval`. Hace uso de `_Set`, `_Message` y `_Dfault` al hacerlo.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [get](#get), que llama a `do_get`.  
  
##  <a name="do_open"></a> messages::do_open  
 Una función virtual llamada para abrir el catálogo de mensajes.  
  
```
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Catname`  
 El nombre del catálogo que se va a buscar.  
  
 `_Loc`  
 La configuración regional que se está buscando en el catálogo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor que se compara con menos de cero en caso de error. De otro modo, el valor devuelto puede usarse como el primer argumento en una llamada posterior a [get](#get).  
  
### <a name="remarks"></a>Comentarios  
 La función miembro protegida intenta abrir un catálogo de mensajes cuyo nombre es `_Catname`. Hace uso de la configuración regional `_Loc` al hacerlo  
  
 El valor devuelto debe usarse como el argumento en una llamada posterior a [close](#close).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [open](#open), que llama a `do_open`.  
  
##  <a name="get"></a> messages::get  
 Recupera el catálogo de mensajes.  
  
```
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Catval`  
 El valor de identificación que especifica el catálogo de mensajes que se va a buscar.  
  
 `_Set`  
 El primer identificado localizaba un mensaje en un catálogo de mensajes.  
  
 `_Message`  
 El segundo identificado localizaba un mensaje en un catálogo de mensajes.  
  
 `_Dfault`  
 La cadena que se va a devolver en caso de error.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una copia de `_Dfault` en caso de error. De otro modo, devuelve una copia de la secuencia de mensajes especificada.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [do_get](#do_get)( `_Catval`, `_Set`, `_Message`, `_Dfault`).  
  
##  <a name="messages"></a> messages::messages  
 Función constructor de la faceta de mensajes.  
  
```
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Refs`  
 Valor entero que se usa para especificar el tipo de administración de memoria del objeto.  
  
 `_Locname`  
 El nombre de la configuración regional.  
  
### <a name="remarks"></a>Comentarios  
 Los valores posibles del parámetro `_Refs` y su importancia son:  
  
-   0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.  
  
-   1: la vigencia del objeto se debe administrar de manera manual.  
  
-   \>1: no se definen estos valores.  
  
 No es posible mostrar ejemplos directos, porque el destructor está protegido.  
  
 El constructor inicializa su objeto base con **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`).  
  
##  <a name="open"></a> messages::open  
 Abre el catálogo de mensajes.  
  
```
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Catname`  
 El nombre del catálogo que se va a buscar.  
  
 `_Loc`  
 La configuración regional que se está buscando en el catálogo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor que se compara con menos de cero en caso de error. De otro modo, el valor devuelto puede usarse como el primer argumento en una llamada posterior a [get](#get).  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve [do_open](#do_open)( `_Catname`, `_Loc`).  
  
##  <a name="string_type"></a> messages::string_type  
 Un tipo que describe una cadena de tipo `basic_string` que contiene caracteres de tipo **CharType**.  
  
```
typedef basic_string<CharType, Traits, Allocator> string_type;
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [basic_string](../standard-library/basic-string-class.md) cuyos objetos pueden almacenar copias de las secuencias de mensajes.  
  
## <a name="see-also"></a>Vea también  
 [\<locale>](../standard-library/locale.md)   
 [messages_base (Clase)](../standard-library/messages-base-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)




