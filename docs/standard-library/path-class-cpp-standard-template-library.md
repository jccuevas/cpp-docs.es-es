---
title: "path (Clase, biblioteca de plantillas est&#225;ndar de C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "filesystem/std::tr2::sys::path"
dev_langs: 
  - "C++"
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
caps.latest.revision: 14
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# path (Clase, biblioteca de plantillas est&#225;ndar de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase **path** almacena un objeto de tipo string\_type, denominado myname aquí a efectos de la exposición, que se puede usar como una ruta de acceso. string\_type es un sinónimo de basic\_string\<value\_type\>, donde value\_type es un sinónimo de char en Windows o wchar\_t en Posix.  
  
 Para obtener más información y ejemplos de código, vea [Exploración del sistema de archivos \(C\+\+\)](../standard-library/file-system-navigation.md).  
  
## Sintaxis  
  
```  
class path;  
```  
  
## path::append  
  
```  
template<class Source>  
    path& append(const Source& source);  
template<class InIt>  
    path& append(InIt first, InIt last);  
```  
  
 Las funciones miembro anexan la secuencia especificada a mypath convertida e insertan un preferred\_separator según sea necesario.  
  
## path::assign  
  
```  
template<class Source>  
    path& assign(const Source& source);  
template<class InIt>  
    path& assign(InIt first, InIt last);  
```  
  
 Las funciones miembro reemplazan mypath con la secuencia especificada, convertida según sea necesario.  
  
## path::begin  
  
```  
iterator begin() const;  
```  
  
 Devuelve un path::iterator que designa el primer elemento de la ruta de acceso del nombre de ruta de acceso, si está presente.  
  
## path::c\_str  
  
```  
const value_type& *c_str() const noexcept;  
```  
  
 Devuelve un puntero al primer carácter de mypath.  
  
## path::clear  
  
```  
void clear() noexcept;  
```  
  
 La función miembro ejecuta mypath.clear\(\)  
  
## path::compare  
  
```  
int compare(const path& pval) const noexcept;  
int compare(const string_type& str) const;  
int compare(const value_type *ptr) const;  
```  
  
 La primera función devuelve mypath.compare\(pval.native\(\)\). La segunda función devuelve mypath.compare\(str\). La tercera función devuelve mypath.compare\(ptr\).  
  
## path::concat  
  
```  
template<class Source>  
    path& concat(const Source& source);  
template<class InIt>  
    path& concat(InIt first, InIt last);  
```  
  
 Las funciones miembro anexan la secuencia especificada a mypath, convertida según sea necesario \(pero no insertan un preferred\_separator\).  
  
## path::const\_iterator  
  
```  
typedef iterator const_iterator;  
```  
  
 El tipo es un sinónimo de iterador.  
  
## path::empty  
  
```  
bool empty() const noexcept;  
```  
  
 Devuelve mypath.empty\(\).  
  
## path::end  
  
```  
iterator end() const;  
```  
  
 Devuelve un iterador de final de secuencia de tipo iterador.  
  
## path::extension  
  
```  
path extension() const;  
```  
  
 Devuelve el sufijo de filename\(\) X tal que:  
  
 Si X \=\= path\("."\) &#124;&#124; X \=\= path\(".."\) o bien, si X no contiene ningún punto, el sufijo está vacío.  
  
 De lo contrario, el sufijo comienza con \(e incluye\) el punto situado más al derecha.  
  
## path::filename  
  
```  
path filename() const;  
```  
  
 Devuelve el componente del directorio raíz de myname, específicamente `empty() ? path() : *--end()`. El componente puede estar vacío.  
  
## path::generic\_string  
  
```  
template<class Elem,  
    class Traits = char_traits<Elem>,  
    class Alloc = allocator<Elem>>  
    basic_string<Elem, Traits, Alloc>  
        generic_string(const Alloc& al = Alloc()) const;  
STD string generic_string() const;  
```  
  
 Devuelve `this->string<Elem, Traits, Alloc>(_Al)` con \(en Windows\) cualquier barra diagonal inversa convertida en una barra diagonal.  
  
