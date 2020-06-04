---
title: '&lt;filesystem&gt; (Funciones)'
ms.date: 03/27/2019
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::absolute
- FILESYSTEM/std::experimental::filesystem::canonical
- FILESYSTEM/std::experimental::filesystem::copy
- FILESYSTEM/std::experimental::filesystem::copy_file
- FILESYSTEM/std::experimental::filesystem::copy_symlink
- FILESYSTEM/std::experimental::filesystem::create_directories
- FILESYSTEM/std::experimental::filesystem::create_directory
- FILESYSTEM/std::experimental::filesystem::create_directory_symlink
- FILESYSTEM/std::experimental::filesystem::create_hard_link
- FILESYSTEM/std::experimental::filesystem::create_symlink
- FILESYSTEM/std::experimental::filesystem::current_path
- FILESYSTEM/std::experimental::filesystem::equivalent
- FILESYSTEM/std::experimental::filesystem::exists
- FILESYSTEM/std::experimental::filesystem::file_size
- FILESYSTEM/std::experimental::filesystem::hard_link_count
- FILESYSTEM/std::experimental::filesystem::hash_value
- FILESYSTEM/std::experimental::filesystem::is_block_file
- FILESYSTEM/std::experimental::filesystem::is_character_file
- FILESYSTEM/std::experimental::filesystem::is_directory
- FILESYSTEM/std::experimental::filesystem::is_empty
- FILESYSTEM/std::experimental::filesystem::is_fifo
- FILESYSTEM/std::experimental::filesystem::is_other
- FILESYSTEM/std::experimental::filesystem::is_regular_file
- FILESYSTEM/std::experimental::filesystem::is_socket
- FILESYSTEM/std::experimental::filesystem::is_symlink
- FILESYSTEM/std::experimental::filesystem::last_write_time
- FILESYSTEM/std::experimental::filesystem::permissions
- FILESYSTEM/std::experimental::filesystem::read_symlink
- FILESYSTEM/std::experimental::filesystem::remove
- FILESYSTEM/std::experimental::filesystem::remove_all
- FILESYSTEM/std::experimental::filesystem::rename
- FILESYSTEM/std::experimental::filesystem::resize_file
- FILESYSTEM/std::experimental::filesystem::space
- FILESYSTEM/std::experimental::filesystem::status
- FILESYSTEM/std::experimental::filesystem::status_known
- FILESYSTEM/std::experimental::filesystem::swap
- FILESYSTEM/std::experimental::filesystem::symlink_status
- FILESYSTEM/std::experimental::filesystem::system_complete
- FILESYSTEM/std::experimental::filesystem::temp_directory_path
- FILESYSTEM/std::experimental::filesystem::u8path
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
helpviewer_keywords:
- std::experimental::filesystem::absolute
- std::experimental::filesystem::canonical
- std::experimental::filesystem::copy
- std::experimental::filesystem::copy_file
- std::experimental::filesystem::copy_symlink
- std::experimental::filesystem::create_directories
- std::experimental::filesystem::create_directory
- std::experimental::filesystem::create_directory_symlink
- std::experimental::filesystem::create_hard_link
- std::experimental::filesystem::create_symlink
- std::experimental::filesystem::current_path
- std::experimental::filesystem::equivalent
- std::experimental::filesystem::exists
- std::experimental::filesystem::file_size
- std::experimental::filesystem::hard_link_count
- std::experimental::filesystem::hash_value
- std::experimental::filesystem::is_block_file
- std::experimental::filesystem::is_character_file
- std::experimental::filesystem::is_directory
- std::experimental::filesystem::is_empty
- std::experimental::filesystem::is_fifo
- std::experimental::filesystem::is_other
- std::experimental::filesystem::is_regular_file
- std::experimental::filesystem::is_socket
- std::experimental::filesystem::is_symlink
- std::experimental::filesystem::last_write_time
- std::experimental::filesystem::permissions
- std::experimental::filesystem::read_symlink
- std::experimental::filesystem::remove
- std::experimental::filesystem::remove_all
- std::experimental::filesystem::rename
- std::experimental::filesystem::resize_file
- std::experimental::filesystem::space
- std::experimental::filesystem::status
- std::experimental::filesystem::status_known
- std::experimental::filesystem::swap
- std::experimental::filesystem::symlink_status
- std::experimental::filesystem::system_complete
- std::experimental::filesystem::temp_directory_path
- std::experimental::filesystem::u8path
ms.openlocfilehash: 1e5994faab69c1809f820b41186d9b618aa7c193
ms.sourcegitcommit: d2ccbba1bf4e66d6b6b0582dc01ba39f4a54f0aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2020
ms.locfileid: "82984089"
---
# <a name="ltfilesystemgt-functions"></a>&lt;filesystem&gt; (Funciones)

