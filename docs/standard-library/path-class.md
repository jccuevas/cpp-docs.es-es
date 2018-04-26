---
title: path (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::path
dev_langs:
- C++
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 12e342baa69a0fa9b354d1eac7890f5c38637c1b
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="path-class"></a>path (Clase)

La clase **path** almacena un objeto de tipo string\_type, denominado myname aquí a efectos de la exposición, que se puede usar como una ruta de acceso. string\_type es un sinónimo de basic\_string\<value_type>, donde value\_type es un sinónimo de char en Windows o wchar_t en Posix.

Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos (C++)](../standard-library/file-system-navigation.md).

## <a name="syntax"></a>Sintaxis

```cpp
class path;
```

## <a name="pathappend"></a>path::append

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

Las funciones miembro anexan la secuencia especificada a mypath convertida e insertan un preferred_separator según sea necesario.

## <a name="pathassign"></a>path::assign

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

Las funciones miembro reemplazan mypath con la secuencia especificada, convertida según sea necesario.

## <a name="pathbegin"></a>path::begin

```cpp
iterator begin() const;
```

Devuelve un path::iterator que designa el primer elemento de la ruta de acceso del nombre de ruta de acceso, si está presente.

## <a name="pathcstr"></a>path::c_str

```cpp
const value_type& *c_str() const noexcept;
```

Devuelve un puntero al primer carácter de mypath.

## <a name="pathclear"></a>path::clear

```cpp
void clear() noexcept;
```

La función miembro ejecuta mypath.clear()

## <a name="pathcompare"></a>path::compare

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

La primera función devuelve mypath.compare(pval.native()). La segunda función devuelve mypath.compare(str). La tercera función devuelve mypath.compare(ptr).

## <a name="pathconcat"></a>path::concat

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

Las funciones miembro anexan la secuencia especificada a mypath, convertida según sea necesario (pero no insertan un preferred_separator).

## <a name="pathconstiterator"></a>path::const_iterator

```cpp
typedef iterator const_iterator;
```

El tipo es un sinónimo de iterador.

## <a name="pathempty"></a>path::empty

```cpp
bool empty() const noexcept;
```

Devuelve mypath.empty().

## <a name="pathend"></a>path::end

```cpp
iterator end() const;
```

Devuelve un iterador de final de secuencia de tipo iterador.

## <a name="pathextension"></a>path::extension

```cpp
path extension() const;
```

Devuelve el sufijo de filename() X tal que:

Si X == path(".") &#124;&#124; X == path("..") o si X no contiene ningún punto, el sufijo está vacío.

De lo contrario, el sufijo comienza con (e incluye) el punto situado más al derecha.

## <a name="pathfilename"></a>path::filename

```cpp
path filename() const;
```

Devuelve el componente del directorio raíz de myname, específicamente `empty()  path() : *--end()`. El componente puede estar vacío.

## <a name="pathgenericstring"></a>path::generic_string

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

Devuelve `this->string<Elem, Traits, Alloc>(al)` con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

## <a name="pathgenericu16string"></a>path::generic_u16string

```cpp
u16string generic_u16string() const;
```

Devuelve u16string() con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

## <a name="pathgenericu32string"></a>path::generic_u32string

```cpp
u32string generic_u32string() const;
```

Devuelve u32string() con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

## <a name="pathgenericu8string"></a>path::generic_u8string

```cpp
string generic_u8string() const;
```

Devuelve u8string() con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

## <a name="pathgenericwstring"></a>path::generic_wstring

```cpp
wstring generic_wstring() const;
```

Devuelve wstring() con (en Windows) cualquier barra diagonal inversa convertida en una barra diagonal.

## <a name="pathhasextension"></a>path::has_extension

```cpp
bool has_extension() const;
```

Devuelve !extension().empty().

## <a name="pathhasfilename"></a>path::has_filename

```cpp
bool has_filename() const;
```

Devuelve !filename().empty().

## <a name="pathhasparentpath"></a>path::has_parent_path

```cpp
bool has_parent_path() const;
```

Devuelve !parent_path().empty().

## <a name="pathhasrelativepath"></a>path::has_relative_path