## path::generic\_u16string  
  
```  
STD u16string generic_u16string() const;  
```  
  
 Devuelve u16string\(\) con \(en Windows\) cualquier barra diagonal inversa convertida en una barra diagonal.  
  
## path::generic\_u32string  
  
```  
STD u32string generic_u32string() const;  
```  
  
 Devuelve u32string\(\) con \(en Windows\) cualquier barra diagonal inversa convertida en una barra diagonal.  
  
## path::generic\_u8string  
  
```  
STD string generic_u8string() const;  
```  
  
 Devuelve u8string\(\) con \(en Windows\) cualquier barra diagonal inversa convertida en una barra diagonal.  
  
## path::generic\_wstring  
  
```  
STD wstring generic_wstring() const;  
```  
  
 Devuelve wstring\(\) con \(en Windows\) cualquier barra diagonal inversa convertida en una barra diagonal.  
  
## path::has\_extension  
  
```  
bool has_extension() const;  
```  
  
 Devuelve \!extension\(\).empty\(\).  
  
## path::has\_filename  
  
```  
bool has_filename() const;  
```  
  
 Devuelve \!filename\(\).empty\(\).  
  
## path::has\_parent\_path  
  
```  
  
bool has_parent_path() const;  
  
```  
  
 Devuelve \!parent\_path\(\).empty\(\).  
  
## path::has\_relative\_path  
  
```  
bool has_relative_path() const;  
  
```  
  
 Devuelve \!relative\_path\(\).empty\(\).  
  
## path::has\_root\_directory  
  
```  
bool has_root_directory() const;  
  
```  
  
 Devuelve \!root\_directory\(\).empty\(\).  
  
## path::has\_root\_name  
  
```  
bool has_root_name() const;  
```  
  
 Devuelve \!root\_name\(\).empty\(\).  
  
## path::has\_root\_path  
  
```  
bool has_root_path() const;  
  
```  
  
 Devuelve \!root\_path\(\).empty\(\).  
  
## path::has\_stem  
  
```  
bool has_stem() const;  
```  
  
 Devuelve \!stem\(\).empty\(\).  
  
## path::is\_absolute  
  
```  
bool is_absolute() const;  
```  
  
 Para Windows, la función devuelve has\_root\_name\(\) && has\_root\_directory\(\). Para Posix, la función devuelve has\_root\_directory\(\).  
  
## path::is\_relative  
  
```  
bool is_relative() const;  
```  
  
 Devuelve \!is\_absolute\(\).  
  
## path::iterator  
  
```  
class iterator  
    {// bidirectional iterator for path  
    typedef bidirectional_iterator_tag iterator_category;  
    typedef path_type value_type;  
    typedef ptrdiff_t difference_type;  
    typedef const value_type *pointer;  
    typedef const value_type& reference;  
    .....  
    };  
  
```  
  
 La clase describe un iterador constante bidireccional que designa los componentes de la ruta de acceso de myname en la secuencia:  
  
1.  el nombre de raíz, si está presente  
  
2.  el directorio raíz, si está presente  
  
3.  los elementos restantes del directorio de la ruta de acceso principal, si está presente, que terminan con el nombre de archivo, si está presente  
  
4.  
  
5.  
  
 Para pval, un objeto de tipo path:  
  
1.  path::iterator X \= pval.begin\(\) designa el primer elemento de la ruta de acceso en el nombre de ruta de acceso, si está presente.  
  
2.  X \=\= pval.end\(\) es true cuando X apunta inmediatamente después del final de la secuencia de componentes.  
  
3.  \*X devuelve una cadena que coincide con el componente actual.  
  
4.  \+\+X designa el próximo componente de la secuencia, si está presente.  
  
5.  \-\-X designa el componente anterior de la secuencia, si existe.  
  
6.  Al modificar myname, se invalidan todos los iteradores que designan elementos en myname.  
  
## path::make\_preferred  
  
```  
path& make_preferred();  
  
```  
  
 La función miembro convierte cada separador en un preferred\_separator según sea necesario.  
  
## path::native  
  
```  
const string_type& native() const noexcept;  
```  
  
 Devuelve myname.  
  
