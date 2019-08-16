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
ms.openlocfilehash: f417c33d5502f8e5bd247936c8a0f93007239924
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449939"
---
# <a name="messages-class"></a>messages (Clase)

La clase de plantilla describe un objeto que puede actuar como una faceta de configuración regional para recuperar mensajes traducidos y adaptados de un catálogo de mensajes internacionalizados para una configuración regional concreta.

Actualmente, mientras se implementa la clase messages, no hay mensajes.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType>
class messages : public messages_base;
```

### <a name="parameters"></a>Parámetros

*CharType*\
Tipo usado dentro de un programa para codificar los caracteres de una configuración regional.

## <a name="remarks"></a>Comentarios

Como ocurre con cualquier faceta de configuración regional, el identificador de objeto estático tiene un valor almacenado inicial de cero. El primer intento de acceso a su valor almacenado almacena un valor positivo único en **id.**

Básicamente esta faceta abre un catálogo de mensajes definidos en la clase base messages_base, recupera la información necesaria y cierra el catálogo.

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[messages](#messages)|Función constructor de la faceta de mensajes.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|DESCRIPCIÓN|
|-|-|
|[char_type](#char_type)|Tipo de carácter usado para mostrar mensajes.|
|[string_type](#string_type)|Un tipo que describe una cadena de tipo `basic_string` que contiene caracteres de tipo `CharType`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
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

## <a name="char_type"></a> messages::char_type

Tipo de carácter usado para mostrar mensajes.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla **CharType**.

## <a name="close"></a> messages::close

Cierra el catálogo de mensajes.

```cpp
void close(catalog _Catval) const;
```

### <a name="parameters"></a>Parámetros

*_Catval*\
El catálogo que se va a cerrar.

### <a name="remarks"></a>Comentarios

La función miembro llama a [do_close](#do_close)(_ *Catval*).

## <a name="do_close"></a> messages::do_close

Una función virtual llamada para perder el catálogo de mensajes.

```cpp
virtual void do_close(catalog _Catval) const;
```

### <a name="parameters"></a>Parámetros

*_Catval*\
El catálogo que se va a cerrar.

### <a name="remarks"></a>Comentarios

La función miembro protegida cierra el catálogo de mensajes *_Catval*, que debe haber sido abierto por una llamada anterior a [do_open](#do_open).

*_Catval* debe obtenerse de un catálogo abierto anteriormente que no esté cerrado.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [close](#close), que llama a `do_close`.

## <a name="do_get"></a> messages::do_get

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

*_ Establecer*\
El primer identificado localizaba un mensaje en un catálogo de mensajes.

*_Message*\
El segundo identificado localizaba un mensaje en un catálogo de mensajes.

*_Dfault*\
La cadena que se va a devolver en caso de error.

### <a name="return-value"></a>Valor devuelto

Devuelve una copia de *_Dfault* en caso de error. De otro modo, devuelve una copia de la secuencia de mensajes especificada.

### <a name="remarks"></a>Comentarios

La función miembro protegida intenta obtener una secuencia de mensajes del catálogo de mensajes *_Catval*. Puede hacer uso de *_ Set*, *_Message*y *_Dfault* para hacerlo.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [get](#get), que llama a `do_get`.

## <a name="do_open"></a> messages::do_open

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

### <a name="remarks"></a>Comentarios

La función miembro protegida intenta abrir un catálogo de mensajes cuyo nombre es *_Catname*. Puede hacer uso de la configuración regional *_Loc* al hacerlo.

El valor devuelto debe usarse como el argumento en una llamada posterior a [close](#close).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [open](#open), que llama a `do_open`.

## <a name="get"></a> messages::get

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

*_ Establecer*\
El primer identificado localizaba un mensaje en un catálogo de mensajes.

*_Message*\
El segundo identificado localizaba un mensaje en un catálogo de mensajes.

*_Dfault*\
La cadena que se va a devolver en caso de error.

### <a name="return-value"></a>Valor devuelto

Devuelve una copia de *_Dfault* en caso de error. De otro modo, devuelve una copia de la secuencia de mensajes especificada.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_get](#do_get)( `_Catval`, `_Set`, `_Message`, `_Dfault`).

## <a name="messages"></a> messages::messages

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

### <a name="remarks"></a>Comentarios

Los valores posibles para el parámetro *_Refs* y su importancia son:

- 0: La duración del objeto se administra mediante las configuraciones regionales que lo contienen.

- 1: La duración del objeto debe administrarse manualmente.

- \> 1: Estos valores no están definidos.

No es posible mostrar ejemplos directos, porque el destructor está protegido.

El constructor inicializa su objeto base con **locale::** [facet](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="open"></a> messages::open

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

### <a name="remarks"></a>Comentarios

La función miembro devuelve [do_open](#do_open)( `_Catname`, `_Loc`).

## <a name="string_type"></a> messages::string_type

Un tipo que describe una cadena de tipo `basic_string` que contiene caracteres de tipo `CharType`.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [basic_string](../standard-library/basic-string-class.md) cuyos objetos pueden almacenar copias de las secuencias de mensajes.

## <a name="see-also"></a>Vea también

[\<locale>](../standard-library/locale.md)\
[messages_base (Clase)](../standard-library/messages-base-class.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