```cpp
bool has_relative_path() const;
```

Devuelve !relative_path().empty().

## <a name="pathhasrootdirectory"></a>path::has_root_directory

```cpp
bool has_root_directory() const;
```

Devuelve !root_directory().empty().

## <a name="pathhasrootname"></a>path::has_root_name

```cpp
bool has_root_name() const;
```

Devuelve !root_name().empty().

## <a name="pathhasrootpath"></a>path::has_root_path

```cpp
bool has_root_path() const;
```

Devuelve !root_path().empty().

## <a name="pathhasstem"></a>path::has_stem

```cpp
bool has_stem() const;
```

Devuelve !stem().empty().

## <a name="pathisabsolute"></a>path::is_absolute

```cpp
bool is_absolute() const;
```

Para Windows, la función devuelve has_root_name() && has_root_directory(). Para Posix, la función devuelve has_root_directory().

## <a name="pathisrelative"></a>path::is_relative

```cpp
bool is_relative() const;
```

Devuelve !is_absolute().

## <a name="pathiterator"></a>path::iterator

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

La clase describe un iterador constante bidireccional que designa los componentes de la ruta de acceso de myname en la secuencia:

1. el nombre de raíz, si está presente

1. el directorio raíz, si está presente

1. los elementos restantes del directorio de la ruta de acceso principal, si está presente, que terminan con el nombre de archivo, si está presente

Para pval, un objeto de tipo path:

1. path::iterator X = pval.begin() designa el primer elemento de la ruta de acceso en el nombre de ruta de acceso, si está presente.

1. X == pval.end() es true cuando X apunta inmediatamente después del final de la secuencia de componentes.

3. *X devuelve una cadena que coincide con el componente actual.

1. ++X designa el próximo componente de la secuencia, si está presente.

1. --X designa el componente anterior de la secuencia, si existe.

1. Al modificar myname, se invalidan todos los iteradores que designan elementos en myname.

## <a name="pathmakepreferred"></a>path::make_preferred

```cpp
path& make_preferred();
```

La función miembro convierte cada separador en un preferred_separator según sea necesario.

## <a name="pathnative"></a>path::native

```cpp
const string_type& native() const noexcept;
```

Devuelve myname.

## <a name="pathoperator"></a>path::operator=

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

El primer operador miembro copia right.myname a myname. El segundo operador miembro mueve right.myname a myname. El tercer operador miembro se comporta igual que *this = path(source).

## <a name="pathoperator"></a>path::operator+=

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

Las funciones miembro se comportan igual que las siguientes expresiones correspondientes:

1. concat(right);

1. concat(path(str));

1. concat(ptr);

1. concat(string_type(1, elem));

1. concat(source);

1. concat(path(basic_string\<Elem>(1, elem)));

## <a name="pathoperator"></a>path::operator/=

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

Las funciones miembro se comportan igual que las siguientes expresiones correspondientes:

1. append(right);

1. append(source);

## <a name="pathoperator-stringtype"></a>path::operator string_type

```cpp
operator string_type() const;
```

El operador miembro devuelve myname.

## <a name="pathparentpath"></a>path::parent_path

```cpp
path parent_path() const;
```

Devuelve el componente principal de ruta de acceso de myname, específicamente el prefijo de myname después de quitar filename().native() y los separadores de directorio inmediatamente anteriores. (Igualmente, si funciones begin()! = end(), es la combinación de todos los elementos en el intervalo [funciones begin(),--end()) aplicando consecutivamente operador / =.) El componente puede estar vacío.

## <a name="pathpath"></a>path::path

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

Todos los constructores crean myname de varias maneras:

Para path(), es myname().

Para path(const path& right), es myname(right.myname).

Para path(path&& right), es myname(right.myname).

Para template\<class Source> path(const Source& source), es myname(source).

Para template\<class Source> path(const Source& source, const locale& loc), es myname(source), que obtiene cualquier faceta codecvt necesaria de loc.

Para template\<class InIt> path(InIt first, InIt last), es myname(first, last).

Para template\<class InIt> path(InIt first, InIt last, const locale& loc), es myname(first, last), que obtiene cualquier faceta codecvt necesaria de loc.