## path::operator\=  
  
```  
path& operator=(const path& right);  
path& operator=(path&& right) noexcept;  
template<class Source>  
    path& operator=(const Source& source);  
  
```  
  
 El primer operador miembro copia right.myname a myname. El segundo operador miembro mueve right.myname a myname. El tercer operador miembro se comporta igual que \*this \= path\(source\).  
  
## path::operator\+\=  
  
```  
path& operator+=(const path& right);  
path& operator+=(const string_type& str);  
path& operator+=(const value_type *ptr);  
path& operator+=(value_type elem);  
template<class Source>  
    path& operator+=(const Source& source);  
template<class Elem>  
    path& operator+=(Elem elem);  
```  
  
 Las funciones miembro se comportan igual que las siguientes expresiones correspondientes:  
  
1.  concat\(right\);  
  
2.  concat\(path\(str\)\);  
  
3.  concat\(ptr\);  
  
4.  concat\(string\_type\(1, elem\)\);  
  
5.  concat\(source\);  
  
6.  concat\(path\(basic\_string\<Elem\>\(1, elem\)\)\);  
  
## path::operator\/\=  
  
```  
path& operator/=(const path& right);  
template<class Source>  
    path& operator/=(const Source& source);  
  
```  
  
 Las funciones miembro se comportan igual que las siguientes expresiones correspondientes:  
  
1.  append\(right\);  
  
2.  append\(source\);  
  
## path::operator string\_type  
  
```  
operator string_type() const;  
```  
  
 El operador miembro devuelve myname.  
  
## path::parent\_path  
  
```  
path parent_path() const;  
  
```  
  
 Devuelve el componente principal de ruta de acceso de myname, específicamente el prefijo de myname después de quitar filename\(\).native\(\) y los separadores de directorio inmediatamente anteriores. \(Igualmente, si funciones begin\(\)\! \= end\(\), es la combinación de todos los elementos en el intervalo \[funciones begin\(\),\-\-end\(\)\) aplicando consecutivamente operador \/ \=.\) El componente puede estar vacío.  
  
## path::path  
  
```  
path();  
path(const path& right);  
path(path&& right) noexcept;  
template<class Source>  
    path(const Source& source);  
template<class Source>  
    path(const Source& source, const locale& loc);  
template<class InIt>  
    path(InIt first, InIt last);  
template<class InIt>  
    path(InIt first, InIt last, const locale& loc);  
  
```  
  
 Todos los constructores crean myname de varias maneras:  
  
 Para path\(\), es myname\(\).  
  
 Para path\(const path& right\), es myname\(right.myname\).  
  
 Para path\(path&& right\), es myname\(right.myname\).  
  
 Para template\<class Source\> path\(const Source& source\), es myname\(source\).  
  
 Para template\<class Source\> path\(const Source& source, const locale& loc\), es myname\(source\), que obtiene cualquier faceta codecvt necesaria de loc.  
  
 Para template\<class InIt\> path\(InIt first, InIt last\), es myname\(first, last\).  
  
 Para template\<class InIt\> path\(InIt first, InIt last, const locale& loc\), es myname\(first, last\), que obtiene cualquier faceta codecvt necesaria de loc.  
  
## path::preferred\_separator  
  
```  
#if _WIN32_C_LIB  
static constexpr value_type preferred_separator == L'\\';  
#else // assume Posix  
static constexpr value_type preferred_separator == '/';  
#endif // filesystem model now defined  
  
```  
  
 El objeto constante ofrece el carácter preferido para separar los componentes de la ruta de acceso, según el sistema operativo host. Tenga en cuenta que en la mayoría de los contextos en Windows también se permite usar L '\/' en su lugar.  
  
## path::relative\_path  
  
```  
path relative_path() const;  
  
```  
  
 Devuelve el componente de ruta de acceso relativa de myname, específicamente el sufijo de myname después de quitar root\_path\(\).native\(\) y los separadores de directorio redundantes inmediatamente posteriores. El componente puede estar vacío.  
  
## path::remove\_filename  
  
