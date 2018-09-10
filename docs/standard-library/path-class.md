---
title: path (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::path
dev_langs:
- C++
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4559bec84d7e6051155ad73f68a1ef8ae13ca6cc
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104165"
---
# <a name="path-class"></a>path (Clase)

La clase **path** almacena un objeto de tipo string\_type, denominado myname aquí a efectos de la exposición, que se puede usar como una ruta de acceso. string\_type es un sinónimo de basic\_string\<value_type>, donde value\_type es un sinónimo de char en Windows o wchar_t en Posix.

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

|Nombre de tipo|Descripción|
|-|-|
|[const_iterator](#const_iterator)|Sinónimo de `iterator`.|
|[iterator](#iterator)|Un iterador constante bidireccional que designa el `path` componentes de `myname`.|
|[string_type](#string_type)|El tipo es un sinónimo de `basic_string<value_type>`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[append](#append)|Anexa la secuencia especificada a `mypath`, convertida e insertan un preferred_separator según sea necesario.|
|[assign](#assign)|Reemplaza `mypath` con la secuencia especificada, convertida según sea necesario.|
|[begin](#begin)|Devuelve un `path::iterator` que designa el primer elemento de ruta de acceso de la ruta de acceso, si está presente.|
|[c_str](#c_str)|Devuelve un puntero al primer carácter en `mypath`.|
|[clear](#clear)|Ejecuta `mypath.clear()`.|
|[compare](#compare)|Devuelve los valores de comparación.|
|[concat](#compare)|Anexa la secuencia especificada a `mypath`, convertir (pero no insertan un preferred_separator) según sea necesario.|
|[empty](#empty)|Devuelve `mypath.empty()`.|
|[end](#end)|Devuelve un iterador de final de secuencia de tipo `iterator`.|
|[Extensión](#extension)|Devuelve el sufijo de `filename()`.|
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
|[is_absolute](#is_absolute)|Para Windows, la función devuelve `has_root_name() && has_root_directory()`. Para Posix, la función devuelve `has_root_directory()`.|
|[is_relative.](#is_relative)|Devuelve `!is_absolute()`.|
|[make_preferred](#make_preferred)|Convierte cada separador en un preferred_separator según sea necesario.|
|[native](#native)|Devuelve `myname`.|
|[parent_path](#parent_path)|Devuelve el elemento primario de componente de ruta de acceso de `myname`.|
|[preferred_separator](#preferred_separator)|El objeto constante ofrece el carácter preferido para separar los componentes de la ruta de acceso, según el sistema operativo host. |
|[RELATIVE_PATH](#relative_path)|Devuelve el componente de ruta de acceso relativa de `myname`. |
|[remove_filename](#remove_filename)|Quita el nombre de archivo.|
|[replace_extension)](#replace_extension)|Reemplaza la extensión de `myname`. |
|[replace_filename](#replace_filename)|RReplaces el nombre de archivo.|
|[root_directory](#root_directory)|Devuelve el componente del directorio raíz de `myname`. |
|[root_name](#root_name)|Devuelve el componente de nombre de raíz de `myname`. |
|[root_path](#root_path)|Devuelve el componente de ruta de acceso raíz de `myname`.|
|[stem](#stem)|Devuelve el `stem` componente de `myname`.|
|[string](#string)|Convierte la secuencia almacenada en `mypath`.|
|[swap](#swap)|Ejecuta `swap(mypath, right.mypath)`.|
|[u16string](#u16string)|Convierte la secuencia almacenada en `mypath` UTF-16 y la devuelve almacenada en un objeto de tipo `u16string`.|
|[u32string](#u32string)|Convierte la secuencia almacenada en `mypath` UTF-32 y la devuelve almacenada en un objeto de tipo `u32string`.|
|[u8string](#u8string)|Convierte la secuencia almacenada en `mypath` a UTF-8 y la devuelve almacenada en un objeto de tipo `u8string`.|
|[value_type](#value_type)|El tipo describe los elementos de la ruta de acceso preferidos de sistema operativo host.|
|[wstring](#wstring)|Convierte la secuencia almacenada en `mypath` a la codificación preferida por el sistema host para un `wchar_t` secuencia y la devuelve almacenada en un objeto de tipo `wstring`.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator=](#op_as)|Reemplaza los elementos de la ruta de acceso con una copia de otra ruta de acceso.|
|[operator+=](#op_add)|Diversos `concat` expresiones.|
|[operator/=](#op_divide)|Diversos `append` expresiones.|
|[string_type (operador)](#op_string)|Devuelve `myname`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<filesystem >

**Espacio de nombres:** std::experimental::filesystem

## <a name="append"></a> Path:: Append

Anexa la secuencia especificada a `mypath`, convertido e insertar un `preferred_separator` según sea necesario.

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>Parámetros

*source*<br/>
Secuencia especificada.

*first*<br/>
Inicio de la secuencia especificada.

*Último*<br/>
Final de la secuencia especificada.

## <a name="assign"></a> Path::Assign

Reemplaza `mypath` con la secuencia especificada, convertida según sea necesario.

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>Parámetros

*source*<br/>
Secuencia especificada.

*first*<br/>
Inicio de la secuencia especificada.

*Último*<br/>
Final de la secuencia especificada.

## <a name="begin"></a> Path:: begin

Devuelve un `path::iterator` que designa el primer elemento de ruta de acceso de la ruta de acceso, si está presente.

```cpp
iterator begin() const;
```

## <a name="c_str"></a> Path::c_str

Devuelve un puntero al primer carácter en `mypath`.

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="clear"></a> Path::Clear

Ejecuta `mypath.clear()`.

```cpp
void clear() noexcept;
```

## <a name="compare"></a> Path:: Compare

La primera función devuelve `mypath.compare(pval.native())`. La segunda función devuelve `mypath.compare(str)`. La tercera función devuelve `mypath.compare(ptr)`.

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parámetros

*PVal*<br/>
Ruta de acceso para comparar.

*str*<br/>
Cadena que se va a comparar.

*ptr*<br/>
Puntero a comparar.

## <a name="concat"></a> Path::Concat

Anexa la secuencia especificada a `mypath`, convertir (pero no insertan un preferred_separator) según sea necesario.

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>Parámetros

*source*<br/>
Secuencia especificada.

*first*<br/>
Inicio de la secuencia especificada.

*Último*<br/>
Final de la secuencia especificada.

## <a name="const_iterator"></a> Path::const_iterator

Sinónimo de `iterator`.

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a> Path:: Empty

Devuelve `mypath.empty()`.

```cpp
bool empty() const noexcept;
```

## <a name="end"></a> Path:: end

Devuelve un iterador de final de secuencia de tipo `iterator`.

```cpp
iterator end() const;
```

## <a name="extension"></a> Path:: Extension

Devuelve el sufijo de `filename()`.

```cpp
path extension() const;
```

### <a name="remarks"></a>Comentarios

Devuelve el sufijo de `filename() X` tal que:

Si `X == path(".") || X == path("..")` o si `X` no contiene ningún punto, el sufijo está vacío.

De lo contrario, el sufijo comienza con (e incluye) el punto situado más al derecha.

## <a name="filename"></a> Path:: filename

Devuelve el componente del directorio raíz de myname, específicamente `empty() path() : *--end()`. El componente puede estar vacío.

```cpp
path filename() const;
```

## <a name="generic_string"></a> Path::generic_string

Devuelve `this->string<Elem, Traits, Alloc>(al)` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="generic_u16string"></a> Path::generic_u16string

Devuelve `u16string()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

```cpp
u16string generic_u16string() const;
```

## <a name="generic_u32string"></a> Path::generic_u32string

Devuelve `u32string()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

```cpp
u32string generic_u32string() const;
```

## <a name="generic_u8string"></a> Path::generic_u8string

Devuelve `u8string()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

```cpp
string generic_u8string() const;
```

## <a name="generic_wstring"></a> Path::generic_wstring

Devuelve `wstring()` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

```cpp
wstring generic_wstring() const;
```

## <a name="has_extension"></a> Path::has_extension

Devuelve `!extension().empty()`.

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a> Path::has_filename

Devuelve `!filename().empty()`.

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a> Path:: has_parent_path

Devuelve `!parent_path().empty()`.

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a> Path::has_relative_path

Devuelve `!relative_path().empty()`.

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a> Path::has_root_directory

Devuelve `!root_directory().empty()`.

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a> Path:: has_root_name

Devuelve `!root_name().empty()`.

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a> Path:: has_root_path

Devuelve `!root_path().empty()`.

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a> Path::has_stem

Devuelve `!stem().empty()`.

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a> Path::is_absolute

Para Windows, la función devuelve `has_root_name() && has_root_directory()`. Para Posix, la función devuelve `has_root_directory()`.

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a> Path::is_relative

Devuelve `!is_absolute()`.

```cpp
bool is_relative() const;
```

## <a name="iterator"></a> Path:: Iterator

Un iterador constante bidireccional que designa los componentes de ruta de acceso de `myname`.

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

### <a name="remarks"></a>Comentarios

La clase describe un iterador constante bidireccional que designa el `path` componentes de `myname` en la secuencia:

1. el nombre de raíz, si está presente

1. el directorio raíz, si está presente

1. los elementos restantes del directorio del elemento primario `path`, si está presente, terminan con el nombre de archivo, si está presente

Para `pval` un objeto de tipo `path`:

1. `path::iterator X = pval.begin()` designa el primer `path` elemento en la ruta de acceso, si está presente.

1. `X == pval.end()` es true cuando `X` puntos inmediatamente después del final de la secuencia de componentes.

3. `*X` Devuelve una cadena que coincide con el componente actual

1. `++X` designa el componente siguiente de la secuencia, si está presente.

1. `--X` designa el componente anterior de la secuencia, si existe.

1. Modificar `myname` invalida todos los iteradores que designan elementos en `myname`.

## <a name="make_preferred"></a> Path::make_preferred

Convierte cada separador en un preferred_separator según sea necesario.

```cpp
path& make_preferred();
```

## <a name="native"></a> Path::Native

Devuelve `myname`.

```cpp
const string_type& native() const noexcept;
```

## <a name="op_as"></a> Path:: operator =

Reemplaza los elementos de la ruta de acceso con una copia de otra ruta de acceso.

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El [ruta](../standard-library/path-class.md) que se copia en el `path`.

*source*<br/>
La ruta de acceso de origen.

### <a name="remarks"></a>Comentarios

Las copias de operador miembro primera `right.myname` a `myname`. El segundo operador miembro mueve `right.myname` a `myname`. El tercer operador miembro comporta igual que `*this = path(source)`.

## <a name="op_add"></a> Path:: operator +=

Diversos `concat` expresiones.

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

*right*<br/>
La ruta de acceso se ha agregado.

*str*<br/>
La cadena se ha agregado.

*ptr*<br/>
El puntero se ha agregado.

*Elem*<br/>
Agregado `value_type` o `Elem`.

*source*<br/>
El origen se ha agregado.

### <a name="remarks"></a>Comentarios

Las funciones miembro se comportan igual que las siguientes expresiones correspondientes:

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string\<Elem>(1, elem)));`

## <a name="op_divide"></a> Path:: operator / =

Diversos `append` expresiones.

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
La ruta de acceso se ha agregado.

*source*<br/>
El origen se ha agregado.

### <a name="remarks"></a>Comentarios

Las funciones miembro se comportan igual que las siguientes expresiones correspondientes:

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a> Path:: operator string_type

Devuelve `myname`.

```cpp
operator string_type() const;
```

## <a name="parent_path"></a> Path::parent_path

Devuelve el elemento primario de componente de ruta de acceso de `myname`.

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Comentarios

Devuelve el elemento primario de componente de ruta de acceso de `myname`, específicamente el prefijo de `myname` después de quitar `filename().native()` y los separadores de directorio inmediatamente anterior. (Igualmente, si `begin() != end()`, es la combinación de todos los elementos en el intervalo [funciones begin() Begin (), aplicando consecutivamente operador / =.) El componente puede estar vacío.

## <a name="path"></a> Path:: path

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

*right*<br/>
La ruta de acceso de los cuales la ruta de acceso construido va a ser una copia.

*source*<br/>
El origen del que la ruta de acceso construido es a ser una copia.

*LOC*<br/>
La configuración regional especificada.

*first*<br/>
Posición del primer elemento que se va a copiar.

*Último*<br/>
La posición del último elemento que se va a copiar.

### <a name="remarks"></a>Comentarios

Los constructores todos construcción `myname` de varias maneras:

Para `path()` es `myname()`.

Para `path(const path& right`) es `myname(right.myname)`.

Para `path(path&& right)` es `myname(right.myname)`.

Para `template<class Source> path(const Source& source)` es `myname(source)`.

Para `template<class Source> path(const Source& source, const locale& loc)` es `myname(source)`, obtiene cualquier codecvt necesaria de `loc`.

Para `template<class InIt> path(InIt first, InIt last)` es `myname(first, last)`.

Para `template<class InIt> path(InIt first, InIt last, const locale& loc)` es `myname(first, last)`, obtiene cualquier codecvt necesaria de `loc`.

## <a name="preferred_separator"></a> Path::preferred_separator

El objeto constante ofrece el carácter preferido para separar los componentes de la ruta de acceso, según el sistema operativo host. 

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume Posix
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>Comentarios

Tenga en cuenta que en la mayoría de los contextos en Windows también se permite usar L '/' en su lugar.

## <a name="relative_path"></a> Path:: RELATIVE_PATH

Devuelve el componente de ruta de acceso relativa de `myname`. 

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Comentarios

Devuelve el componente de ruta de acceso relativa de `myname`, específicamente el sufijo de `myname` después de quitar `root_path().native()` y los separadores de directorio redundantes inmediatamente posteriores. El componente puede estar vacío.

## <a name="remove_filename"></a> Path:: remove_filename

Quita el nombre de archivo.

```cpp
path& remove_filename();
```

## <a name="replace_extension"></a> Path::replace_extension

Reemplaza la extensión de `myname`. 

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>Parámetros

*newext*<br/>
La nueva extensión.

### <a name="remarks"></a>Comentarios

Quita primero el sufijo `extension().native()` desde `myname`. A continuación si `!newext.empty() && newext[0] != dot` (donde `dot` es `*path(".").c_str()`), a continuación, `dot` se anexa a `myname`. A continuación, `newext` se anexa a `myname`.

## <a name="replace_filename"></a> Path:: replace_filename

Reemplaza el nombre de archivo.

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>Parámetros

*PVal*<br/>
La ruta de acceso del nombre de archivo.

### <a name="remarks"></a>Comentarios

La función miembro ejecuta:

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="root_directory"></a> Path:: root_directory

Devuelve el componente del directorio raíz de `myname`. 

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Comentarios

El componente puede estar vacío.

## <a name="root_name"></a> Path:: root_name

Devuelve el componente de nombre de raíz de `myname`. 

```cpp
path root_name() const;
```

### <a name="remarks"></a>Comentarios

El componente puede estar vacío.

## <a name="root_path"></a> Path:: root_path

Devuelve el componente de ruta de acceso raíz de `myname`.

```cpp
path root_path() const;
```

### <a name="remarks"></a>Comentarios

Devuelve el componente de ruta de acceso raíz de `myname`, específicamente root_name () / root_directory. El componente puede estar vacío.

## <a name="stem"></a> Path::stem

Devuelve el `stem` componente de `myname`.

```cpp
path stem() const;
```

### <a name="remarks"></a>Comentarios

Devuelve el `stem` componente de `myname`, concretamente `filename().native()` con cualquier finales `extension().native()` quitado. El componente puede estar vacío.

## <a name="string"></a> Path:: String

Convierte la secuencia almacenada en `mypath`.

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Comentarios

La primera función miembro (template) convierte la secuencia almacenada en mypath del mismo modo que:

1. `string()` para `string<char, Traits, Alloc>()`

1. `wstring()` para `string<wchar_t, Traits, Alloc>()`

1. `u16string()` para `string<char16_t, Traits, Alloc>()`

1. `u32string()` para `string<char32_t, Traits, Alloc>()`

La segunda función miembro convierte la secuencia almacenada en `mypath` a la codificación preferida por el sistema host para una secuencia char y devuelve almacenada en un objeto de tipo cadena.

## <a name="string_type"></a> Path::STRING_TYPE

El tipo es un sinónimo de `basic_string<value_type>`.

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="swap"></a> Path:: swap

Ejecuta `swap(mypath, right.mypath)`.

```cpp
void swap(path& right) noexcept;
```

## <a name="u16string"></a> Path::u16string

Convierte la secuencia almacenada en `mypath` UTF-16 y la devuelve almacenada en un objeto de tipo `u16string`.

```cpp
u16string u16string() const;
```

## <a name="u32string"></a> Path::u32string

Convierte la secuencia almacenada en `mypath` UTF-32 y la devuelve almacenada en un objeto de tipo `u32string`.

```cpp
u32string u32string() const;
```

## <a name="u8string"></a> Path::u8string

Convierte la secuencia almacenada en `mypath` a UTF-8 y la devuelve almacenada en un objeto de tipo `u8string`.

```cpp
string u8string() const;
```

## <a name="value_type"></a> Path::value_type

El tipo describe los elementos de la ruta de acceso preferidos de sistema operativo host.

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume Posix
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a> Path::wstring

Convierte la secuencia almacenada en `mypath` a la codificación preferida por el sistema host para un `wchar_t` secuencia y la devuelve almacenada en un objeto de tipo `wstring`.

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
