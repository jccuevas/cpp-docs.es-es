---
title: path (clase)
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 0bc26bb04464c52ed08d46e6a12c12cae6909d6f
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898804"
---
# <a name="path-class"></a>path (clase)

La clase path almacena un objeto de tipo `string_type`, al que se llama `myname` aquí a efectos de la exposición, adecuado para su uso como un nombre de ruta de **acceso** . `string_type` es un sinónimo de `basic_string<value_type>`, donde `value_type` es un sinónimo de **wchar_t** en Windows o **Char** en POSIX.

Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Sintaxis

```cpp
class path;
```

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[path](#path)|Construye un objeto `path`.|

### <a name="typedefs"></a>Definiciones de tipo

|Nombre de tipo|Descripción|
|-|-|
|[const_iterator](#const_iterator)|Sinónimo de `iterator`.|
|[iterator](#iterator)|Iterador constante bidireccional que designa los componentes de `path` de `myname`.|
|[string_type](#string_type)|El tipo es un sinónimo de `basic_string<value_type>`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[append](#append)|Anexa la secuencia especificada a `mypath`, convertida e inserta un preferred_separator según sea necesario.|
|[assign](#assign)|Reemplaza `mypath` con la secuencia especificada, convertida según sea necesario.|
|[begin](#begin)|Devuelve un `path::iterator` que designa el primer elemento path en el nombre de ruta de acceso, si está presente.|
|[c_str](#c_str)|Devuelve un puntero al primer carácter de `mypath`.|
|[clear](#clear)|Ejecuta `mypath.clear()`.|
|[compare](#compare)|Devuelve valores de comparación.|
|[concat](#compare)|Anexa la secuencia especificada a `mypath`, convertido (pero no insertando un separador) según sea necesario.|
|[empty](#empty)|Devuelve `mypath.empty()`.|
|[end](#end)|Devuelve un iterador de final de secuencia de tipo `iterator`.|
|[extension](#extension)|Devuelve el sufijo de `filename()`.|
|[filename](#filename)|Devuelve el componente del directorio raíz de myname, específicamente `empty() path() : *--end()`. El componente puede estar vacío.|
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
|[is_absolute](#is_absolute)|En Windows, la función devuelve `has_root_name() && has_root_directory()`. Para POSIX, la función devuelve `has_root_directory()`.|
|[is_relative](#is_relative)|Devuelve `!is_absolute()`.|
|[make_preferred](#make_preferred)|Convierte cada separador en un preferred_separator según sea necesario.|
|[native](#native)|Devuelve `myname`.|
|[parent_path](#parent_path)|Devuelve el componente de ruta de acceso principal de `myname`.|
|[preferred_separator](#preferred_separator)|El objeto constante ofrece el carácter preferido para separar los componentes de la ruta de acceso, según el sistema operativo host. |
|[relative_path](#relative_path)|Devuelve el componente de ruta de acceso relativa de `myname`. |
|[remove_filename](#remove_filename)|Quita el nombre de archivo.|
|[replace_extension](#replace_extension)|Reemplaza la extensión de `myname`. |
|[replace_filename](#replace_filename)|RReplaces el nombre de archivo.|
|[root_directory](#root_directory)|Devuelve el componente de directorio raíz de `myname`. |
|[root_name](#root_name)|Devuelve el componente de nombre raíz de `myname`. |
|[root_path](#root_path)|Devuelve el componente de ruta de acceso raíz de `myname`.|
|[stem](#stem)|Devuelve el componente de `stem` de `myname`.|
|[string](#string)|Convierte la secuencia almacenada en `mypath`.|
|[swap](#swap)|Ejecuta `swap(mypath, right.mypath)`.|
|[u16string](#u16string)|Convierte la secuencia almacenada en `mypath` en UTF-16 y la devuelve almacenada en un objeto de tipo `u16string`.|
|[u32string](#u32string)|Convierte la secuencia almacenada en `mypath` en UTF-32 y la devuelve almacenada en un objeto de tipo `u32string`.|
|[u8string](#u8string)|Convierte la secuencia almacenada en `mypath` en UTF-8 y la devuelve almacenada en un objeto de tipo `u8string`.|
|[value_type](#value_type)|El tipo describe los elementos de la ruta de acceso preferidos de sistema operativo host.|
|[wstring](#wstring)|Convierte la secuencia almacenada en `mypath` en la codificación preferida por el sistema host para una secuencia de `wchar_t` y la devuelve almacenada en un objeto de tipo `wstring`.|

### <a name="operators"></a>Operadores

|"??"|Descripción|
|-|-|
|[operator=](#op_as)|Reemplaza los elementos de la ruta de acceso por una copia de otra ruta de acceso.|
|[operator+=](#op_add)|Varias expresiones `concat`.|
|[operator/=](#op_divide)|Varias expresiones `append`.|
|[operador string_type](#op_string)|Devuelve `myname`.|

## <a name="requirements"></a>Requisitos de

**Encabezado:** \<filesystem >

**Espacio de nombres:** std::experimental::filesystem

## <a name="append"></a>Ruta de acceso:: Append

Anexa la secuencia especificada a `mypath`, convertida e inserta un `preferred_separator` según sea necesario.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Parameters

\ de *origen*
Secuencia especificada.

*primer*\
Inicio de la secuencia especificada.

*última*\
Final de la secuencia especificada.

## <a name="assign"></a>Ruta de acceso:: Assign

Reemplaza `mypath` con la secuencia especificada, convertida según sea necesario.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Parameters

\ de *origen*
Secuencia especificada.

*primer*\
Inicio de la secuencia especificada.

*última*\
Final de la secuencia especificada.

## <a name="begin"></a>Ruta de acceso:: Begin

Devuelve un `path::iterator` que designa el primer elemento path en el nombre de ruta de acceso, si está presente.

```cpp
iterator begin() const;
```

## <a name="c_str"></a>Ruta de acceso:: c_str

Devuelve un puntero al primer carácter de `mypath`.

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="clear"></a>Ruta de acceso:: Clear

Ejecuta `mypath.clear()`.

```cpp
void clear() noexcept;
```

## <a name="compare"></a>Ruta de acceso:: Compare

La primera función devuelve `mypath.compare(pval.native())`. La segunda función devuelve `mypath.compare(str)`. La tercera función devuelve `mypath.compare(ptr)`.

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parameters

*pval*\
Ruta de acceso que se va a comparar.

\ *Str*
Cadena que se va a comparar.

\ *ptr*
Puntero que se va a comparar.

## <a name="concat"></a>path:: concat

Anexa la secuencia especificada a `mypath`, convertido (pero no insertando un separador) según sea necesario.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Parameters

\ de *origen*
Secuencia especificada.

*primer*\
Inicio de la secuencia especificada.

*última*\
Final de la secuencia especificada.

## <a name="const_iterator"></a>Ruta de acceso:: const_iterator

Sinónimo de `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a>Ruta de acceso:: vacío

Devuelve `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="end"></a>Ruta de acceso:: end

Devuelve un iterador de final de secuencia de tipo `iterator`.

```cpp
iterator end() const;
```

## <a name="extension"></a>Ruta de acceso:: Extension

Devuelve el sufijo de `filename()`.

```cpp
path extension() const;
```

### <a name="remarks"></a>Notas

Devuelve el sufijo de `filename() X` tal que:

Si `X == path(".") || X == path("..")` o si `X` no contiene ningún punto, el sufijo está vacío.

De lo contrario, el sufijo comienza con (e incluye) el punto situado más al derecha.

## <a name="filename"></a>path:: FILENAME

Devuelve el componente del directorio raíz de myname, específicamente `empty() path() : *--end()`. El componente puede estar vacío.

```cpp
path filename() const;
```

## <a name="generic_string"></a>Ruta de acceso:: generic_string

Devuelve `this->string<Elem, Traits, Alloc>(al)` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="generic_u16string"></a>Ruta de acceso:: generic_u16string

Devuelve `u16string()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

```cpp
u16string generic_u16string() const;
```

## <a name="generic_u32string"></a>Ruta de acceso:: generic_u32string

Devuelve `u32string()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

```cpp
u32string generic_u32string() const;
```

## <a name="generic_u8string"></a>Ruta de acceso:: generic_u8string

Devuelve `u8string()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

```cpp
string generic_u8string() const;
```

## <a name="generic_wstring"></a>Ruta de acceso:: generic_wstring

Devuelve `wstring()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

```cpp
wstring generic_wstring() const;
```

## <a name="has_extension"></a>Ruta de acceso:: has_extension

Devuelve `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a>Ruta de acceso:: has_filename

Devuelve `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a>Ruta de acceso:: has_parent_path

Devuelve `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a>Ruta de acceso:: has_relative_path

Devuelve `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a> path::has_root_directory

Devuelve `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a>Ruta de acceso:: has_root_name

Devuelve `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a>Ruta de acceso:: has_root_path

Devuelve `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a>Ruta de acceso:: has_stem

Devuelve `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a>Ruta de acceso:: is_absolute

En Windows, la función devuelve `has_root_name() && has_root_directory()`. Para POSIX, la función devuelve `has_root_directory()`.

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a>Ruta de acceso:: is_relative

Devuelve `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="iterator"></a>path:: iterator

Iterador constante bidireccional que designa los componentes de la ruta de acceso de `myname`.

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

### <a name="remarks"></a>Notas

La clase describe un iterador constante bidireccional que designa los componentes de `path` de `myname` en la secuencia:

1. el nombre de raíz, si está presente

1. el directorio raíz, si está presente

1. los elementos restantes del directorio del `path`primario, si están presentes, que terminan con el nombre de archivo, si está presente.

Para `pval` un objeto de tipo `path`:

1. `path::iterator X = pval.begin()` designa el primer elemento `path` en el nombre de ruta, si está presente.

1. `X == pval.end()` es true cuando `X` apunta justo después del final de la secuencia de componentes.

3. `*X` devuelve una cadena que coincide con el componente actual

1. `++X` designa el componente siguiente de la secuencia, si está presente.

1. `--X` designa el componente anterior de la secuencia, si existe.

1. La modificación de `myname` invalida todos los iteradores que designan elementos en `myname`.

## <a name="make_preferred"></a>Ruta de acceso:: make_preferred

Convierte cada separador en un `preferred_separator` según sea necesario.

```cpp
path& make_preferred();
```

## <a name="native"></a>Ruta de acceso:: nativo

Devuelve `myname`.

```cpp
const string_type& native() const noexcept;
```

## <a name="op_as"></a>path:: Operator =

Reemplaza los elementos de la ruta de acceso por una copia de otra ruta de acceso.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Parameters

\ *derecha*
La [ruta de acceso](../standard-library/path-class.md) que se copia en el `path`.

\ de *origen*
Ruta de acceso de origen.

### <a name="remarks"></a>Notas

El primer operador miembro copia `right.myname` en `myname`. El segundo operador miembro mueve `right.myname` a `myname`. El tercer operador miembro se comporta igual que `*this = path(source)`.

## <a name="op_add"></a>path:: Operator + =

Varias expresiones `concat`.

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

### <a name="parameters"></a>Parameters

\ *derecha*
La ruta de acceso agregada.

\ *Str*
Cadena agregada.

\ *ptr*
El puntero agregado.

\ *Elem*
`value_type` o `Elem`agregados.

\ de *origen*
El origen agregado.

### <a name="remarks"></a>Notas

Las funciones miembro se comportan igual que las siguientes expresiones correspondientes:

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="op_divide"></a>path:: Operator/=

Varias expresiones `append`.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Parameters

\ *derecha*
La ruta de acceso agregada.

\ de *origen*
El origen agregado.

### <a name="remarks"></a>Notas

Las funciones miembro se comportan igual que las siguientes expresiones correspondientes:

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a>path:: Operator string_type

Devuelve `myname`.

```cpp
operator string_type() const;
```

## <a name="parent_path"></a>Ruta de acceso::p arent_path

Devuelve el componente de ruta de acceso principal de `myname`.

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Notas

Devuelve el componente de ruta de acceso primaria de `myname`, específicamente el prefijo de `myname` después de quitar `filename().native()` y cualquier separador de directorio inmediatamente anterior. (Igualmente, si `begin() != end()`, es la combinación de todos los elementos del intervalo `[begin(), --end())` aplicando sucesivamente `operator/=`). El componente puede estar vacío.

## <a name="path"></a>Ruta de acceso::p gistro

Crea una `path` de varias maneras.

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

### <a name="parameters"></a>Parameters

\ *derecha*
Ruta de acceso de la que la ruta de acceso construida va a ser una copia.

\ de *origen*
Origen del que la ruta de acceso construida va a ser una copia.

\ *Loc*
Configuración regional especificada.

*primer*\
Posición del primer elemento que se va a copiar.

*última*\
Posición del último elemento que se va a copiar.

### <a name="remarks"></a>Notas

Todos los constructores construyen `myname` de varias maneras:

Por `path()` se `myname()`.

Por `path(const path& right`) es `myname(right.myname)`.

Por `path(path&& right)` se `myname(right.myname)`.

Por `template<class Source> path(const Source& source)` se `myname(source)`.

Por `template<class Source> path(const Source& source, const locale& loc)` se `myname(source)`, obteniendo cualquier aspecto de codecvt necesario de `loc`.

Por `template<class InIt> path(InIt first, InIt last)` se `myname(first, last)`.

Por `template<class InIt> path(InIt first, InIt last, const locale& loc)` se `myname(first, last)`, obteniendo cualquier aspecto de codecvt necesario de `loc`.

## <a name="preferred_separator"></a> path::preferred_separator

El objeto constante ofrece el carácter preferido para separar los componentes de la ruta de acceso, según el sistema operativo host.

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume POSIX
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>Notas

Tenga en cuenta que en la mayoría de los contextos en Windows también se permite usar L '/' en su lugar.

## <a name="relative_path"></a>Ruta de acceso:: relative_path

Devuelve el componente de ruta de acceso relativa de `myname`.

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Notas

Devuelve el componente de ruta de acceso relativa de `myname`, específicamente el sufijo de `myname` después de quitar `root_path().native()` y cualquier separador de directorio redundante inmediatamente posterior. El componente puede estar vacío.

## <a name="remove_filename"></a>Ruta de acceso:: remove_filename

Quita el nombre de archivo.

```cpp
path& remove_filename();
```

## <a name="replace_extension"></a>Ruta de acceso:: replace_extension

Reemplaza la extensión de `myname`.

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Parameters

\ *newext*
La nueva extensión.

### <a name="remarks"></a>Notas

En primer lugar, quita el sufijo `extension().native()` de `myname`. Después, si `!newext.empty() && newext[0] != dot` (donde se `*path(".").c_str()``dot`), se anexa `dot` a `myname`. A continuación, se anexa *newext* a `myname`.

## <a name="replace_filename"></a>Ruta de acceso:: replace_filename

Reemplaza el nombre de archivo.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>Parameters

*pval*\
Ruta de acceso del nombre de archivo.

### <a name="remarks"></a>Notas

La función miembro ejecuta:

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="root_directory"></a> path::root_directory

Devuelve el componente de directorio raíz de `myname`.

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Notas

El componente puede estar vacío.

## <a name="root_name"></a>Ruta de acceso:: root_name

Devuelve el componente de nombre raíz de `myname`.

```cpp
path root_name() const;
```

### <a name="remarks"></a>Notas

El componente puede estar vacío.

## <a name="root_path"></a>Ruta de acceso:: root_path

Devuelve el componente de ruta de acceso raíz de `myname`.

```cpp
path root_path() const;
```

### <a name="remarks"></a>Notas

Devuelve el componente de ruta de acceso raíz de `myname`, específicamente `root_name()` / `root_directory`. El componente puede estar vacío.

## <a name="stem"></a>Ruta de acceso:: tallo

Devuelve el componente de `stem` de `myname`.

```cpp
path stem() const;
```

### <a name="remarks"></a>Notas

Devuelve el componente de `stem` de `myname`, en concreto `filename().native()` con cualquier `extension().native()` que se quite al final. El componente puede estar vacío.

## <a name="string"></a>path:: String

Convierte la secuencia almacenada en `mypath`.

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Notas

La primera función miembro (plantilla) convierte la secuencia almacenada en `mypath` de la misma manera que:

1. `string()` para `string<char, Traits, Alloc>()`

1. `wstring()` para `string<wchar_t, Traits, Alloc>()`

1. `u16string()` para `string<char16_t, Traits, Alloc>()`

1. `u32string()` para `string<char32_t, Traits, Alloc>()`

La segunda función miembro convierte la secuencia almacenada en `mypath` a la codificación preferida por el sistema host para una secuencia **Char** y la devuelve almacenada en un objeto de tipo `string`.

## <a name="string_type"></a>Ruta de acceso:: string_type

El tipo es un sinónimo de `basic_string<value_type>`.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="swap"></a>path:: swap

Ejecuta `swap(mypath, right.mypath)`.

```cpp
void swap(path& right) noexcept;
```

## <a name="u16string"></a>Ruta de acceso:: u16string

Convierte la secuencia almacenada en `mypath` en UTF-16 y la devuelve almacenada en un objeto de tipo `u16string`.

```cpp
u16string u16string() const;
```

## <a name="u32string"></a>Ruta de acceso:: u32string

Convierte la secuencia almacenada en `mypath` en UTF-32 y la devuelve almacenada en un objeto de tipo `u32string`.

```cpp
u32string u32string() const;
```

## <a name="u8string"></a>Ruta de acceso:: u8string

Convierte la secuencia almacenada en `mypath` en UTF-8 y la devuelve almacenada en un objeto de tipo `u8string`.

```cpp
string u8string() const;
```

## <a name="value_type"></a>Ruta de acceso:: value_type

El tipo describe los elementos de `path` que el sistema operativo host favorece.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a>Ruta de acceso:: wstring

Convierte la secuencia almacenada en `mypath` en la codificación preferida por el sistema host para una secuencia de **wchar_t** y la devuelve almacenada en un objeto de tipo `wstring`.

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
