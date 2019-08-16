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
ms.openlocfilehash: 8c6dcce3de32c7e25d2489cb508454dff500a1a6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454427"
---
# <a name="directoryiterator-class"></a>directory_iterator (Clase)

Describe un iterador de entrada que establece secuencias en los nombres de archivo en un directorio. En el caso `X`de un iterador, la expresión `*X` se evalúa como `directory_entry` un objeto de clase que contiene el nombre de archivo y cualquier elemento conocido sobre su estado.

La clase almacena un objeto de tipo `path`, al `mydir` que se llama aquí para la exposición, que representa el nombre del directorio que se va a secuenciar y un objeto de tipo `directory_entry` llamado `myentry` aquí, que representa el actual. nombre de archivo en la secuencia del directorio. Un objeto construido predeterminado de tipo `directory_entry` tiene un nombreruta `mydir` vacío y representa el iterador de final de secuencia.

Por ejemplo, dado el directorio `abc` con las `def` entradas `ghi`y, el código:

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

llamará `visit` a con los `path("abc/def")` argumentos `path("abc/ghi")`y.

Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Sintaxis

```cpp
class directory_iterator;
```

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[directory_iterator](#directory_iterator)|Construye un iterador de entrada que secuencia a través de los nombres de archivo en un directorio.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[increment](#increment)|Intenta avanzar al siguiente nombre de archivo del directorio.|

### <a name="operators"></a>Operadores

|Operador|DESCRIPCIÓN|
|-|-|
|[operator!=](#op_neq)|Devuelve `!(*this == right)`.|
|[operator=](#op_as)|Los operadores predeterminados de asignación de miembros se comportan según lo previsto.|
|[operator==](#op_eq)|Devuelve **true** solo si `*this` y *right* son iteradores de final de secuencia o si ambos no son iteradores de final de secuencia.|
|[operator*](#op_star)|Devuelve `myentry`.|
|[operator->](#op_cast)|Devuelve `&**this`.|
|[operator++](#op_increment)|Llama `increment()`a, devuelve `*this`o realiza una copia del objeto, llama `increment()`a y, a continuación, devuelve la copia.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<experimental/filesystem>

**Espacio de nombres:** std::experimental::filesystem

## <a name="directory_iterator"></a>directory_iterator::d irectory_iterator

El primer constructor crea un iterador de final de secuencia. Los constructores segundo y tercero almacenan *pval* en `mydir`y, a continuación, intentan abrir y leer `mydir` como un directorio. Si es correcto, almacenan el primer nombre de archivo en `myentry`el directorio en; de lo contrario, generan un iterador de final de secuencia.

Los constructores predeterminados se comportan según lo previsto.

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parámetros

*pval*\
Ruta de acceso del nombre de archivo almacenado.

*n°*\
Código de error de estado.

*directory_iterator*\
Objeto almacenado.

## <a name="increment"></a>directory_iterator:: Increment

La función intenta avanzar al siguiente nombre de archivo del directorio. Si es correcto, almacena ese nombre de `myentry`archivo en; de lo contrario, genera un iterador de final de secuencia.

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="op_neq"></a> directory_iterator::operator!=

El operador miembro devuelve `!(*this == right)`.

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parámetros

*correcta*\
[Directory_iterator](../standard-library/directory-iterator-class.md) que se va a comparar `directory_iterator`con.

## <a name="op_as"></a> directory_iterator::operator=

Los operadores predeterminados de asignación de miembros se comportan según lo previsto.

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>Parámetros

*correcta*\
[Directory_iterator](../standard-library/directory-iterator-class.md) que se va a copiar `directory_iterator`en.

## <a name="op_eq"></a> directory_iterator::operator==

El operador miembro devuelve **true** solo si tanto `*this` como *el derecho* son iteradores de final de secuencia o si ambos no son iteradores de final de secuencia.

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>Parámetros

*correcta*\
[Directory_iterator](../standard-library/directory-iterator-class.md) que se va a comparar `directory_iterator`con.

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

## <a name="op_increment"></a>directory_iterator:: Operator + +

La primera función miembro llama `increment()`a y después `*this`devuelve. La segunda función miembro realiza una copia del objeto, llama `increment()`a y, a continuación, devuelve la copia.

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>Parámetros

*Inter*\
Número de incrementos.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md)
