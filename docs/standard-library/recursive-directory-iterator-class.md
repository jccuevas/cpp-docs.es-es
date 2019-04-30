---
title: recursive_directory_iterator (Clase)
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: 52e6f738aa226dba26bae0cf6e97cd18d107d677
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370136"
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator (Clase)

Describe un iterador de entrada que secuencia a través de los nombres de archivo en un directorio, posiblemente descendiendo a los subdirectorios de forma recursiva. Para un iterador `X`, la expresión `*X` se evalúa como un objeto de clase `directory_entry` que contiene el nombre de archivo y cualquier elemento conocido sobre su estado.

Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Sintaxis

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Comentarios

La clase de plantilla almacena:

1. un objeto de tipo `stack<pair<directory_iterator, path>>`, llamado `mystack` aquí a efectos de la exposición, que representa el anidamiento de directorios que se va a secuenciar

1. un objeto de tipo `directory_entry` llamado `myentry` aquí, que representa el nombre de archivo actual en la secuencia del directorio

1. un objeto de tipo **bool**, llamado `no_push` aquí, que registra si está deshabilitado el descenso recursivo en subdirectorios

1. un objeto de tipo `directory_options`, llamado `myoptions` aquí, que registra las opciones establecidas en la construcción

Un objeto construido de forma predeterminada del tipo `recursive_directory_entry` tiene un iterador de final de secuencia en `mystack.top().first` y representa el iterador de final de secuencia. Por ejemplo, dado el directorio `abc` con entradas `def` (un directorio), `def/ghi`, y `jkl`, el código:

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

llamará a visit con los argumentos `path("abc/def/ghi")` y `path("abc/jkl")`. Puede calificar secuencias a través de un subárbol de directorio de dos maneras:

1. Un symlink de directorio se examinará solo si se construye un `recursive_directory_iterator` con un `directory_options` argumento cuyo valor es `directory_options::follow_directory_symlink`.

1. Si se llama a `disable_recursion_pending` , un directorio posterior encontrado durante un incremento no será examinado de forma recursiva.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|Construye un objeto `recursive_directory_iterator`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[depth](#depth)|Devuelve `mystack.size() - 1`, por lo que `pval` en profundidad de cero.|
|[disable_recursion_pending](#disable_recursion_pending)|Almacenes **true** en `no_push`.|
|[increment](#increment)|Avanza al siguiente nombre de archivo en secuencia.|
|[options](#options)|Devuelve `myoptions`.|
|[pop](#pop)|Devuelve el siguiente objeto.|
|[recursion_pending](#recursion_pending)|Devuelve `!no_push`.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator!=](#op_neq)|Devuelve `!(*this == right)`.|
|[operator=](#op_as)|Los operadores predeterminados de asignación de miembros se comportan según lo previsto.|
|[operator==](#op_eq)|Devuelve **true** sólo si ambos `*this` y *derecho* son iteradores de final de secuencia o ambos son no final-de-secuencia de los iteradores.|
|[operator*](#op_multiply)|Devuelve `myentry`.|
|[operator->](#op_cast)|Devuelve `&**this`.|
|[operator++](#op_increment)|Incrementa el `recursive_directory_iterator`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<filesystem >

**Espacio de nombres:** std::tr2::sys

## <a name="depth"></a> recursive_directory_iterator::depth

Devuelve `mystack.size() - 1`, por lo que `pval` en profundidad de cero.

```cpp
int depth() const;
```

## <a name="disable_recursion_pending"></a> recursive_directory_iterator::disable_recursion_pending

Almacenes **true** en `no_push`.

```cpp
void disable_recursion_pending();
```

## <a name="increment"></a> recursive_directory_iterator::increment

Avanza al siguiente nombre de archivo en secuencia.

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>Parámetros

*ec*<br/>
Código de error especificado.

### <a name="remarks"></a>Comentarios

La función intenta avanzar al siguiente nombre de archivo de la secuencia anidada. Si es correcta, almacena ese nombre de archivo en `myentry`; en caso contrario, genera un iterador de final de secuencia.

## <a name="op_neq"></a> recursive_directory_iterator::operator!=

Devuelve `!(*this == right)`.

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) para la comparación.

## <a name="op_as"></a> recursive_directory_iterator::operator=

Los operadores predeterminados de asignación de miembros se comportan según lo previsto.

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parámetros

*recursive_directory_iterator*<br/>
El [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) que se copia en el `recursive_directory_iterator`.

## <a name="op_eq"></a> recursive_directory_iterator::operator==

Devuelve **true** sólo si ambos `*this` y *derecho* son iteradores de final de secuencia o ambos son no final-de-secuencia de los iteradores.

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) para la comparación.

## <a name="op_multiply"></a> recursive_directory_iterator::operator*

Devuelve `myentry`.

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a> recursive_directory_iterator::operator->

Devuelve `&**this`.

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a> recursive_directory_iterator::operator++

Incrementa el `recursive_directory_iterator`.

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parámetros

*int*<br/>
El incremento especificado.

### <a name="remarks"></a>Comentarios

Las llamadas a funciones miembro primera `increment()`, a continuación, devuelve `*this`. La segunda función miembro realiza una copia del objeto, las llamadas `increment()`, a continuación, devuelve la copia.

## <a name="options"></a> recursive_directory_iterator::options

Devuelve `myoptions`.

```cpp
directory_options options() const;
```

## <a name="pop"></a> recursive_directory_iterator::pop

Devuelve el siguiente objeto.

```cpp
void pop();
```

### <a name="remarks"></a>Comentarios

Si `depth() == 0` el objeto se convierte en un iterador de final de secuencia. De lo contrario, la función miembro termina el análisis del directorio actual (más profundo) y lo reanuda en el siguiente nivel inferior.

## <a name="recursion_pending"></a> recursive_directory_iterator::recursion_pending

Devuelve `!no_push`.

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iterator"></a> recursive_directory_iterator::recursive_directory_iterator

Construye un objeto `recursive_directory_iterator`.

```cpp
recursive_directory_iterator() noexcept;
explicit recursive_directory_iterator(const path& pval);

recursive_directory_iterator(const path& pval,
    error_code& ec) noexcept;
recursive_directory_iterator(const path& pval,
    directory_options opts);

recursive_directory_iterator(const path& pval,
    directory_options opts,
    error_code& ec) noexcept;
recursive_directory_iterator(const recursive_directory_iterator&) = default;
recursive_directory_iterator(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parámetros

*pval*<br/>
La ruta de acceso especificada.

*error_code*<br/>
El código de error especificado.

*opts*<br/>
Las opciones de directorio especificado.

*recursive_directory_iterator*<br/>
`recursive_directory_iterator` del que el `recursive_directory_iterator` construido va a ser una copia.

### <a name="remarks"></a>Comentarios

El primer constructor crea un iterador de final de secuencia. El almacén de constructores segundo y tercero **false** en `no_push` y `directory_options::none` en `myoptions`, a continuación, intentan abrir y leer *pval* como un directorio. Si es correcto, inicializan `mystack` y `myentry` para designar el primer nombre de archivo de Active Directory no en la secuencia anidada; de lo contrario producen un iterador de final de secuencia.

Los constructores cuarto y quinto comportan igual que el segundo y tercero, salvo que almacenan primero *opts* en `myoptions`. Los constructores predeterminados se comportan según lo previsto.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md)<br/>
