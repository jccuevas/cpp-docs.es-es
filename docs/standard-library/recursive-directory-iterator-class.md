---
title: recursive_directory_iterator (Clase)
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: 98eaf2494a3bc17c0f9d11683fc67fed433ba3a5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451705"
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator (Clase)

Describe un iterador de entrada que secuencia a través de los nombres de archivo en un directorio, posiblemente descendente en subdirectorios de forma recursiva. En el caso `X`de un iterador, la expresión `*X` se evalúa como `directory_entry` un objeto de clase que contiene el nombre de archivo y cualquier elemento conocido sobre su estado.

Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Sintaxis

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Comentarios

La clase de plantilla almacena:

1. objeto de tipo `stack<pair<directory_iterator, path>>`, al que `mystack` se llama aquí para la exposición, que representa el anidamiento de directorios que se va a secuenciar.

1. un objeto de tipo `directory_entry` llamado `myentry` aquí, que representa el nombre de archivo actual en la secuencia del directorio.

1. un objeto de tipo **bool**, llamado `no_push` aquí, que registra si el descenso recursivo en subdirectorios está deshabilitado

1. objeto de tipo `directory_options`, al que `myoptions` se llama aquí, que registra las opciones establecidas en la construcción.

Un objeto construido predeterminado de tipo `recursive_directory_entry` tiene un iterador de final de secuencia en `mystack.top().first` y representa el iterador de final de secuencia. Por ejemplo, dado el directorio `abc` con las `def` entradas (un directorio) `def/ghi`, y `jkl`, el código:

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

llamará a Visit con los `path("abc/def/ghi")` argumentos `path("abc/jkl")`y. Puede calificar la secuenciación a través de un subárbol de directorio de dos maneras:

1. Un symlink de directorio se examinará solo si se construye un `recursive_directory_iterator` con un `directory_options` argumento cuyo valor es `directory_options::follow_directory_symlink`.

1. Si llama `disable_recursion_pending` a, no se examinará de forma recursiva un directorio posterior que se encuentre durante un incremento.

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|Construye un objeto `recursive_directory_iterator`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[depth](#depth)|Devuelve `mystack.size() - 1`, de `pval` modo que está en la profundidad cero.|
|[disable_recursion_pending](#disable_recursion_pending)|Almacena **true** en `no_push`.|
|[increment](#increment)|Avanza al siguiente nombre de archivo en secuencia.|
|[options](#options)|Devuelve `myoptions`.|
|[pop](#pop)|Devuelve el objeto siguiente.|
|[recursion_pending](#recursion_pending)|Devuelve `!no_push`.|

### <a name="operators"></a>Operadores

|Operador|DESCRIPCIÓN|
|-|-|
|[operator!=](#op_neq)|Devuelve `!(*this == right)`.|
|[operator=](#op_as)|Los operadores predeterminados de asignación de miembros se comportan según lo previsto.|
|[operator==](#op_eq)|Devuelve **true** solo si `*this` y *right* son iteradores de final de secuencia o si ambos no son iteradores de final de secuencia.|
|[operator*](#op_multiply)|Devuelve `myentry`.|
|[operator->](#op_cast)|Devuelve `&**this`.|
|[operator++](#op_increment)|Incrementa el `recursive_directory_iterator`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> filesystem

**Espacio de nombres:** std::tr2::sys

## <a name="depth"></a>recursive_directory_iterator::d epth

Devuelve `mystack.size() - 1`, de `pval` modo que está en la profundidad cero.

```cpp
int depth() const;
```

## <a name="disable_recursion_pending"></a> recursive_directory_iterator::disable_recursion_pending

Almacena **true** en `no_push`.

```cpp
void disable_recursion_pending();
```

## <a name="increment"></a>recursive_directory_iterator:: Increment

Avanza al siguiente nombre de archivo en secuencia.

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>Parámetros

*n°*\
Código de error especificado.

### <a name="remarks"></a>Comentarios

La función intenta avanzar al siguiente nombre de archivo de la secuencia anidada. Si es correcto, almacena ese nombre de `myentry`archivo en; de lo contrario, genera un iterador de final de secuencia.

## <a name="op_neq"></a> recursive_directory_iterator::operator!=

Devuelve `!(*this == right)`.

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parámetros

*correcta*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) para la comparación.

## <a name="op_as"></a> recursive_directory_iterator::operator=

Los operadores predeterminados de asignación de miembros se comportan según lo previsto.

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parámetros

*recursive_directory_iterator*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) que se va a copiar `recursive_directory_iterator`en.

## <a name="op_eq"></a> recursive_directory_iterator::operator==

Devuelve **true** solo si `*this` y *right* son iteradores de final de secuencia o si ambos no son iteradores de final de secuencia.

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>Parámetros

*correcta*\
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) para la comparación.

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

## <a name="op_increment"></a>recursive_directory_iterator:: Operator + +

Incrementa el `recursive_directory_iterator`.

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parámetros

*Inter*\
El incremento especificado.

### <a name="remarks"></a>Comentarios

La primera función miembro llama `increment()`a y después `*this`devuelve. La segunda función miembro realiza una copia del objeto, llama `increment()`a y, a continuación, devuelve la copia.

## <a name="options"></a>recursive_directory_iterator:: Options

Devuelve `myoptions`.

```cpp
directory_options options() const;
```

## <a name="pop"></a>recursive_directory_iterator::p op

Devuelve el objeto siguiente.

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

*pval*\
La ruta de acceso especificada.

*error_code*\
Código de error especificado.

*aporta*\
Opciones de directorio especificadas.

*recursive_directory_iterator*\
`recursive_directory_iterator` del que el `recursive_directory_iterator` construido va a ser una copia.

### <a name="remarks"></a>Comentarios

El primer constructor crea un iterador de final de secuencia. Los constructores segundo y tercero almacenan **false** en `directory_options::none` `no_push` y `myoptions`en, y luego intentan abrir y leer *pval* como un directorio. Si es correcto, `mystack` inicializan `myentry` y para designar el primer nombre de archivo que no es de directorio en la secuencia anidada; de lo contrario, generan un iterador de final de secuencia.

Los constructores cuarto y quinto se comportan igual que el segundo y el tercero, salvo que los *primeros almacenan* en `myoptions`. Los constructores predeterminados se comportan según lo previsto.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md)