```  
path& remove_filename();  
  
```  
  
## path::replace\_extension  
  
```  
path& replace_extension(const path& newext = path());  
  
```  
  
 La función miembro quita primero el sufijo extension\(\).native\(\) de myname. Entonces si \!newext.empty\(\) && newext\[0\] \!\= dot \[donde dot es \*path\("."\).c\_str\(\)\], dot se anexa a myname. A continuación, se anexa newext a myname.  
  
## path::replace\_filename  
  
```  
  
path& replace_filename(const path& pval);  
  
```  
  
 La función miembro ejecuta:  
  
```  
remove_filename();  
*this /= pval;  
return (*this);  
```  
  
## path::root\_directory  
  
```  
path root_directory() const;  
  
```  
  
 Devuelve el componente de directorio raíz de myname. El componente puede estar vacío.  
  
## path::root\_name  
  
```  
path root_name() const;  
  
```  
  
 Devuelve el componente de nombre de raíz de myname. El componente puede estar vacío.  
  
## path::root\_path  
  
```  
  
path root_path() const;  
  
```  
  
 Devuelve el componente de ruta de acceso raíz de myname, específicamente root\_name\(\) \/ root\_directory. El componente puede estar vacío.  
  
## path::stem  
  
```  
  
path stem() const;  
  
```  
  
 Devuelve el componente troncal de myname, específicamente filename\(\).native\(\) con cualquier extension\(\).native\(\) final quitado. El componente puede estar vacío.  
  
## path::string  
  
```  
template<class Elem,  
    class Traits = char_traits<Elem>,  
    class Alloc = allocator<Elem>>  
    basic_string<Elem, Traits, Alloc>  
        string(const Alloc& al = Alloc()) const;  
STD string string() const;  
  
```  
  
 La primera función miembro \(template\) convierte la secuencia almacenada en mypath del mismo modo que:  
  
1.  string\(\) para string\<char, Traits, Alloc\>\(\)  
  
2.  wstring\(\) para string\<wchar\_t, Traits, Alloc\>\(\)  
  
3.  u16string\(\) para string\<char16\_t, Traits, Alloc\>\(\)  
  
4.  u32string\(\) para string\<char32\_t, Traits, Alloc\>\(\)  
  
 La segunda función miembro convierte la secuencia almacenada en mypath a la codificación preferida de sistema host para una secuencia char y la devuelve almacenada en un objeto de tipo string.  
  
## path::string\_type  
  
```  
typedef basic_string<value_type> string_type;  
  
```  
  
 El tipo es un sinónimo de basic\_string\<value\_type\>.  
  
## path::swap  
  
```  
void swap(path & right) noexcept;  
  
```  
  
 Ejecuta swap\(mypath, right.mypath\).  
  
## path::u16string  
  
```  
STD u16string u16string() const;  
  
```  
  
 La función miembro convierte la secuencia almacenada en mypath a UTF\-16 y la devuelve almacenada en un objeto de tipo u16string.  
  
## path::u32string  
  
```  
STD u32string u32string() const;  
  
```  
  
 La función miembro convierte la secuencia almacenada en mypath a UTF\-32 y la devuelve almacenada en un objeto de tipo u32string.  
  
## path::u8string  
  
```  
STD string u8string() const;  
  
```  
  
 La función miembro convierte la secuencia almacenada en mypath a UTF\-8 y la devuelve almacenada en un objeto de tipo u8string.  
  
## path::value\_type  
  
```  
  
#if _WIN32_C_LIB  
typedef wchar_t value_type;  
#else // assume Posix  
typedef char value_type;  
#endif // filesystem model now defined  
  
```  
  
 El tipo describe los elementos de la ruta de acceso preferidos de sistema operativo host.  
  
## path::wstring  
  
```  
STD wstring wstring() const;  
```  
  
 Convierte la secuencia almacenada en mypath a la codificación preferida de sistema host para una secuencia wchar\_t y la devuelve almacenada en un objeto de tipo wstring.  
  
## Requisitos  
 **Encabezado:** filesystem  
  
 **Espacio de nombres:** std::tr2::sys  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)