---
title: path (Clase)
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 669dfd2c8cd8576ebfb6684bab7cf63cdd51babc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372105"
---
# <a name="path-class"></a>path (Clase)

La clase **path** almacena `string_type`un `myname` objeto de tipo , llamado aquí para fines de exposición, adecuado para su uso como nombre de ruta de acceso. `string_type`es un `basic_string<value_type>`sinónimo `value_type` de , donde es un sinónimo de **wchar_t** en Windows o **char** en POSIX.

Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Sintaxis

```cpp
class path;
```

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[path](#path)|Construye un objeto `path`.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[const_iterator](#const_iterator)|Sinónimo de `iterator`.|
|[Iterador](#iterator)|Iterador constante bidireccional que `path` designa los componentes de `myname`.|
|[string_type](#string_type)|El tipo es un sinónimo de `basic_string<value_type>`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Anexar](#append)|Anexa la secuencia especificada `mypath`a , convertida e insertando un preferred_separator según sea necesario.|
|[Asignar](#assign)|Reemplaza `mypath` por la secuencia especificada, convertida según sea necesario.|
|[Comenzar](#begin)|Devuelve `path::iterator` un designación del primer elemento de ruta de acceso en el nombre de ruta de acceso, si está presente.|
|[c_str](#c_str)|Devuelve un puntero al `mypath`primer carácter de .|
|[Claro](#clear)|Ejecuta `mypath.clear()`.|
|[Comparar](#compare)|Devuelve valores de comparación.|
|[concat](#compare)|Anexa la secuencia especificada `mypath`a , convertida (pero no insertando un separador) según sea necesario.|
|[Vacío](#empty)|Devuelve `mypath.empty()`.|
|[Final](#end)|Devuelve un iterador de `iterator`fin de secuencia de tipo .|
|[Extensión](#extension)|Devuelve el `filename()`sufijo de .|
|[Nombre](#filename)|Devuelve el componente del directorio raíz de myname, específicamente `empty() path() : *--end()`. El componente puede estar vacío.|
|[generic_string](#generic_string)|Devuelve `this->string<Elem, Traits, Alloc>(al)` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.|
|[generic_u16string](#generic_u16string)|Devuelve `u16string()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.|
|[generic_u32string](#generic_u32string)|Devuelve `u32string()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.|
|[generic_u8string](#generic_u8string)|Devuelve `u8string()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.|
|[generic_wstring](#generic_wstring)|Devuelve `wstring()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.|
|[has_extension](#has_extension)|Devuelve `!extension().empty()`.|
|[has_filename](#has_filename)|Devuelve `!filename().empty()`.|
|[has_parent_path](#has_parent_path)|Devuelve `!parent_path().empty()`.|
|[has_relative_path](#has_relative_path)|Devuelve `!relative_path().empty()`.|
|[has_root_directory](#has_root_directory)|Devuelve `!root_directory().empty()`.|
|[has_root_name](#has_root_name)|Devuelve `!root_name().empty()`.|
|[has_root_path](#has_root_path)|Devuelve `!root_path().empty()`.|
|[has_stem](#has_stem)|Devuelve `!stem().empty()`.|
|[is_absolute](#is_absolute)|Para Windows, la `has_root_name() && has_root_directory()`función devuelve . Para POSIX, la `has_root_directory()`función devuelve .|
|[is_relative](#is_relative)|Devuelve `!is_absolute()`.|
|[make_preferred](#make_preferred)|Convierte cada separador en un preferred_separator según sea necesario.|
|[Nativo](#native)|Devuelve `myname`.|
|[parent_path](#parent_path)|Devuelve el componente `myname`de ruta de acceso principal de .|
|[preferred_separator](#preferred_separator)|El objeto constante ofrece el carácter preferido para separar los componentes de la ruta de acceso, según el sistema operativo host. |
|[relative_path](#relative_path)|Devuelve el componente `myname`de ruta de acceso relativa de . |
|[remove_filename](#remove_filename)|Quita el nombre de archivo.|
|[replace_extension](#replace_extension)|Reemplaza la extensión `myname`de . |
|[replace_filename](#replace_filename)|RReemplaza el nombre de archivo.|
|[root_directory](#root_directory)|Devuelve el componente `myname`de directorio raíz de . |
|[root_name](#root_name)|Devuelve el componente `myname`de nombre raíz de . |
|[root_path](#root_path)|Devuelve el componente `myname`de ruta de acceso raíz de .|
|[stem](#stem)|Devuelve `stem` el `myname`componente de .|
|[string](#string)|Convierte la secuencia `mypath`almacenada en .|
|[swap](#swap)|Ejecuta `swap(mypath, right.mypath)`.|
|[u16string](#u16string)|Convierte la secuencia `mypath` almacenada en UTF-16 y la devuelve `u16string`almacenada en un objeto de tipo .|
|[u32string](#u32string)|Convierte la secuencia `mypath` almacenada en UTF-32 y la devuelve `u32string`almacenada en un objeto de tipo .|
|[u8string](#u8string)|Convierte la secuencia `mypath` almacenada en UTF-8 y la devuelve `u8string`almacenada en un objeto de tipo .|
|[value_type](#value_type)|El tipo describe los elementos de la ruta de acceso preferidos de sistema operativo host.|
|[wstring](#wstring)|Convierte la secuencia `mypath` almacenada en la codificación favorecida por el sistema host para una `wchar_t` secuencia y la devuelve almacenada en un objeto de tipo `wstring`.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador](#op_as)|Reemplaza los elementos de la ruta de acceso por una copia de otra ruta de acceso.|
|[operador +o](#op_add)|Varias `concat` expresiones.|
|[operador/](#op_divide)|Varias `append` expresiones.|
|[operador string_type](#op_string)|Devuelve `myname`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<sistema de archivos>

**Espacio de nombres:** std::experimental::filesystem

## <a name="pathappend"></a><a name="append"></a>path::append

Anexa la secuencia especificada `mypath`a , convertida e insertando una `preferred_separator` según sea necesario.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Parámetros

*Fuente*\
Secuencia especificada.

*Primero*\
Inicio de la secuencia especificada.

*Última*\
Fin de la secuencia especificada.

## <a name="pathassign"></a><a name="assign"></a>path::assign

Reemplaza `mypath` por la secuencia especificada, convertida según sea necesario.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Parámetros

*Fuente*\
Secuencia especificada.

*Primero*\
Inicio de la secuencia especificada.

*Última*\
Fin de la secuencia especificada.

## <a name="pathbegin"></a><a name="begin"></a>path::begin

Devuelve `path::iterator` un designación del primer elemento de ruta de acceso en el nombre de ruta de acceso, si está presente.

```cpp
iterator begin() const;
```

## <a name="pathc_str"></a><a name="c_str"></a>camino::c_str

Devuelve un puntero al `mypath`primer carácter de .

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="pathclear"></a><a name="clear"></a>path::clear

Ejecuta `mypath.clear()`.

```cpp
void clear() noexcept;
```

## <a name="pathcompare"></a><a name="compare"></a>path::compare

La primera función devuelve `mypath.compare(pval.native())`. La segunda función devuelve `mypath.compare(str)`. La tercera `mypath.compare(ptr)`función devuelve .

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parámetros

*Pval*\
Ruta de acceso para comparar.

*Str*\
Cadena para comparar.

*Ptr*\
Puntero para comparar.

## <a name="pathconcat"></a><a name="concat"></a>path::concat

Anexa la secuencia especificada `mypath`a , convertida (pero no insertando un separador) según sea necesario.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Parámetros

*Fuente*\
Secuencia especificada.

*Primero*\
Inicio de la secuencia especificada.

*Última*\
Fin de la secuencia especificada.

## <a name="pathconst_iterator"></a><a name="const_iterator"></a>camino::const_iterator

Sinónimo de `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="pathempty"></a><a name="empty"></a>path::empty

Devuelve `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="pathend"></a><a name="end"></a>path::end

Devuelve un iterador de `iterator`fin de secuencia de tipo .

```cpp
iterator end() const;
```

## <a name="pathextension"></a><a name="extension"></a>path::extension

Devuelve el `filename()`sufijo de .

```cpp
path extension() const;
```

### <a name="remarks"></a>Observaciones

Devuelve el `filename() X` sufijo de tal forma que:

Si `X == path(".") || X == path("..")` o `X` si no contiene ningún punto, el sufijo está vacío.

De lo contrario, el sufijo comienza con (e incluye) el punto situado más al derecha.

## <a name="pathfilename"></a><a name="filename"></a>path::filename

Devuelve el componente del directorio raíz de myname, específicamente `empty() path() : *--end()`. El componente puede estar vacío.

```cpp
path filename() const;
```

## <a name="pathgeneric_string"></a><a name="generic_string"></a>path::generic_string

Devuelve `this->string<Elem, Traits, Alloc>(al)` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="pathgeneric_u16string"></a><a name="generic_u16string"></a>camino::generic_u16string

Devuelve `u16string()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

```cpp
u16string generic_u16string() const;
```

## <a name="pathgeneric_u32string"></a><a name="generic_u32string"></a>path::generic_u32string

Devuelve `u32string()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

```cpp
u32string generic_u32string() const;
```

## <a name="pathgeneric_u8string"></a><a name="generic_u8string"></a>camino::generic_u8string

Devuelve `u8string()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

```cpp
string generic_u8string() const;
```

## <a name="pathgeneric_wstring"></a><a name="generic_wstring"></a>camino::generic_wstring

Devuelve `wstring()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

```cpp
wstring generic_wstring() const;
```

## <a name="pathhas_extension"></a><a name="has_extension"></a>camino::has_extension

Devuelve `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="pathhas_filename"></a><a name="has_filename"></a>path::has_filename

Devuelve `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="pathhas_parent_path"></a><a name="has_parent_path"></a>camino::has_parent_path

Devuelve `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="pathhas_relative_path"></a><a name="has_relative_path"></a>path::has_relative_path

Devuelve `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="pathhas_root_directory"></a><a name="has_root_directory"></a>path::has_root_directory

Devuelve `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="pathhas_root_name"></a><a name="has_root_name"></a>camino::has_root_name

Devuelve `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="pathhas_root_path"></a><a name="has_root_path"></a>path::has_root_path

Devuelve `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="pathhas_stem"></a><a name="has_stem"></a>path::has_stem

Devuelve `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="pathis_absolute"></a><a name="is_absolute"></a>camino::is_absolute

Para Windows, la `has_root_name() && has_root_directory()`función devuelve . Para POSIX, la `has_root_directory()`función devuelve .

```cpp
bool is_absolute() const;
```

## <a name="pathis_relative"></a><a name="is_relative"></a>camino::is_relative

Devuelve `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="pathiterator"></a><a name="iterator"></a>path::iterator

Iterador constante bidireccional que designa `myname`los componentes de ruta de acceso de .

```cpp
class iterator
   {
   // bidirectional iterator for path
   typedef bidirectional_iterator_tag iterator_category;
   typedef path_type value_type;
   typedef ptrdiff_t difference_type;
   typedef const value_type *pointer;
   typedef const value_type& reference;
   // ...
   };
```

### <a name="remarks"></a>Observaciones

La clase describe un iterador constante `path` bidireccional `myname` que designa los componentes de la secuencia:

1. el nombre de raíz, si está presente

1. el directorio raíz, si está presente

1. los elementos de directorio `path`restantes del elemento primario, si están presentes, terminando con el nombre de archivo, si está presente

Para `pval` un objeto `path`de tipo :

1. `path::iterator X = pval.begin()`designa el `path` primer elemento en el nombre de ruta de acceso, si está presente.

1. `X == pval.end()`es cierto `X` cuando los puntos justo después del final de la secuencia de componentes.

1. `*X`devuelve una cadena que coincide con el componente actual

1. `++X` designa el componente siguiente de la secuencia, si está presente.

1. `--X` designa el componente anterior de la secuencia, si existe.

1. La `myname` modificación invalida todos los iteradores que designan elementos en `myname`.

## <a name="pathmake_preferred"></a><a name="make_preferred"></a>path::make_preferred

Convierte cada separador `preferred_separator` en un según sea necesario.

```cpp
path& make_preferred();
```

## <a name="pathnative"></a><a name="native"></a>path::native

Devuelve `myname`.

```cpp
const string_type& native() const noexcept;
```

## <a name="pathoperator"></a><a name="op_as"></a>ruta::operador ?

Reemplaza los elementos de la ruta de acceso por una copia de otra ruta de acceso.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
La [ruta](../standard-library/path-class.md) que se `path`copia en el archivo .

*Fuente*\
La ruta de origen.

### <a name="remarks"></a>Observaciones

El primer operador `right.myname` `myname`miembro copia en . El segundo operador `right.myname` `myname`miembro se mueve a . El tercer operador miembro se `*this = path(source)`comporta igual que .

## <a name="pathoperator"></a><a name="op_add"></a>ruta::operador+-

Varias `concat` expresiones.

```cpp
path& operator+=(const path& right);
path& operator+=(const string_type& str);
path& operator+=(const value_type *ptr);
path& operator+=(value_type elem);

template <class Source>
path& operator+=(const Source& source);

template <class Elem>
path& operator+=(Elem elem);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
La ruta de acceso agregada.

*Str*\
La cadena agregada.

*Ptr*\
El puntero agregado.

*Elem*\
El `value_type` añadido `Elem`o .

*Fuente*\
La fuente agregada.

### <a name="remarks"></a>Observaciones

Las funciones miembro se comportan igual que las siguientes expresiones correspondientes:

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="pathoperator"></a><a name="op_divide"></a>ruta::operador/

Varias `append` expresiones.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
La ruta de acceso agregada.

*Fuente*\
La fuente agregada.

### <a name="remarks"></a>Observaciones

Las funciones miembro se comportan igual que las siguientes expresiones correspondientes:

1. `append(right);`

1. `append(source);`

## <a name="pathoperator-string_type"></a><a name="op_string"></a>path::operator string_type

Devuelve `myname`.

```cpp
operator string_type() const;
```

## <a name="pathparent_path"></a><a name="parent_path"></a>path::parent_path

Devuelve el componente `myname`de ruta de acceso principal de .

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Observaciones

Devuelve el componente `myname`de ruta de `myname` acceso `filename().native()` principal de , específicamente el prefijo de después de quitar y los separadores de directorio inmediatamente anteriores. (Igualmente, `begin() != end()`si , es la combinación `[begin(), --end())` de todos `operator/=`los elementos en el rango mediante la aplicación sucesiva .) El componente puede estar vacío.

## <a name="pathpath"></a><a name="path"></a>camino::path

Construye un `path` de varias maneras.

```cpp
path();

path(const path& right);
path(path&& right) noexcept;

template <class Source>
path(const Source& source);

template <class Source>
path(const Source& source, const locale& loc);

template <class InIt>
path(InIt first, InIt last);

template <class InIt>
path(InIt first, InIt last, const locale& loc);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
La ruta de acceso de la que la ruta de acceso construida debe ser una copia.

*Fuente*\
El origen del que la ruta de acceso construida debe ser una copia.

*Loc*\
La configuración regional especificada.

*Primero*\
Posición del primer elemento que se va a copiar.

*Última*\
La posición del último elemento que se va a copiar.

### <a name="remarks"></a>Observaciones

Todos los constructores construyen `myname` de varias maneras:

Porque `path()` es `myname()`.

Para `path(const path& right`) `myname(right.myname)`es .

Porque `path(path&& right)` es `myname(right.myname)`.

Porque `template<class Source> path(const Source& source)` es `myname(source)`.

Porque `template<class Source> path(const Source& source, const locale& loc)` es `myname(source)`, la obtención de las `loc`facetas codecvt necesarias de .

Porque `template<class InIt> path(InIt first, InIt last)` es `myname(first, last)`.

Porque `template<class InIt> path(InIt first, InIt last, const locale& loc)` es `myname(first, last)`, la obtención de las `loc`facetas codecvt necesarias de .

## <a name="pathpreferred_separator"></a><a name="preferred_separator"></a>path::preferred_separator

El objeto constante ofrece el carácter preferido para separar los componentes de la ruta de acceso, según el sistema operativo host.

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume POSIX
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>Observaciones

Tenga en cuenta que en la mayoría de los contextos en Windows también se permite usar L '/' en su lugar.

## <a name="pathrelative_path"></a><a name="relative_path"></a>camino::relative_path

Devuelve el componente `myname`de ruta de acceso relativa de .

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Observaciones

Devuelve el componente `myname`de ruta de `myname` acceso `root_path().native()` relativa de , específicamente el sufijo de después de quitar y los separadores de directorio redundantes inmediatamente posteriores. El componente puede estar vacío.

## <a name="pathremove_filename"></a><a name="remove_filename"></a>path::remove_filename

Quita el nombre de archivo.

```cpp
path& remove_filename();
```

## <a name="pathreplace_extension"></a><a name="replace_extension"></a>camino::replace_extension

Reemplaza la extensión `myname`de .

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Parámetros

*newext*\
La nueva extensión.

### <a name="remarks"></a>Observaciones

En primer lugar, quita el sufijo `extension().native()` de `myname`. A `!newext.empty() && newext[0] != dot` continuación, `dot` `*path(".").c_str()`si `dot` (donde está `myname`), se anexa a . A *continuación, newext* se anexa a `myname`.

## <a name="pathreplace_filename"></a><a name="replace_filename"></a>camino::replace_filename

Reemplaza el nombre de archivo.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>Parámetros

*Pval*\
La ruta de acceso del nombre de archivo.

### <a name="remarks"></a>Observaciones

La función miembro ejecuta:

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="pathroot_directory"></a><a name="root_directory"></a>camino::root_directory

Devuelve el componente `myname`de directorio raíz de .

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Observaciones

El componente puede estar vacío.

## <a name="pathroot_name"></a><a name="root_name"></a>camino::root_name

Devuelve el componente `myname`de nombre raíz de .

```cpp
path root_name() const;
```

### <a name="remarks"></a>Observaciones

El componente puede estar vacío.

## <a name="pathroot_path"></a><a name="root_path"></a>path::root_path

Devuelve el componente `myname`de ruta de acceso raíz de .

```cpp
path root_path() const;
```

### <a name="remarks"></a>Observaciones

Devuelve el componente `myname`de ruta `root_name()`  /  `root_directory`de acceso raíz de , específicamente . El componente puede estar vacío.

## <a name="pathstem"></a><a name="stem"></a>path::stem

Devuelve `stem` el `myname`componente de .

```cpp
path stem() const;
```

### <a name="remarks"></a>Observaciones

Devuelve `stem` el `myname`componente de `filename().native()` , específicamente con cualquier final `extension().native()` eliminado. El componente puede estar vacío.

## <a name="pathstring"></a><a name="string"></a>path::string

Convierte la secuencia `mypath`almacenada en .

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Observaciones

La primera función miembro (plantilla) `mypath` convierte la secuencia almacenada de la misma manera que:

1. `string()` para `string<char, Traits, Alloc>()`

1. `wstring()` para `string<wchar_t, Traits, Alloc>()`

1. `u16string()` para `string<char16_t, Traits, Alloc>()`

1. `u32string()` para `string<char32_t, Traits, Alloc>()`

La segunda función miembro convierte `mypath` la secuencia almacenada en la codificación favorecida por el `string`sistema host para una secuencia **char** y la devuelve almacenada en un objeto de tipo .

## <a name="pathstring_type"></a><a name="string_type"></a>path::string_type

El tipo es un sinónimo de `basic_string<value_type>`.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="pathswap"></a><a name="swap"></a>path::swap

Ejecuta `swap(mypath, right.mypath)`.

```cpp
void swap(path& right) noexcept;
```

## <a name="pathu16string"></a><a name="u16string"></a>path::u16string

Convierte la secuencia `mypath` almacenada en UTF-16 y la devuelve `u16string`almacenada en un objeto de tipo .

```cpp
u16string u16string() const;
```

## <a name="pathu32string"></a><a name="u32string"></a>path::u32string

Convierte la secuencia `mypath` almacenada en UTF-32 y la devuelve `u32string`almacenada en un objeto de tipo .

```cpp
u32string u32string() const;
```

## <a name="pathu8string"></a><a name="u8string"></a>path::u8string

Convierte la secuencia `mypath` almacenada en UTF-8 y la devuelve `u8string`almacenada en un objeto de tipo .

```cpp
string u8string() const;
```

## <a name="pathvalue_type"></a><a name="value_type"></a>path::value_type

El tipo describe `path` los elementos favorecidos por el sistema operativo host.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="pathwstring"></a><a name="wstring"></a>path::wstring

Convierte la secuencia `mypath` almacenada en la codificación favorecida por el sistema host para `wstring`una secuencia de **wchar_t** y la devuelve almacenada en un objeto de tipo .

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
