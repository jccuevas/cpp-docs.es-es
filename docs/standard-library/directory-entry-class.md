---
title: Clase directory_entry
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- filesystem/std::experimental::filesystem::directory_entry::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator=
- filesystem/std::experimental::filesystem::directory_entry::assign
- filesystem/std::experimental::filesystem::directory_entry::replace_filename
- filesystem/std::experimental::filesystem::directory_entry::path
- filesystem/std::experimental::filesystem::directory_entry::status
- filesystem/std::experimental::filesystem::directory_entry::symlink_status
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;
- filesystem/std::experimental::filesystem::directory_entry::operator==
- filesystem/std::experimental::filesystem::directory_entry::operator!=
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;=
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;=
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
helpviewer_keywords:
- std::experimental::filesystem::directory_entry
- std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- std::experimental::filesystem::directory_entry::directory_entry
- std::experimental::filesystem::directory_entry::operator=
- std::experimental::filesystem::directory_entry::assign
- std::experimental::filesystem::directory_entry::replace_filename
- std::experimental::filesystem::directory_entry::path
- std::experimental::filesystem::directory_entry::status
- std::experimental::filesystem::directory_entry::symlink_status
- std::experimental::filesystem::directory_entry::operator&lt;
- std::experimental::filesystem::directory_entry::operator==
- std::experimental::filesystem::directory_entry::operator!=
- std::experimental::filesystem::directory_entry::operator&lt;=
- std::experimental::filesystem::directory_entry::operator&gt;
- std::experimental::filesystem::directory_entry::operator&gt;=
ms.openlocfilehash: 35b0dc55bf5db2f799d9ade28cd5968ceab3332b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458960"
---
# <a name="directoryentry-class"></a>Clase directory_entry

