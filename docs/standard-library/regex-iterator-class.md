---
title: regex_iterator (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- regex_iterator
- std::regex_iterator
- regex/std::regex_iterator
- std::regex_iterator::operator==
- regex/std::regex_iterator::operator==
- std::regex_iterator::operator!=
- regex/std::regex_iterator::operator!=
- std::regex_iterator::operator*
- regex/std::regex_iterator::operator*
- std::regex_iterator::operator->
- regex/std::regex_iterator::operator->
- std::regex_iterator::operator++
- regex/std::regex_iterator::operator++
dev_langs:
- C++
helpviewer_keywords:
- regex_iterator class
ms.assetid: 0cfd8fd0-5a95-4f3c-bf8e-6ef028c423d3
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 248e9ba676b906af62f6804f4939e04158a8e2ef
ms.openlocfilehash: 8bfed3b74020bce20f18700d30573f01cdfd2adc
ms.lasthandoff: 02/24/2017

---
# <a name="regexiterator-class"></a>regex_iterator (Clase)
Clase de iterador para las coincidencias.  
  
## <a name="syntax"></a>Sintaxis  
```
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator {  
public:  
   typedef basic_regex<Elem, RXtraits> regex_type;  
   typedef match_results<BidIt> value_type;  
   typedef std::forward_iterator_tag iterator_category;  
   typedef std::ptrdiff_t difference_type;  
   typedef const match_results<BidIt>* pointer;  
   typedef const match_results<BidIt>& reference;  

   regex_iterator();
   regex_iterator(
      BidIt first, BidIt last, const regex_type& re,  
      regex_constants::match_flag_type f = regex_constants::match_default);

   bool operator==(const regex_iterator& right);
   bool operator!=(const regex_iterator& right);
   const match_results<BidIt>& operator*();
   const match_results<BidIt> * operator->();
   regex_iterator& operator++();
   regex_iterator& operator++(int);

private:
   BidIt begin; // exposition only  
   BidIt end; // exposition only  
   regex_type *pregex;     // exposition only  
   regex_constants::match_flag_type flags; // exposition only  
   match_results<BidIt> match; // exposition only  
   };  
```  
  
### <a name="parameters"></a>Parámetros  
 `BidIt`  
 El tipo de iterador para subcoincidencias.  
  
 `Elem`  
 Tipo de los elementos que debe coincidir.  
  
 `RXtraits`  
 Clase Traits para los elementos.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla describe un objeto constante de iterador hacia delante. Extrae objetos de tipo `match_results<BidIt>` aplicando varias veces su propio objeto de expresión regular `*pregex` a la secuencia de caracteres definida por el rango de iterador `[begin, end)`.  
  
## <a name="examples"></a>Ejemplos  
 Para obtener ejemplos de expresiones regulares, vea los temas siguientes:  
  
- [regex_match (Función)](../standard-library/regex-functions.md#regex_match_function)  
  
- [regex_replace (Función)](../standard-library/regex-functions.md#regex_replace_function)  
  
- [regex_search (Función)](../standard-library/regex-functions.md#regex_search_function)  
  
- [swap (Función)](../standard-library/regex-functions.md#swap_function)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<regex>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-nameregexiteratordifferencetypea--regexiteratordifferencetype"></a><a name="regex_iterator__difference_type"></a>  regex_iterator::difference_type  
 El tipo de diferencia de un iterador.  
  
```  
typedef std::ptrdiff_t difference_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `std::ptrdiff_t`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_iterator_difference_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratoriteratorcategorya--regexiteratoriteratorcategory"></a><a name="regex_iterator__iterator_category"></a>  regex_iterator::iterator_category  
 Tipo de la categoría del iterador.  
  
```  
typedef std::forward_iterator_tag iterator_category;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `std::forward_iterator_tag`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_iterator_iterator_category.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratoroperatorneqa--regexiteratoroperator"></a><a name="regex_iterator__operator_neq"></a>  regex_iterator::operator!=  
 Compara iteradores para buscar desigualdad.  
  
```  
bool operator!=(const regex_iterator& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Iterador con el que se compara.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve `!(*this == right)`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_iterator_operator_ne.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratoroperatorstara--regexiteratoroperator"></a><a name="regex_iterator__operator_star"></a>  regex_iterator::operator*  
 Tiene acceso a la coincidencia designada.  
  
```  
const match_results<BidIt>& operator*();
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve el valor almacenado `match`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_iterator_operator_star.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratoroperatoraddadda--regexiteratoroperator"></a><a name="regex_iterator__operator_add_add"></a>  regex_iterator::operator++  
 Incrementa el iterador almacenado.  
  
```  
regex_iterator& operator++();
regex_iterator& operator++(int);
```  
  
### <a name="remarks"></a>Comentarios  
 Si la coincidencia actual no tiene ningún carácter, el primer operador llama a `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`; de lo contrario, pasa el valor almacenado `begin` para señalar el primer carácter después de la coincidencia actual y luego llama a `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`. En cualquiera de los casos, si se produce un error en la búsqueda, el operador establece el objeto en un iterador de final de la secuencia. El operador devuelve el objeto.  
  
 El segundo operador realiza una copia del objeto, incrementa el objeto y devuelve la copia.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_iterator_operator_inc.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratoroperatoreqa--regexiteratoroperator"></a><a name="regex_iterator__operator_eq"></a>  regex_iterator::operator=  
 Compara iteradores para buscar igualdad.  
  
```  
bool operator==(const regex_iterator& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Iterador con el que se compara.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve true si `*this` y `right` son los iteradores de final de secuencia o si ninguno es un iterador de final de secuencia y `begin == right.begin`, `end == right.end`, `pregex == right.pregex`y `flags == right.flags`. De lo contrario, devuelve false.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_iterator_operator_as.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratoroperator-gta--regexiteratoroperator-gt"></a><a name="regex_iterator__operator-_gt_"></a>  regex_iterator::operator-&gt;  
 Tiene acceso a la coincidencia designada.  
  
```  
const match_results<BidIt> * operator->();
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve la dirección del valor almacenado `match`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_iterator_operator_arrow.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratorpointera--regexiteratorpointer"></a><a name="regex_iterator__pointer"></a>  regex_iterator::pointer  
 El tipo de un puntero a una coincidencia.  
  
```  
typedef match_results<BidIt> *pointer;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `match_results<BidIt>*`, donde `BidIt` es el parámetro de plantilla.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_iterator_pointer.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratorreferencea--regexiteratorreference"></a><a name="regex_iterator__reference"></a>  regex_iterator::reference  
 El tipo de una referencia a una coincidencia.  
  
```  
typedef match_results<BidIt>& reference;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `match_results<BidIt>&`, donde `BidIt` es el parámetro de plantilla.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_iterator_reference.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratorregexiteratora--regexiteratorregexiterator"></a><a name="regex_iterator__regex_iterator"></a>  regex_iterator::regex_iterator  
 Construye el iterador.  
  
```  
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,  
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```  
  
### <a name="parameters"></a>Parámetros  
 `first`  
 Principio de la secuencia que debe coincidir.  
  
 `last`  
 Final de la secuencia que debe coincidir.  
  
 `re`  
 Expresión regular para las coincidencias.  
  
 `f`  
 Marcadores para coincidencias.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor crea un iterador de final de secuencia. El segundo constructor inicializa el valor almacenado `begin` con `first`, el valor almacenado `end` con `last`, el valor almacenado `pregex` con `&re`y el valor almacenado `flags` con `f`. A continuación, llama a `regex_search(begin, end, match, *pregex, flags)`. Si se produce un error en la búsqueda, el constructor establece el objeto en un iterador de final de secuencia.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_iterator_construct.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratorregextypea--regexiteratorregextype"></a><a name="regex_iterator__regex_type"></a>  regex_iterator::regex_type  
 El tipo de expresión regular que debe coincidir.  
  
```  
typedef basic_regex<Elem, RXtraits> regex_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 La definición de tipo es un sinónimo de `basic_regex<Elem, RXtraits>`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_iterator_regex_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratorvaluetypea--regexiteratorvaluetype"></a><a name="regex_iterator__value_type"></a>  regex_iterator::value_type  
 Tipo de una coincidencia.  
  
```  
typedef match_results<BidIt> value_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `match_results<BidIt>`, donde `BidIt` es el parámetro de plantilla.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_iterator_value_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
## <a name="see-also"></a>Vea también  
[\<regex>](../standard-library/regex.md)  
[regex_constants (Clase)](../standard-library/regex-constants-class.md)  
[regex_error (Clase)](../standard-library/regex-error-class.md)  
[Funciones de \<regex>](../standard-library/regex-functions.md)  
[regex_iterator (Clase)](../standard-library/regex-iterator-class.md)  
[Operadores de \<regex>](../standard-library/regex-operators.md)  
[regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md)  
[regex_traits (Clase)](../standard-library/regex-traits-class.md)  
[Definiciones de tipo \<regex>](../standard-library/regex-typedefs.md)  

  