Estas funciones gratuitas en el encabezado del [ \<>del sistema](../standard-library/filesystem.md) de archivos realizan operaciones de modificación y consulta en rutas de acceso, archivos, vínculos simbólicos, directorios y volúmenes. Para obtener más información y ejemplos de código, vea [navegación del sistema de archivos (C++)](../standard-library/file-system-navigation.md).

## <a name="absolute"></a><a name="absolute"></a>mínimo

```cpp
path absolute(const path& pval, const path& base = current_path());
```

La función devuelve el nombreruta absoluto correspondiente a *pval* en relación con el `base`nombreruta:

1. Si `pval.has_root_name() && pval.has_root_directory()` la función devuelve *pval*.

1. Si `pval.has_root_name() && !pval.has_root_directory()` `pval.root_name()`  /  `absolute(base).root_directory()`  / la función devuelve `absolute(base).relative_path()`.  /  `pval.relative_path()`

1. Si `!pval.has_root_name() && pval.has_root_directory()` la función devuelve `absolute(base).root_name()`  /  *pval*.

1. Si `!pval.has_root_name() && !pval.has_root_directory()` la función devuelve `absolute(base)`  /  *pval*.

## <a name="begin"></a><a name="begin"></a>inicia

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

Ambas funciones devuelven *ITER*.

## <a name="canonical"></a><a name="canonical"></a>dar

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

Todas las funciones forman un nombreruta `pabs = absolute(pval, base)` absoluto (o `pabs = absolute(pval)` para la sobrecarga sin ningún parámetro base) y, a continuación, la reducen a una forma canónica en la siguiente secuencia de pasos:

1. Cada componente `X` de ruta de `is_symlink(X)` acceso para el que es `read_symlink(X)` **true** se reemplaza por.

1. Se quitan `.` todos los componentes de ruta de acceso (punto es el directorio actual establecido por los componentes de ruta de acceso anteriores).

1. Cada par de componentes `X` / `..` de ruta de acceso (punto-punto es el directorio principal establecido por los componentes de ruta de acceso anteriores) se quita.

A continuación, la `pabs`función devuelve.

## <a name="copy"></a><a name="copy"></a>copiar

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Todas las funciones posiblemente copian o vinculan uno o varios archivos *de* a *a a* bajo el control de *OPC*, que `copy_options::none` se toma como para las sobrecargas sin el parámetro *OPC* . *OPC* debe contener al menos uno de los siguientes:

- `skip_existing`, `overwrite_existing`o `update_existing`

- `copy_symlinks` o `skip_symlinks`

- `directories_only`, `create_symlinks`o `create_hard_links`

Las funciones determinan en primer `f` lugar los valores `t` de file_status de *from* y *for:*

- Si `opts & (copy_options::create_symlinks | copy_options::skip_symlinks)`, llamando a`symlink_status`

- de lo contrario, mediante una llamada a`status`

- En caso contrario, notifican un error.

Si `!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)`es, notifican un error (y no hacen nada más).

De lo contrario `is_symlink(f)` , si es:

- Si `options & copy_options::skip_symlinks`es, no haga nada.

- En caso contrario `!exists(t)&& options & copy_options::copy_symlinks`, si `copy_symlink(from, to, opts)`es, entonces.

- De lo contrario, notifique un error.

De lo contrario `is_regular_file(f)`, si es, entonces:

- Si `opts & copy_options::directories_only`es, no haga nada.

- En caso contrario `opts & copy_options::create_symlinks`, si `create_symlink(to, from)`es, entonces.

- En caso contrario `opts & copy_options::create_hard_links`, si `create_hard_link(to, from)`es, entonces.

- En caso contrario `is_directory(f)`, si `copy_file(from, to`  /  `from.filename(), opts)`es, entonces.

- En caso contrario, es `copy_file(from, to, opts)`.

De lo contrario `is_directory(f) && (opts & copy_options::recursive || !opts)`, si es, entonces:

```cpp
if (!exists(t))
{  // copy directory contents recursively
    create_directory(to, from, ec);

    for (directory_iterator next(from), end; ec == error_code() && next != end; ++next)
    {
        copy(next->path(), to / next->path().filename(), opts, ec);
    }
}
```

De lo contrario, no hacen nada.

## <a name="copy_file"></a><a name="copy_file"></a>copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Es posible que todas las funciones copien el archivo *de a* *a a* bajo el control de *OPC*, `copy_options::none` que se toma como para las sobrecargas sin ningún parámetro *OPC* . *OPC* debe contener, como máximo, `skip_existing`una `overwrite_existing`de, `update_existing`o.