Describe un objeto devuelto por `*X`, donde *X* es un [directory_iterator](../standard-library/directory-iterator-class.md) o un [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
class directory_entry;
```

## <a name="remarks"></a>Comentarios

La clase almacena un objeto de tipo [path](../standard-library/path-class.md). La `path` almacenada puede ser una instancia de la [path (Clase)](../standard-library/path-class.md) o de un tipo que se deriva de `path`. También almacena dos valores [file_type](../standard-library/filesystem-enumerations.md#file_type): uno que representa lo que se conoce sobre el estado del nombre de archivo almacenado y otra que representa lo que se conoce sobre el estado del vínculo simbólico del nombre de archivo.

Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md).

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[directory_entry](#directory_entry)|Los constructores predeterminados se comportan según lo previsto. El cuarto `mypath` constructor se inicializa como *pval*, `mystat` en *stat_arg*y `mysymstat` en *symstat_arg*.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[assign](#assign)|La función miembro asigna *pval* a `mypath`, *STAT* a `mystat`y symstat a.  `mysymstat`|
|[path](#path)|La función miembro devuelve `mypath`.|
|[replace_filename](#replace_filename)|La función miembro reemplaza `mypath` por `mypath.parent_path()`  /  *pval* ,`mystat` con *stat_arg* y`mysymstat` con *symstat_arg*|
|[status](#status)|Ambas funciones miembro devuelven `mystat` la primera modificación.|
|[symlink_status](#symlink_status)|Ambas funciones miembro devuelven `mysymstat` la primera modificación.|

### <a name="operators"></a>Operadores

|Operador|DESCRIPCIÓN|
|-|-|
|[operator!=](#op_neq)|Reemplaza los elementos de la lista por una copia de otra lista.|
|[operator=](#op_as)|Los operadores predeterminados de asignación de miembros se comportan según lo previsto.|
|[operator==](#op_eq)|Devuelve `mypath == right.mypath`.|
|[operator<](#op_lt)|Devuelve `mypath < right.mypath`.|
|[operator<=](#op_lteq)|Devuelve `!(right < *this)`.|
|[operator>](#op_gt)|Devuelve `right < *this`.|
|[operator>=](#op_gteq)|Devuelve `!(*this < right)`.|
|[Operator const path_type &](#path_type)|Devuelve `mypath`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<experimental/sistema de archivos&gt;

**Espacio de nombres:** std::experimental::filesystem

## <a name="assign"></a>quitar

La función miembro asigna *pval* a `mypath`, *stat_arg* a `mystat`y symstat_arg a.  `mysymstat`

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parámetros

*pval*\
Ruta de acceso del nombre de archivo almacenado.

*stat_arg*\
Estado del nombre de archivo almacenado.

*symstat_arg*\
Estado de vínculo simbólico del nombre de archivo almacenado.

## <a name="directory_entry"></a>directory_entry

Los constructores predeterminados se comportan según lo previsto. El cuarto `mypath` constructor se inicializa como *pval*, `mystat` en *stat_arg*y `mysymstat` en *symstat_arg*.

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parámetros

*pval*\
Ruta de acceso del nombre de archivo almacenado.

*stat_arg*\
Estado del nombre de archivo almacenado.

*symstat_arg*\
Estado de vínculo simbólico del nombre de archivo almacenado.

## <a name="op_neq"></a>operador! =

La función miembro devuelve `!(*this == right)`.

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parámetros

*correcta*\
[Directory_entry](../standard-library/directory-entry-class.md) que se va a comparar `directory_entry`con.

## <a name="op_as"></a> operator=

Los operadores predeterminados de asignación de miembros se comportan según lo previsto.

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

### <a name="parameters"></a>Parámetros

*correcta*\
[Directory_entry](../standard-library/directory-entry-class.md) que se va a copiar `directory_entry`en.

## <a name="op_eq"></a>operador = =

La función miembro devuelve `mypath == right.mypath`.

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parámetros

*correcta*\
[Directory_entry](../standard-library/directory-entry-class.md) que se va a comparar `directory_entry`con.

## <a name="op_lt"></a> operator&lt;

La función miembro devuelve `mypath < right.mypath`.

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parámetros

*correcta*\
[Directory_entry](../standard-library/directory-entry-class.md) que se va a comparar `directory_entry`con.

## <a name="op_lteq"></a>Operator&lt;=

La función miembro devuelve `!(right < *this)`.

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parámetros

*correcta*\
[Directory_entry](../standard-library/directory-entry-class.md) que se va a comparar `directory_entry`con.

## <a name="op_gt"></a> operator&gt;

La función miembro devuelve `right < *this`.

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parámetros

*correcta*\
[Directory_entry](../standard-library/directory-entry-class.md) que se va a comparar `directory_entry`con.

## <a name="op_gteq"></a>Operator&gt;=

La función miembro devuelve `!(*this < right)`.

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parámetros

*correcta*\
[Directory_entry](../standard-library/directory-entry-class.md) que se va a comparar `directory_entry`con.

## <a name="path_type"></a>Operator const path_type &

El operador miembro devuelve `mypath`.

```cpp
operator const std::experimental::filesystem::path&() const;
```

## <a name="path"></a>camino

La función miembro devuelve `mypath`.

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

## <a name="replace_filename"></a>replace_filename

La función miembro reemplaza `mypath` por `mypath.parent_path()`  /  *pval* ,`mystat` con *stat_arg* y`mysymstat` con *symstat_arg*

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parámetros

*pval*\
Ruta de acceso del nombre de archivo almacenado.

*stat_arg*\
Estado del nombre de archivo almacenado.

*symstat_arg*\
Estado de vínculo simbólico del nombre de archivo almacenado.

## <a name="status"></a>estatus

Ambas funciones miembro devuelven `mystat` posiblemente la primera modificación de la siguiente manera:

1. Si `status_known(mystat)` después no hace nada.

1. De lo contrario `!status_known(mysymstat) && !is_symlink(mysymstat)` , `mystat = mysymstat`si es.

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Parámetros

*n°*\
Código de error de estado.

## <a name="symlink_status"></a> symlink_status

Ambas funciones miembro devuelven `mysymstat` posiblemente la primera modificación de la siguiente manera: Si `status_known(mysymstat)` después no hace nada. En caso contrario, es `mysymstat = symlink_status(mypval)`.

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Parámetros

*n°*\
Código de error de estado.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem&gt;](../standard-library/filesystem.md)
