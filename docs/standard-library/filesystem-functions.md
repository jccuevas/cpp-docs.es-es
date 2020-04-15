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
ms.openlocfilehash: f1b48ed6f533d4ccb5f9ef5e6dbcbd6e5cc4f7a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332048"
---
# <a name="ltfilesystemgt-functions"></a>&lt;filesystem&gt; (Funciones)

Estas funciones [ \<](../standard-library/filesystem.md) gratuitas en el sistema de>encabezado modificando y consultan operaciones en rutas de acceso, archivos, enlaces simbólicos, directorios y volúmenes. Para obtener más información y ejemplos de código, vea Navegación del sistema de archivos [(C++)](../standard-library/file-system-navigation.md).

## <a name="absolute"></a><a name="absolute"></a>Absoluta

```cpp
path absolute(const path& pval, const path& base = current_path());
```

La función devuelve el nombre de ruta absoluto `base`correspondiente a *pval* relativo al nombre de ruta:

1. Si `pval.has_root_name() && pval.has_root_directory()` la función devuelve *pval*.

1. Si `pval.has_root_name() && !pval.has_root_directory()` la `pval.root_name()`  /  `absolute(base).root_directory()`  /  `absolute(base).relative_path()`  /  `pval.relative_path()`función devuelve .

1. Si `!pval.has_root_name() && pval.has_root_directory()` la `absolute(base).root_name()`  / función devuelve *pval*.

1. Si `!pval.has_root_name() && !pval.has_root_directory()` la `absolute(base)`  / función devuelve *pval*.

## <a name="begin"></a><a name="begin"></a>Comenzar

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

Ambas funciones devuelven *iter*.

## <a name="canonical"></a><a name="canonical"></a>Canónica

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

Todas las funciones forman `pabs = absolute(pval, base)` un `pabs = absolute(pval)` nombre de ruta absoluto (o para la sobrecarga sin parámetro base) y, a continuación, lo reducen a una forma canónica en la siguiente secuencia de pasos:

1. Cada componente `X` de `is_symlink(X)` ruta para el `read_symlink(X)`que es **true** se sustituye por .

1. Se elimina `.` cada componente de ruta de acceso (punto es el directorio actual establecido por los componentes de ruta anteriores).

1. Se elimina cada `X` / `..` par de componentes de ruta de acceso (punto-punto es el directorio principal establecido por los componentes de ruta anteriores).

A continuación, `pabs`la función devuelve .

## <a name="copy"></a><a name="copy"></a>Copia

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Todas las funciones posiblemente copian o vinculan uno o más archivos `copy_options::none` *de* *a* bajo control de *opts*, que se toma como para las sobrecargas sin parámetro *opts.* *las opciones* deberán contener como máximo una de las:

- `skip_existing`, `overwrite_existing` o `update_existing`

- `copy_symlinks` o `skip_symlinks`

- `directories_only`, `create_symlinks` o `create_hard_links`

Las funciones determinan `f` primero los `t` valores file_status para *desde* y *para:*

- si `opts & (copy_options::create_symlinks | copy_options::skip_symlinks)`, llamando a`symlink_status`

- de lo contrario, llamando a`status`

- En caso contrario, notifican un error.

Si `!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)`, a continuación, notifican un error (y no hacen nada más).

De lo `is_symlink(f)` contrario, si es a continuación:

- Si `options & copy_options::skip_symlinks`, entonces no haga nada.

- De lo `!exists(t)&& options & copy_options::copy_symlinks`contrario, si , entonces `copy_symlink(from, to, opts)`.

- De lo contrario, informe de un error.

De lo `is_regular_file(f)`contrario, si , entonces:

- Si `opts & copy_options::directories_only`, entonces no haga nada.

- De lo `opts & copy_options::create_symlinks`contrario, si , entonces `create_symlink(to, from)`.

- De lo `opts & copy_options::create_hard_links`contrario, si , entonces `create_hard_link(to, from)`.

- De lo `is_directory(f)`contrario, si , entonces `copy_file(from, to`  /  `from.filename(), opts)`.

- En caso contrario, es `copy_file(from, to, opts)`.

De lo `is_directory(f) && (opts & copy_options::recursive || !opts)`contrario, si , entonces:

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

Todas las funciones posiblemente copian el archivo *de* *a* bajo control de *opts*, que se toma como `copy_options::none` para las sobrecargas sin parámetro *opts.* *las opciones* deberán contener `skip_existing` `overwrite_existing`como `update_existing`máximo una de , , o .

