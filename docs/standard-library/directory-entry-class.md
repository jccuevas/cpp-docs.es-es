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
ms.openlocfilehash: c1b68aefd44d8f0ac60c36307dee93333d801bb9
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342983"
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

|Constructor|Descripción|
|-|-|
|[directory_entry](#directory_entry)|Los constructores predeterminados se comportan según lo previsto. El cuarto constructor inicializa `mypath` a *pval*, `mystat` a *stat_arg*, y `mysymstat` a *symstat_arg*.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[assign](#assign)|La función miembro asigna *pval* a `mypath`, *stat* a `mystat`, y *symstat* a `mysymstat`.|
|[path](#path)|La función miembro devuelve `mypath`.|
|[replace_filename](#replace_filename)|La función miembro reemplaza `mypath` con `mypath.parent_path()`  /  *pval*, `mystat` con *stat_arg*, y `mysymstat` con *symstat_arg*|
|[status](#status)|Ambas funciones miembro devuelven `mystat` posiblemente primero se modifica.|
|[symlink_status](#symlink_status)|Ambas funciones miembro devuelven `mysymstat` posiblemente primero se modifica.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator!=](#op_neq)|Reemplaza los elementos de la lista por una copia de otra lista.|
|[operator=](#op_as)|Los operadores predeterminados de asignación de miembros se comportan según lo previsto.|
|[operator==](#op_eq)|Devuelve `mypath == right.mypath`.|
|[operator<](#op_lt)|Devuelve `mypath < right.mypath`.|
|[operator<=](#op_lteq)|Devuelve `!(right < *this)`.|
|[operator>](#op_gt)|Devuelve `right < *this`.|
|[operator>=](#op_gteq)|Devuelve `!(*this < right)`.|
|[operator const path_type&](#path_type)|Devuelve `mypath`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<experimental/filesystem&gt;

**Espacio de nombres:** std::experimental::filesystem

## <a name="assign"></a> Asignar

La función miembro asigna *pval* a `mypath`, *stat_arg* a `mystat`, y *symstat_arg* a `mysymstat`.

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parámetros

*pval*<br/>
La ruta de acceso del nombre de archivo almacenado.

*stat_arg*<br/>
El estado del nombre de archivo almacenado.

*symstat_arg*<br/>
El estado del vínculo simbólico del nombre de archivo almacenado.

## <a name="directory_entry"></a> directory_entry

Los constructores predeterminados se comportan según lo previsto. El cuarto constructor inicializa `mypath` a *pval*, `mystat` a *stat_arg*, y `mysymstat` a *symstat_arg*.

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parámetros

*pval*<br/>
La ruta de acceso del nombre de archivo almacenado.

*stat_arg*<br/>
El estado del nombre de archivo almacenado.

*symstat_arg*<br/>
El estado del vínculo simbólico del nombre de archivo almacenado.

## <a name="op_neq"></a> operator!=

La función miembro devuelve `!(*this == right)`.

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El [directory_entry](../standard-library/directory-entry-class.md) que se compara con el `directory_entry`.

## <a name="op_as"></a> operator=

Los operadores predeterminados de asignación de miembros se comportan según lo previsto.

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El [directory_entry](../standard-library/directory-entry-class.md) que se copia en el `directory_entry`.

## <a name="op_eq"></a> operador ==

La función miembro devuelve `mypath == right.mypath`.

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El [directory_entry](../standard-library/directory-entry-class.md) que se compara con el `directory_entry`.

## <a name="op_lt"></a> operator&lt;

La función miembro devuelve `mypath < right.mypath`.

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El [directory_entry](../standard-library/directory-entry-class.md) que se compara con el `directory_entry`.

## <a name="op_lteq"></a> Operador&lt;=

La función miembro devuelve `!(right < *this)`.

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El [directory_entry](../standard-library/directory-entry-class.md) que se compara con el `directory_entry`.

## <a name="op_gt"></a> operator&gt;

La función miembro devuelve `right < *this`.

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El [directory_entry](../standard-library/directory-entry-class.md) que se compara con el `directory_entry`.

## <a name="op_gteq"></a> Operador&gt;=

La función miembro devuelve `!(*this < right)`.

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El [directory_entry](../standard-library/directory-entry-class.md) que se compara con el `directory_entry`.

## <a name="path_type"></a> operator const path_type &

El operador miembro devuelve `mypath`.

```cpp
operator const std::experimental::filesystem::path&() const;
```

## <a name="path"></a> Ruta de acceso

La función miembro devuelve `mypath`.

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

## <a name="replace_filename"></a> replace_filename

La función miembro reemplaza `mypath` con `mypath.parent_path()`  /  *pval*, `mystat` con *stat_arg*, y `mysymstat` con *symstat_arg*

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parámetros

*pval*<br/>
La ruta de acceso del nombre de archivo almacenado.

*stat_arg*<br/>
El estado del nombre de archivo almacenado.

*symstat_arg*<br/>
El estado del vínculo simbólico del nombre de archivo almacenado.

## <a name="status"></a> Estado

Ambas funciones miembro devuelven `mystat` posiblemente primero se modifica como sigue:

1. Si `status_known(mystat)` , a continuación, no hacer nada.

1. De lo contrario, si `!status_known(mysymstat) && !is_symlink(mysymstat)` , a continuación, `mystat = mysymstat`.

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Parámetros

*ec*<br/>
El código de error de estado.

## <a name="symlink_status"></a> symlink_status

Ambas funciones miembro devuelven `mysymstat` posiblemente primero se modifica como sigue: Si `status_known(mysymstat)` , a continuación, no hacer nada. En caso contrario, es `mysymstat = symlink_status(mypval)`.

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Parámetros

*ec*<br/>
El código de error de estado.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem&gt;](../standard-library/filesystem.md)<br/>
