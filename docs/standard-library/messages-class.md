---
title: messages (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages
- xlocmes/std::messages::char_type
- xlocmes/std::messages::string_type
- xlocmes/std::messages::close
- xlocmes/std::messages::do_close
- xlocmes/std::messages::do_get
- xlocmes/std::messages::do_open
- xlocmes/std::messages::get
- xlocmes/std::messages::open
helpviewer_keywords:
- std::messages [C++]
- std::messages [C++], char_type
- std::messages [C++], string_type
- std::messages [C++], close
- std::messages [C++], do_close
- std::messages [C++], do_get
- std::messages [C++], do_open
- std::messages [C++], get
- std::messages [C++], open
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
ms.openlocfilehash: deb9eaedba3c99bb2fcb8399ac412ccedb11545f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375922"
---
# <a name="messages-class"></a>messages (Clase)

La plantilla de clase describe un objeto que puede servir como una faceta de configuración regional para recuperar mensajes localizados de un catálogo de mensajes internacionalizados para una configuración regional determinada.

Actualmente, mientras se implementa la clase messages, no hay mensajes.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType>
class messages : public messages_base;
```

### <a name="parameters"></a>Parámetros

*CharType*\
Tipo usado dentro de un programa para codificar los caracteres de una configuración regional.

## <a name="remarks"></a>Observaciones

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**

Básicamente esta faceta abre un catálogo de mensajes definidos en la clase base messages_base, recupera la información necesaria y cierra el catálogo.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[Mensajes](#messages)|Función constructor de la faceta de mensajes.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo de carácter usado para mostrar mensajes.|
|[string_type](#string_type)|Un tipo que describe una cadena de tipo `basic_string` que contiene caracteres de tipo `CharType`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Cerca](#close)|Cierra el catálogo de mensajes.|
|[do_close](#do_close)|Una función virtual llamada para perder el catálogo de mensajes.|
|[do_get](#do_get)|Una función virtual llamada para recuperar el catálogo de mensajes.|
|[do_open](#do_open)|Una función virtual llamada para abrir el catálogo de mensajes.|
|[get](#get)|Recupera el catálogo de mensajes.|
|[open](#open)|Abre el catálogo de mensajes.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<locale>

**Espacio de nombres:** std

## <a name="messageschar_type"></a><a name="char_type"></a>mensajes::char_type

Tipo de carácter usado para mostrar mensajes.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla **CharType**.

## <a name="messagesclose"></a><a name="close"></a>mensajes::cerrar

Cierra el catálogo de mensajes.

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>Parámetros

*_Catval*\
El catálogo que se va a cerrar.

### <a name="remarks"></a>Observaciones

La función miembro llama a [do_close](#do_close)(_ *Catval*).

## <a name="messagesdo_close"></a><a name="do_close"></a>messages::do_close

Una función virtual llamada para perder el catálogo de mensajes.

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>Parámetros

*_Catval*\
El catálogo que se va a cerrar.

### <a name="remarks"></a>Observaciones

La función miembro protegida cierra el catálogo de *_Catval*, que debe haber sido abierto por una llamada anterior a [do_open](#do_open).

*_Catval* debe obtenerse de un catálogo abierto anteriormente que no esté cerrado.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [close](#close), que llama a `do_close`.

## <a name="messagesdo_get"></a><a name="do_get"></a>mensajes::do_get

Una función virtual llamada para recuperar el catálogo de mensajes.

```cpp
virtual string_type do_get(
    catalog _Catval,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Parámetros

*_Catval*\
El valor de identificación que especifica el catálogo de mensajes que se va a buscar.

*_Set*\
El primer identificado localizaba un mensaje en un catálogo de mensajes.

*_Message*\
El segundo identificado localizaba un mensaje en un catálogo de mensajes.

*_Dfault*\
La cadena que se va a devolver en caso de error.

### <a name="return-value"></a>Valor devuelto

Devuelve una copia de *_Dfault* en caso de error. De otro modo, devuelve una copia de la secuencia de mensajes especificada.

### <a name="remarks"></a>Observaciones

La función miembro protegida intenta obtener una secuencia de mensajes del catálogo de *_Catval*. Puede hacer uso de *_Set,* *_Message,* y *_Dfault* al hacerlo.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get](#get), que llama a `do_get`.

## <a name="messagesdo_open"></a><a name="do_open"></a>mensajes::do_open

Una función virtual llamada para abrir el catálogo de mensajes.

```cpp
virtual catalog do_open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Parámetros

*_Catname*\
El nombre del catálogo que se va a buscar.

*_Loc*\
La configuración regional que se está buscando en el catálogo.

### <a name="return-value"></a>Valor devuelto

Devuelve un valor que se compara con menos de cero en caso de error. De otro modo, el valor devuelto puede usarse como el primer argumento en una llamada posterior a [get](#get).

### <a name="remarks"></a>Observaciones

La función miembro protegida intenta abrir un catálogo de mensajes cuyo nombre es *_Catname*. Puede hacer uso de la *_Loc* de la configuración regional al hacerlo

El valor devuelto debe usarse como el argumento en una llamada posterior a [close](#close).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [open](#open), que llama a `do_open`.

## <a name="messagesget"></a><a name="get"></a>mensajes::get

Recupera el catálogo de mensajes.

```cpp
string_type get(
    catalog _CatVal,
    int _Set,
    int _Message,
    const string_type& _Dfault) const;
```

### <a name="parameters"></a>Parámetros

*_Catval*\
El valor de identificación que especifica el catálogo de mensajes que se va a buscar.

*_Set*\
El primer identificado localizaba un mensaje en un catálogo de mensajes.

*_Message*\
El segundo identificado localizaba un mensaje en un catálogo de mensajes.

*_Dfault*\
La cadena que se va a devolver en caso de error.

### <a name="return-value"></a>Valor devuelto

Devuelve una copia de *_Dfault* en caso de error. De otro modo, devuelve una copia de la secuencia de mensajes especificada.

### <a name="remarks"></a>Observaciones

La función miembro `_Set`devuelve `_Message` `_Dfault` [do_get](#do_get)( `_Catval`, , , ).

## <a name="messagesmessages"></a><a name="messages"></a>mensajes::mensajes

Función constructor de la faceta de mensajes.

```cpp
explicit messages(
    size_t _Refs = 0);

protected: messages(
    const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Parámetros

*_Refs*\
Valor entero que se usa para especificar el tipo de administración de memoria del objeto.

*_Locname*\
El nombre de la configuración regional.

### <a name="remarks"></a>Observaciones

Los valores posibles para el parámetro *_Refs* y su importancia son:

- 0: la vigencia del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: la vigencia del objeto se debe administrar de manera manual.

- \>1: Estos valores no están definidos.

No es posible mostrar ejemplos directos, porque el destructor está protegido.

El constructor inicializa su objeto base con **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="messagesopen"></a><a name="open"></a>mensajes::abrir

Abre el catálogo de mensajes.

```cpp
catalog open(
    const string& _Catname,
    const locale& _Loc) const;
```

### <a name="parameters"></a>Parámetros

*_Catname*\
El nombre del catálogo que se va a buscar.

*_Loc*\
La configuración regional que se está buscando en el catálogo.

### <a name="return-value"></a>Valor devuelto

Devuelve un valor que se compara con menos de cero en caso de error. De otro modo, el valor devuelto puede usarse como el primer argumento en una llamada posterior a [get](#get).

### <a name="remarks"></a>Observaciones

La función miembro `_Catname` `_Loc`devuelve [do_open](#do_open)( , ).

## <a name="messagesstring_type"></a><a name="string_type"></a>mensajes::string_type

Un tipo que describe una cadena de tipo `basic_string` que contiene caracteres de tipo `CharType`.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de plantilla de clase [basic_string](../standard-library/basic-string-class.md) cuyos objetos pueden almacenar copias de las secuencias de mensajes.

## <a name="see-also"></a>Consulte también

[\<>de la localidad](../standard-library/locale.md)\
[Clase messages_base](../standard-library/messages-base-class.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