Si `exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))`, a continuación, informe como un error que el archivo ya existe.

De lo `!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))`contrario, si , intente copiar el contenido y los atributos del archivo *desde* el archivo *a*. Notifican como un error si se produce un error en el intento de copia.

Las funciones devuelven **true** si se intenta la copia y se realiza correctamente, de lo contrario **false**.

## <a name="copy_symlink"></a><a name="copy_symlink"></a>copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

Si `is_directory(from)`, la `create_directory_symlink(from, to)`función llama a . De lo `create_symlink(from, to)`contrario, llama a .

## <a name="create_directories"></a><a name="create_directories"></a>create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

Para un nombre de\/\/ruta de acceso como un\/b c, la función crea\/\/directorios a y a b según sea necesario para que pueda crear el directorio a b c según sea necesario. Devuelve **true** solo si realmente crea el directorio *pval*.

## <a name="create_directory"></a><a name="create_directory"></a>create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

La función crea el directorio *pval* según sea necesario. Devuelve true solo si realmente crea el directorio *pval*, en cuyo caso copia `perms::all` permisos del archivo *attr*existente o utiliza para las sobrecargas sin ningún parámetro *attr.*

## <a name="create_directory_symlink"></a><a name="create_directory_symlink"></a>create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

La función crea un vínculo como enlace simbólico al directorio *a*.

## <a name="create_hard_link"></a><a name="create_hard_link"></a>create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

La función crea un vínculo como un vínculo duro al directorio o archivo *a*.

## <a name="create_symlink"></a><a name="create_symlink"></a>create_symlink

```cpp
void create_symlink(const path& to, const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

La función crea un *vínculo* como enlace simbólico al archivo *a*.

## <a name="current_path"></a><a name="current_path"></a>current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

Las funciones sin parámetro *pval* devuelven el nombre de ruta para el directorio actual. Las funciones restantes establecen el directorio actual en *pval*.

## <a name="end"></a><a name="end"></a>Final

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

La primera `directory_iterator()` función vuelve y la segunda función devuelve`recursive_directory_iterator()`

## <a name="equivalent"></a><a name="equivalent"></a>Equivalente

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

Las funciones devuelven **true** solo si *izquierda* y *derecha* eligen la misma entidad de sistema de archivos.

## <a name="exists"></a><a name="exists"></a>Existe

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `status_known && stat.type() != file_not_found`. Las funciones segunda `exists(status(pval))`y tercera devuelven .

## <a name="file_size"></a><a name="file_size"></a>file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

Las funciones devuelven el tamaño en bytes `exists(pval) && is_regular_file(pval)` del archivo elegido por *pval*, si y el tamaño del archivo se puede determinar. De lo contrario, `uintmax_t(-1)`notifican un error y devuelven .

## <a name="hard_link_count"></a><a name="hard_link_count"></a>hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

La función devuelve el número de \-vínculos duros para *pval*, o 1 si se produce un error.

## <a name="hash_value"></a><a name="hash_value"></a>hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

La función devuelve `pval.native()`un valor hash para .

## <a name="is_block_file"></a><a name="is_block_file"></a>is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::block`. Las funciones `is_block_file(status(pval))`restantes devuelven .

## <a name="is_character_file"></a><a name="is_character_file"></a>is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::character`. Las funciones `is_character_file(status(pval))`restantes devuelven .

## <a name="is_directory"></a><a name="is_directory"></a>is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::directory`. Las funciones `is_directory_file(status(pval))`restantes devuelven .

## <a name="is_empty"></a><a name="is_empty"></a>is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

Si `is_directory(pval)`, la `directory_iterator(pval) == directory_iterator()`función devuelve ; de lo `file_size(pval) == 0`contrario devuelve .

## <a name="is_fifo"></a><a name="is_fifo"></a>is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::fifo`. Las funciones `is_fifo(status(pval))`restantes devuelven .

## <a name="is_other"></a><a name="is_other"></a>is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::other`. Las funciones `is_other(status(pval))`restantes devuelven .

## <a name="is_regular_file"></a><a name="is_regular_file"></a>is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::regular`. Las funciones `is_regular_file(status(pval))`restantes devuelven .

## <a name="is_socket"></a><a name="is_socket"></a>is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::socket`. Las funciones `is_socket(status(pval))`restantes devuelven .

## <a name="is_symlink"></a><a name="is_symlink"></a>is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve `stat.type() == file_type::symlink`. Las funciones `is_symlink(status(pval))`restantes devuelven .

