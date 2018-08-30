---
title: '&lt;filesystem&gt; (Funciones) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
author: corob-msft
ms.author: corob
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
ms.workload:
- cplusplus
ms.openlocfilehash: 0e47339813256d189e1ce6b71506d9ae29a93f51
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213470"
---
# <a name="ltfilesystemgt-functions"></a>&lt;filesystem&gt; (Funciones)

Estas funciones libres del encabezado [\<filesystem>](../standard-library/filesystem.md) realizan operaciones de modificación y consulta en rutas de acceso, archivos, vínculos simbólicos, directorios y volúmenes. Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md).
||||
|-|-|-|
|[absolute](#absolute)|[begin](#begin)|[canonical](#canonical)|
|[copy](#copy)|[copy_file](#copy_file)|[copy_symlink](#copy_symlink)|
|[create_directories](#create_directories)|[create_directory](#create_directory)|[create_directory_symlink](#create_directory_symlink)|
|[create_hard_link](#create_hard_link)|[create_symlink](#create_symlink)|[current_path](#current_path)|
|[end](#end)|[equivalent](#equivalent)|[exists](#exists)|
|[file_size](#file_size)|[hard_link_count](#hard_link_count)|[hash_value](#hash_value)|
|[is_block_file](#is_block_file)|[is_character_file](#is_character_file)|[is_directory](#is_directory)|
|[is_empty](#is_empty)|[is_fifo](#is_fifo)|[is_other](#is_other)|
|[is_regular_file](#is_regular_file)|[is_socket](#is_socket)|[is_symlink](#is_symlink)|
|[last_write_time](#last_write_time)|[permissions](#permissions)|[read_symlink](#read_symlink)|
|[remove](#remove)|[remove_all](#remove_all)|[rename](#rename)|
|[resize_file](#resize_file)|[space](#space)|[status](#status)|
|[status_known](#status_known)|[swap](#swap)|[symlink_status](#symlink_status)|
|[system_complete](#system_complete)|[temp_directory_path](#temp_directory_path)|[u8path](#u8path)|


## <a name="absolute"></a> absoluta

```cpp
path absolute(const path& pval, const path& base = current_path());
```

La función devuelve el nombre de ruta de acceso absoluta correspondiente a un `pval` en relación con el nombre de ruta de acceso `base`:

1. Si pval.has_root_name() && pval.has_root_directory(), la función devuelve pval.

1. Si pval.has_root_name() && !pval.has_root_directory(), la función devuelve pval.root_name() / absolute(base).root_directory() / absolute(base).relative_path() / pval.relative_path().

1. Si !pval.has_root_name() && pval.has_root_directory(), la función devuelve absolute(base).root_name() / pval.

1. Si !pval.has_root_name() && !pval.has_root_directory(), la función devuelve absolute(base) / pval.

## <a name="begin"></a>  begin

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

Ambas funciones devuelven `iter`.

## <a name="canonical"></a>  canonical

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

Todas las funciones forman un nombre de ruta de acceso absoluta pabs = absolute(pval, base) (o pabs = absolute(pval) para la sobrecarga sin parámetros de base) y luego lo reducen a una forma canónica en la siguiente secuencia de pasos:

1. Cada componente "X" de ruta de acceso para el que is_symlink(X) es true se sustituye por read_symlink(X).

1. Cada componente de ruta de acceso "." (punto es el directorio actual establecido por los componentes de ruta de acceso anteriores) se quita.

1. Cada par de componentes de ruta de acceso "X/.." (punto punto es el directorio principal establecido por los componentes de ruta de acceso anteriores) se quita.

La función devuelve pabs.

## <a name="copy"></a>  copy

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Posiblemente, todas las funciones copian o vinculan uno o varios archivos de `from` a `to` bajo el control de `opts`, que se toma como copy_options::none para las sobrecargas que no tienen el parámetro `opts`. `opts` debe contener, como máximo, una de las siguientes opciones:

- skip_existing, overwrite_existing o update_existing

- copy_symlinks o skip_symlinks

- directories_only, create_symlinks o create_hard_links

Las funciones determinan primero los valores file_status f para `from` y t para `to`:

- si opts & (copy_options::create_symlinks &#124; copy_options::skip_symlinks), mediante una llamada a symlink_status

- De lo contrario, mediante una llamada a status.

- En caso contrario, notifican un error.

Si !exists(f) &#124;&#124; equivalent(f, t) &#124;&#124; is_other(f) &#124;&#124; is_other(t) &#124;&#124; is_directory(f)&& is_regular_file(t), entonces notifican un error (y no realizan ninguna otra acción).

De lo contrario, si is_symlink(f):

- Si options & copy_options::skip_symlinks, no hacen nada.

- De lo contrario, si !exists(t)&& options & copy_options::copy_symlinks, entonces copy_symlink(from, to, opts).

- En caso contrario, notifican un error.

De lo contrario, si is_regular_file(f):

- Si opts & copy_options::directories_only, no hacen nada.

- De lo contrario, si opts & copy_options::create_symlinks, entonces create_symlink(to, from).

- Pero, si opts & copy_options::create_hard_links, entonces create_hard_link(to, from).

- De lo contrario, si is_directory(f), entonces copy_file(from, to / from.filename(), opts).

- En caso contrario, copy_file(from, to, opts).

De lo contrario, si is_directory(f) && (opts & copy_options::recursive &#124;&#124; !opts), entonces:

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

## <a name="copy_file"></a>  copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Posiblemente, todas las funciones copian el archivo que se encuentra en `from` a `to` bajo el control de `opts`, que se toma como copy_options::none para las sobrecargas que no tienen el parámetro `opts`. `opts` debe contener, como máximo, una de las siguientes opciones: skip_existing, overwrite_existing o update_existing.

Si exists\(to\) && \!\(opts & \(copy_options::skip_existing &#124; copy_options::overwrite_existing &#124; copy_options::update_existing\)\), notifican como un error que el archivo ya exista.

De lo contrario, si \!exists\(to\) &#124;&#124; opts & copy_options::overwrite_existing &#124;&#124; opts & copy_options::update_existing&& last_write_time\(to\) \< last_write_time\(from\) &#124;&#124; \!\(opts & \(copy_options::skip_existing &#124; copy_options::overwrite_existing &#124; copy_options:update_existing\)\) , intentan copiar el contenido y los atributos del archivo from de origen al archivo to de destino. Notifican un error si se produce un error en el intento de copia.

Las funciones devuelven true si la copia se ha intentado y se realiza correctamente; en caso contrario, devuelven false.

## <a name="copy_symlink "></a>  copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

Si is_directory\(from\), la función llama a create_directory_symlink\(from, to\). De lo contrario, llama a create_symlink\(from, to\).

## <a name="create_directories"></a>  create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

Para un nombre de ruta de acceso como a\/b\/c, la función crea los directorios a y a\/b según sea necesario para poder crear el directorio a\/b\/c según sea necesario. Devuelve True solo si crea realmente el directorio `pval`.

## <a name="create_directory"></a>  create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

La función crea el directorio `pval` según sea necesario. Devuelve True solo si realmente crea el directorio `pval`, en cuyo caso copia los permisos del archivo `attr` existente o usa perms::all para las sobrecargas que no tienen el parámetro `attr`.

## <a name="create_directory_symlink "></a>  create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

La función crea el vínculo como un vínculo simbólico al directorio `to`.

## <a name="create_hard_link"></a>  create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

La función crea el vínculo como un vínculo físico al directorio o archivo `to`.

## <a name="create_symlink "></a>  create_symlink

```cpp
void create_symlink(const path& to,  const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

La función crea `link` como un vínculo simbólico al archivo `to`.

## <a name="current_path"></a>  current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

Las funciones que no tienen el parámetro `pval` devuelven el nombre de ruta de acceso del directorio actual. Las funciones restantes establecen el directorio actual en `pval`.

## <a name="end"></a>  end

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

La primera función devuelve directory_iterator\(\) y la segunda función devuelve recursive_directory_iterator\(\).

## <a name="equivalent"></a>  equivalent

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

Las funciones devuelven True solo si `left` y `right` designan la misma entidad del sistema de archivos.

## <a name="exists"></a>  exists

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve status_known && stat.type\(\) \!\= file_not_found. Las funciones segunda y tercera devuelven exists\(status\(pval\)\).

## <a name="file_size"></a>  file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

Las funciones devuelven el tamaño en bytes del archivo designado por `pval`, si exists\(pval\) && is_regular_file\(pval\) y si se puede determinar el tamaño del archivo. En caso contrario, notifican un error y devuelven uintmax_t\(\-1\).

## <a name="hard_link_count"></a>  hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

La función devuelve el número de vínculos físicos para `pval` o \-1 si se produce un error.

## <a name="hash_value"></a>  hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

La función devuelve un valor hash para pval.native\(\).

## <a name="is_block_file"></a>  is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve stat.type\(\) \=\= file_type::block. Las funciones restantes devuelven is_block_file\(status\(pval\)\).

## <a name="is_character_file"></a>  is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve stat.type\(\) \=\= file_type::character. Las funciones restantes devuelven is_character_file\(status\(pval\)\).

## <a name="is_directory "></a>  is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve stat.type\(\) \=\= file_type::directory. Las funciones restantes devuelven is_directory_file\(status\(pval\)\).

## <a name="is_empty"></a>  is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

Si is_directory\(pval\), la función devuelve directory_iterator\(pval\) \=\= directory_iterator\(\); de lo contrario, devuelve file_size\(pval\) \=\= 0.

## <a name="is_fifo"></a>  is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve stat.type\(\) \=\= file_type::fifo. Las funciones restantes devuelven is_fifo\(status\(pval\)\).

## <a name="is_other"></a>  is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve stat.type\(\) \=\= file_type::other. Las funciones restantes devuelven is_other\(status\(pval\)\).

## <a name="s_regular_file"></a>  is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve stat.type\(\) \=\= file_type::regular. Las funciones restantes devuelven is_regular_file\(status\(pval\)\).

## <a name="is_socket"></a>  is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve stat.type\(\) \=\= file_type::socket. Las funciones restantes devuelven is_socket\(status\(pval\)\).

## <a name="is_symlink"></a>  is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

La primera función devuelve stat.type\(\) \=\= file_type::symlink. Las funciones restantes devuelven is_symlink\(status\(pval\)\).

## <a name="last_write_time"></a>  last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

Las dos primeras funciones devuelven la hora de la última modificación de datos de `pval` o file_time_type\(\-1\) si se produce un error. Las dos últimas funciones establecen la hora de la última modificación de datos de `pval` en new_time.

## <a name="permissions"></a>  permissions

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

Las funciones establecen los permisos para el nombre de ruta de acceso designado por `pval` en mask & perms::mask bajo el control de perms & \(perms::add_perms &#124; perms::remove_perms\). mask debe contener, como máximo, uno de los siguientes elementos: perms::add_perms o perms::remove_perms.

Si mask & perms::add_perms, las funciones establecen los permisos en status\(pval\).permissions\(\) &#124; mask & perms::mask. En caso contrario, si mask & perms::remove_perms, las funciones establecen los permisos en status\(pval\).permissions\(\) & ~\(mask & perms::mask\). De lo contrario, las funciones establecen los permisos en mask & perms::mask.

## <a name="read_symlink"></a>  read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

Las funciones notifican un error y devuelven path\(\) si \!is_symlink\(pval\). De lo contrario, las funciones devuelven un objeto de tipo `path` que tiene el vínculo simbólico.

## <a name="remove"></a>  remove

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

Las funciones devuelven True solo si exists\(symlink_status\(pval\)\) y el archivo se quita correctamente. Se quita un vínculo simbólico, no el archivo que este designa.

## <a name="remove_all"></a>  remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

Si `pval` es un directorio, las funciones quitan todas las entradas de directorio de forma recursiva y luego la entrada en sí. De lo contrario, las funciones llaman a remove. Devuelven un recuento de todos los elementos que se quitaron correctamente.

## <a name="rename"></a>  rename

```cpp
void rename(const path& from,  const path& to);
void rename(const path& from,  const path& to, error_code& ec) noexcept;
```

Las funciones cambian el nombre de `from` a `to`. Se cambia el nombre de un vínculo simbólico, no del archivo que este designa.

## <a name="resize_file"></a>  resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

Las funciones modifican el tamaño de un archivo de tal modo que file_size\(pval\) \=\= size.

## <a name="space"></a>  space

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

La función devuelve información sobre el volumen designado por `pval`, en una estructura de tipo `space_info`. La estructura contiene uintmax_t\(\-1\) para cualquier valor que no se puede determinar.

## <a name="status"></a>  status

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

Las funciones devuelven el estado del nombre de ruta de acceso, el tipo de archivo y los permisos asociados a `pval`. No se comprueba un vínculo simbólico, sino el archivo que este designa.

## <a name="status_known"></a>  status_known

```cpp
bool status_known(file_status stat) noexcept;
```

La función devuelve stat.type\(\) \!\= file_type::none

## <a name="swap"></a>  swap

```cpp
void swap(path& left, path& right) noexcept;
```

La función intercambia el contenido de `left` y `right`.

## <a name="symlink_status"></a>  symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

Las funciones devuelven el estado de vínculo simbólico del nombre de ruta de acceso, el tipo de archivo y los permisos asociados a `pval`. Las funciones se comportan igual que status\(pval\), excepto que se prueba un vínculo simbólico en sí, pero no el archivo que este designa.

## <a name="system_complete"></a>  system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

Las funciones devuelven un nombre de ruta de acceso absoluta que tiene en cuenta, según sea necesario, el directorio actual asociado a su nombre de raíz. \(Para Posix, las funciones devuelven absolute\(pval\).\)

## <a name="temp_directory_path"></a>  temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

Las funciones devuelven un nombre de ruta de acceso de un directorio adecuado para contener los archivos temporales.

## <a name="u8path"></a>  u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

La primera función se comporta igual que path(source) y la segunda función se comporta igual que path(first, last), excepto que el origen designado en cada caso se toma como una secuencia de elementos char codificados como UTF-8, independientemente del sistema de archivos.