Si `exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))`es, notifique como un error que el archivo ya existe.

De lo contrario `!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))`, si es, intenta copiar el contenido y los atributos del *from* archivo *del archivo al.* Notifican como un error si se produce un error en el intento de copia.

Las funciones devuelven **true** si la copia se intenta y se realiza correctamente; de lo contrario, es **false**.

## <a name="copy_symlink"></a><a name="copy_symlink"></a>copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

Si `is_directory(from)`es, la función `create_directory_symlink(from, to)`llama a. De lo contrario, `create_symlink(from, to)`llama a.

## <a name="create_directories"></a><a name="create_directories"></a>create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

Para\/un nombreruta como a b\/c, la función crea los directorios a y\/b según sea necesario para que pueda crear el directorio a\/b\/c según sea necesario. Devuelve **true** solo si crea realmente el directorio *pval*.

## <a name="create_directory"></a><a name="create_directory"></a>create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

La función crea el directorio *pval* según sea necesario. Devuelve true solo si crea realmente el directorio *pval*, en cuyo caso copia los permisos del *atributo*File existente o usa `perms::all` para las sobrecargas sin el parámetro *ATTR* .

## <a name="create_directory_symlink"></a><a name="create_directory_symlink"></a>create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

La función crea el vínculo como un vínculo simbólico al directorio *en*.

## <a name="create_hard_link"></a><a name="create_hard_link"></a>create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

La función crea el vínculo como un vínculo físico al directorio o archivo *en*.

## <a name="create_symlink"></a><a name="create_symlink"></a>create_symlink

```cpp
void create_symlink(const path& to, const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

La función crea el vínculo como un *vínculo* simbólico al archivo *en*.

## <a name="current_path"></a><a name="current_path"></a>current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

Las funciones sin el parámetro *pval* devuelven el valor de pathname para el directorio actual. Las funciones restantes establecen el directorio actual en *pval*.

## <a name="end"></a><a name="end"></a>extremo

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

La primera función devuelve `directory_iterator()` y la segunda función devuelve`recursive_directory_iterator()`

## <a name="equivalent"></a><a name="equivalent"></a>Equivalent

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

Las funciones devuelven **true** solo si la *izquierda* y la *derecha* eligen la misma entidad filesystem.

## <a name="exists"></a><a name="exists"></a>existencia

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `status_known && stat.type() != file_not_found`. Las funciones segunda y tercera devuelven `exists(status(pval))`.

## <a name="file_size"></a><a name="file_size"></a>file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

Las funciones devuelven el tamaño en bytes del archivo elegido por *pval*, `exists(pval) && is_regular_file(pval)` si se puede determinar el tamaño del archivo. En caso contrario, notifican un `uintmax_t(-1)`error y devuelven.

## <a name="hard_link_count"></a><a name="hard_link_count"></a>hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

La función devuelve el número de vínculos físicos para *pval*o \-1 si se produce un error.

## <a name="hash_value"></a><a name="hash_value"></a>hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

La función devuelve un valor hash para `pval.native()`.

## <a name="is_block_file"></a><a name="is_block_file"></a>is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::block`. Las funciones restantes devuelven `is_block_file(status(pval))`.

## <a name="is_character_file"></a><a name="is_character_file"></a>is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::character`. Las funciones restantes devuelven `is_character_file(status(pval))`.

## <a name="is_directory"></a><a name="is_directory"></a>is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::directory`. Las funciones restantes devuelven `is_directory_file(status(pval))`.

## <a name="is_empty"></a><a name="is_empty"></a>is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

Si `is_directory(pval)`es, la función devuelve `directory_iterator(pval) == directory_iterator()`; en caso contrario `file_size(pval) == 0`, devuelve.

## <a name="is_fifo"></a><a name="is_fifo"></a>is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::fifo`. Las funciones restantes devuelven `is_fifo(status(pval))`.

## <a name="is_other"></a><a name="is_other"></a>is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::other`. Las funciones restantes devuelven `is_other(status(pval))`.

## <a name="is_regular_file"></a><a name="is_regular_file"></a>is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::regular`. Las funciones restantes devuelven `is_regular_file(status(pval))`.

## <a name="is_socket"></a><a name="is_socket"></a>is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::socket`. Las funciones restantes devuelven `is_socket(status(pval))`.

## <a name="is_symlink"></a><a name="is_symlink"></a>is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::symlink`. Las funciones restantes devuelven `is_symlink(status(pval))`.

## <a name="last_write_time"></a><a name="last_write_time"></a>last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

Las dos primeras funciones devuelven la hora de la última *pval*modificación de datos `file_time_type(-1)` para pval, o si se produce un error. Las dos últimas funciones establecen la hora de la última modificación de datos de *pval* en *new_time*.

