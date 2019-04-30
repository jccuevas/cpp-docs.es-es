---
title: directory_iterator (Clase)
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::directory_iterator
- filesystem/std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::increment
- filesystem/std::experimental::filesystem::directory_iterator::operator=
- filesystem/std::experimental::filesystem::directory_iterator::operator==
- filesystem/std::experimental::filesystem::directory_iterator::operator!=
- filesystem/std::experimental::filesystem::directory_iterator::operator*
- filesystem/std::experimental::filesystem::directory_iterator::operator-&gt;
- filesystem/std::experimental::filesystem::directory_iterator::operator++
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
helpviewer_keywords:
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::directory_iterator::directory_iterator
- std::experimental::filesystem::directory_iterator::increment
- std::experimental::filesystem::directory_iterator::operator=
- std::experimental::filesystem::directory_iterator::operator==
- std::experimental::filesystem::directory_iterator::operator!=
- std::experimental::filesystem::directory_iterator::operator*
- std::experimental::filesystem::directory_iterator::operator-&gt;
- std::experimental::filesystem::directory_iterator::operator++
ms.openlocfilehash: 6763f2a96b771fadbec311cf8740352fff53e29a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413851"
---
# <a name="directoryiterator-class"></a>directory_iterator (Clase)

Describe un iterador de entrada que establece secuencias en los nombres de archivo en un directorio. Para un iterador `X`, la expresión `*X` se evalúa como un objeto de clase `directory_entry` que contiene el nombre de archivo y cualquier elemento conocido sobre su estado.

La clase almacena un objeto de tipo `path`, llamado `mydir` aquí para efectos de la exposición, que representa el nombre del directorio secuenciar, y un objeto de tipo `directory_entry` llamado `myentry` aquí, que representa el actual nombre de archivo en la secuencia del directorio. Un objeto construido de forma predeterminada del tipo `directory_entry` tiene un valor vacío `mydir` pathname y representa el iterador de final de secuencia.

Por ejemplo, dado el directorio `abc` con entradas `def` y `ghi`, el código:

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

llamará a `visit` con los argumentos `path("abc/def")` y `path("abc/ghi")`.

Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Sintaxis

```cpp
class directory_iterator;
```

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[directory_iterator](#directory_iterator)|Construye un iterador de entrada que secuencia a través de los nombres de archivo en un directorio.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[increment](#increment)|Intenta avanzar al siguiente nombre de archivo en el directorio.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator!=](#op_neq)|Devuelve `!(*this == right)`.|
|[operator=](#op_as)|Los operadores predeterminados de asignación de miembros se comportan según lo previsto.|
|[operator==](#op_eq)|Devuelve **true** sólo si ambos `*this` y *derecho* son iteradores de final de secuencia o ambos son no final-de-secuencia de los iteradores.|
|[operator*](#op_star)|Devuelve `myentry`.|
|[operator->](#op_cast)|Devuelve `&**this`.|
|[operator++](#op_increment)|Llamadas `increment()`, a continuación, devuelve `*this`, o realiza una copia del objeto, las llamadas `increment()`, a continuación, devuelve la copia.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<experimental/filesystem>

**Espacio de nombres:** std::experimental::filesystem

## <a name="directory_iterator"></a> directory_iterator::directory_iterator

El primer constructor crea un iterador de final de secuencia. El almacén de constructores segundo y tercero *pval* en `mydir`, a continuación, intentan abrir y leer `mydir` como un directorio. Si es correcto, almacenan el primer nombre de archivo en el directorio en `myentry`; de lo contrario producen un iterador de final de secuencia.

Los constructores predeterminados se comportan según lo previsto.

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parámetros

*pval*<br/>
La ruta de acceso del nombre de archivo almacenado.

*ec*<br/>
El código de error de estado.

*directory_iterator*<br/>
El objeto almacenado.

## <a name="increment"></a> directory_iterator::increment

La función intenta avanzar al siguiente nombre de archivo del directorio. Si es correcta, almacena ese nombre de archivo en `myentry`; en caso contrario, genera un iterador de final de secuencia.

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="op_neq"></a> directory_iterator::operator!=

El operador miembro devuelve `!(*this == right)`.

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El [directory_iterator](../standard-library/directory-iterator-class.md) que se compara con el `directory_iterator`.

## <a name="op_as"></a> directory_iterator::operator=

Los operadores predeterminados de asignación de miembros se comportan según lo previsto.

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El [directory_iterator](../standard-library/directory-iterator-class.md) que se copia en el `directory_iterator`.

## <a name="op_eq"></a> directory_iterator::operator==

El operador miembro devuelve **true** sólo si ambos `*this` y *derecho* son iteradores de final de secuencia o ambos son no final-de-secuencia de los iteradores.

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El [directory_iterator](../standard-library/directory-iterator-class.md) que se compara con el `directory_iterator`.

## <a name="op_star"></a> directory_iterator::operator*

El operador miembro devuelve `myentry`.

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a> directory_iterator::operator->

La función miembro devuelve `&**this`.

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a> directory_iterator::operator++

Las llamadas a funciones miembro primera `increment()`, a continuación, devuelve `*this`. La segunda función miembro realiza una copia del objeto, las llamadas `increment()`, a continuación, devuelve la copia.

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parámetros

*int*<br/>
El número de incrementos.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md)<br/>