## <a name="last_write_time"></a><a name="last_write_time"></a>last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

Las dos primeras funciones devuelven la hora `file_time_type(-1)` de la última modificación de datos para *pval*, o si se produce un error. Las dos últimas funciones establecen la hora de la última modificación de datos para *pval* en *new_time*.

## <a name="permissions"></a><a name="permissions"></a>Permisos

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

Las funciones establecen los permisos para `mask & perms::mask` el `perms & (perms::add_perms | perms::remove_perms)`nombre de ruta elegido por *pval* en bajo control de . *máscara* debe contener como `perms::add_perms` `perms::remove_perms`máximo uno de y .

Si `mask & perms::add_perms`, las funciones `status(pval).permissions() | mask & perms::mask`establecen los permisos en . De lo `mask & perms::remove_perms`contrario, si , `status(pval).permissions() & ~(mask & perms::mask)`las funciones establecen los permisos en . De lo contrario, las `mask & perms::mask`funciones establecen los permisos en .

## <a name="proximate"></a><a name="proximate"></a>Próximo

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

Las funciones informan `path()` `!is_symlink(pval)`de un error y devuelven si . De lo contrario, las funciones devuelven un objeto de tipo `path` que tiene el vínculo simbólico.

## <a name="relative"></a><a name="relative"></a>Relativa

```cpp
path relative(const path& p, error_code& ec);
path relative(const path& p, const path& base = current_path());
path relative(const path& p, const path& base, error_code& ec);
```

## <a name="remove"></a><a name="remove"></a>eliminar

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

Las funciones devuelven **true** solo si `exists(symlink_status(pval))` y el archivo se elimina correctamente. Un enlace simbólico se elimina en sí mismo, no el archivo que elige.

## <a name="remove_all"></a><a name="remove_all"></a>remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

Si *pval* es un directorio, las funciones eliminan recursivamente todas las entradas de directorio y, a continuación, la propia entrada. De lo contrario, las funciones llaman a `remove`. Devuelven un recuento de todos los elementos que se quitaron correctamente.

## <a name="rename"></a><a name="rename"></a>Renombrar

```cpp
void rename(const path& from, const path& to);
void rename(const path& from, const path& to, error_code& ec) noexcept;
```

Las funciones renombran *de* *a*. Se cambia el nombre de un enlace simbólico, no el archivo que elige.

## <a name="resize_file"></a><a name="resize_file"></a>resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

Las funciones alteran el tamaño de un archivo de tal forma que`file_size(pval) == size`

## <a name="space"></a><a name="space"></a>Espacio

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

La función devuelve información sobre el volumen elegido `space_info`por *pval*, en una estructura de tipo . La estructura `uintmax_t(-1)` contiene para cualquier valor que no se pueda determinar.

## <a name="status"></a><a name="status"></a>Estado

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

Las funciones devuelven el estado pathname, el tipo de archivo y los permisos asociados a *pval*. Un enlace simbólico no se ha probado, pero el archivo que elige.

## <a name="status_known"></a><a name="status_known"></a>status_known

```cpp
bool status_known(file_status stat) noexcept;
```

La función devuelve`stat.type() != file_type::none`

## <a name="swap"></a><a name="swap"></a>Intercambio

```cpp
void swap(path& left, path& right) noexcept;
```

La función intercambia el contenido de *izquierda* y *derecha*.

## <a name="symlink_status"></a><a name="symlink_status"></a>symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

Las funciones devuelven el estado del enlace simbólico del nombre de ruta, el tipo de archivo y los permisos asociados con *pval*. Las funciones se `status(pval)` comportan igual que excepto que un enlace simbólico se prueba en sí mismo, no el archivo que elige.

## <a name="system_complete"></a><a name="system_complete"></a>system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

Las funciones devuelven un nombre de ruta de acceso absoluta que tiene en cuenta, según sea necesario, el directorio actual asociado a su nombre de raíz. \(Para POSIX, las `absolute(pval)`funciones devuelven .\)

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

La primera función se `path(source)` comporta igual que y la `path(first, last)` segunda función se comporta igual que excepto que el origen elegido en cada caso se toma como una secuencia de elementos char codificados como UTF-8, sea cual sea el sistema de archivos.

## <a name="weakly_canonical"></a><a name="weakly_canonical"></a>weakly_canonical

```cpp
path weakly_canonical(const path& p);
path weakly_canonical(const path& p, error_code& ec);
```