## <a name="permissions"></a><a name="permissions"></a>los

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

Las funciones establecen los permisos para el nombreruta elegido por *pval* en `mask & perms::mask` el control de `perms & (perms::add_perms | perms::remove_perms)`. *Mask* debe contener como máximo una de `perms::add_perms` y `perms::remove_perms`.

Si `mask & perms::add_perms`es, las funciones establecen los permisos `status(pval).permissions() | mask & perms::mask`en. De lo contrario `mask & perms::remove_perms`, si es, las funciones establecen `status(pval).permissions() & ~(mask & perms::mask)`los permisos en. De lo contrario, las funciones establecen los `mask & perms::mask`permisos en.

## <a name="proximate"></a><a name="proximate"></a>cercano

```cpp
path proximate(const path& p, error_code& ec);
path proximate(const path& p, const path& base = current_path());
path proximate(const path& p, const path& base, error_code& ec);
```

## <a name="read_symlink"></a><a name="read_symlink"></a>read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

Las funciones notifican un error y `path()` devuelven si `!is_symlink(pval)`. De lo contrario, las funciones devuelven un objeto de tipo `path` que tiene el vínculo simbólico.

## <a name="relative"></a><a name="relative"></a>relativa

```cpp
path relative(const path& p, error_code& ec);
path relative(const path& p, const path& base = current_path());
path relative(const path& p, const path& base, error_code& ec);
```

## <a name="remove"></a><a name="remove"></a>retirar

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

Las funciones devuelven **true** solo si `exists(symlink_status(pval))` y el archivo se quita correctamente. Se quita un vínculo simbólico, no el archivo que elija.

## <a name="remove_all"></a><a name="remove_all"></a>remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

Si *pval* es un directorio, las funciones quitan todas las entradas de directorio de forma recursiva y, a continuación, la propia entrada. De lo contrario, las `remove`funciones llaman a. Devuelven un recuento de todos los elementos que se quitaron correctamente.

## <a name="rename"></a><a name="rename"></a>cambiar el nombre

```cpp
void rename(const path& from, const path& to);
void rename(const path& from, const path& to, error_code& ec) noexcept;
```

Las funciones cambiaron el nombre *de* *a.* Se cambia el nombre de un vínculo simbólico, no del archivo que elija.

## <a name="resize_file"></a><a name="resize_file"></a>resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

Las funciones modifican el tamaño de un archivo de modo que`file_size(pval) == size`

## <a name="space"></a><a name="space"></a>Espacia

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

La función devuelve información sobre el volumen elegido por *pval*, en una estructura de tipo `space_info`. La estructura contiene `uintmax_t(-1)` cualquier valor que no se puede determinar.

## <a name="status"></a><a name="status"></a>estatus

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

Las funciones devuelven el estado de la ruta de acceso, el tipo de archivo y los permisos asociados a *pval*. No se prueba un vínculo simbólico, sino el archivo que elige.

## <a name="status_known"></a><a name="status_known"></a>status_known

```cpp
bool status_known(file_status stat) noexcept;
```

La función devuelve`stat.type() != file_type::none`

## <a name="swap"></a><a name="swap"></a>pasar

```cpp
void swap(path& left, path& right) noexcept;
```

La función intercambia el contenido de *izquierda* y *derecha*.

## <a name="symlink_status"></a><a name="symlink_status"></a>symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, error_code& ec) noexcept;
```

Las funciones devuelven el estado de symlink del directorio, el tipo de archivo y los permisos asociados a *pval*. Las funciones se comportan `status(pval)` igual que, salvo que se prueba un vínculo simbólico, no el archivo que elija.

## <a name="system_complete"></a><a name="system_complete"></a>system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

Las funciones devuelven un nombre de ruta de acceso absoluta que tiene en cuenta, según sea necesario, el directorio actual asociado a su nombre de raíz. \(Para POSIX, las funciones devuelven `absolute(pval)`.\)

## <a name="temp_directory_path"></a><a name="temp_directory_path"></a>temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

Las funciones devuelven un nombre de ruta de acceso de un directorio adecuado para contener los archivos temporales.

## <a name="u8path"></a><a name="u8path"></a>u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

La primera función se comporta igual que `path(source)` y la segunda función se comporta igual que `path(first, last)` , salvo que el origen elegido en cada caso se toma como una secuencia de elementos char codificados como UTF-8, independientemente del sistema de archivos.

## <a name="weakly_canonical"></a><a name="weakly_canonical"></a>weakly_canonical

```cpp
path weakly_canonical(const path& p);
path weakly_canonical(const path& p, error_code& ec);
```