## <a name="pathpreferredseparator"></a>path::preferred_separator

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume Posix
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

El objeto constante ofrece el carácter preferido para separar los componentes de la ruta de acceso, según el sistema operativo host. Tenga en cuenta que en la mayoría de los contextos en Windows también se permite usar L '/' en su lugar.

## <a name="pathrelativepath"></a>path::relative_path

```cpp
path relative_path() const;
```

Devuelve el componente de ruta de acceso relativa de myname, específicamente el sufijo de myname después de quitar root_path().native() y los separadores de directorio redundantes inmediatamente posteriores. El componente puede estar vacío.

## <a name="pathremovefilename"></a>path::remove_filename

```cpp
path& remove_filename();
```

## <a name="pathreplaceextension"></a>path::replace_extension

```cpp
path& replace_extension(const path& newext = path());
```

La función miembro quita primero el sufijo extension().native() de myname. Entonces si !newext.empty() && newext[0] != dot [donde dot es *path(".").c_str()], dot se anexa a myname. A continuación, se anexa newext a myname.

## <a name="pathreplacefilename"></a>path::replace_filename

```cpp
path& replace_filename(const path& pval);
```

La función miembro ejecuta:

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="pathrootdirectory"></a>path::root_directory

```cpp
path root_directory() const;
```

Devuelve el componente de directorio raíz de myname. El componente puede estar vacío.

## <a name="pathrootname"></a>path::root_name

```cpp
path root_name() const;
```

Devuelve el componente de nombre de raíz de myname. El componente puede estar vacío.

## <a name="pathrootpath"></a>path::root_path

```cpp
path root_path() const;
```

Devuelve el componente de ruta de acceso raíz de myname, específicamente root_name() / root_directory. El componente puede estar vacío.

## <a name="pathstem"></a>path::stem

```cpp
path stem() const;
```

Devuelve el componente troncal de myname, específicamente filename().native() con cualquier extension().native() final quitado. El componente puede estar vacío.

## <a name="pathstring"></a>path::string

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

La primera función miembro (template) convierte la secuencia almacenada en mypath del mismo modo que:

1. string() para string\<char, Traits, Alloc>()

1. wstring() para string\<wchar_t, Traits, Alloc>()

1. u16string() para string\<char16_t, Traits, Alloc>()

1. u32string() para string\<char32_t, Traits, Alloc>()

La segunda función miembro convierte la secuencia almacenada en mypath a la codificación preferida de sistema host para una secuencia char y la devuelve almacenada en un objeto de tipo string.

## <a name="pathstringtype"></a>path::string_type

```cpp
typedef basic_string<value_type> string_type;
```

El tipo es un sinónimo de basic_string<value_type>.

## <a name="pathswap"></a>path::swap

```cpp
void swap(path& right) noexcept;
```

Ejecuta swap(mypath, right.mypath).

## <a name="pathu16string"></a>path::u16string

```cpp
u16string u16string() const;
```

La función miembro convierte la secuencia almacenada en mypath a UTF-16 y la devuelve almacenada en un objeto de tipo u16string.

## <a name="pathu32string"></a>path::u32string

```cpp
u32string u32string() const;
```

La función miembro convierte la secuencia almacenada en mypath a UTF-32 y la devuelve almacenada en un objeto de tipo u32string.

## <a name="pathu8string"></a>path::u8string

```cpp
string u8string() const;
```

La función miembro convierte la secuencia almacenada en mypath a UTF-8 y la devuelve almacenada en un objeto de tipo u8string.

## <a name="pathvaluetype"></a>path::value_type

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume Posix
typedef char value_type;
#endif // filesystem model now defined
```

El tipo describe los elementos de la ruta de acceso preferidos de sistema operativo host.

## <a name="pathwstring"></a>path::wstring

```cpp
wstring wstring() const;
```

Convierte la secuencia almacenada en mypath a la codificación preferida de sistema host para una secuencia wchar_t y la devuelve almacenada en un objeto de tipo wstring.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<filesystem >

**Espacio de nombres:** std::experimental::filesystem

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
