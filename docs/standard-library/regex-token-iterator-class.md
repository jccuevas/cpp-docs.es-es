---
title: regex_token_iterator (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- regex_token_iterator
- std::regex_token_iterator
- regex/std::regex_token_iterator
- std::regex_token_iterator::regex_type
- regex/std::regex_token_iterator::regex_type
- std::regex_token_iterator::value_type
- regex/std::regex_token_iterator::value_type
- std::regex_token_iterator::iterator_category
- regex/std::regex_token_iterator::iterator_category
- std::regex_token_iterator::difference_type
- regex/std::regex_token_iterator::difference_type
- std::regex_token_iterator::pointer
- regex/std::regex_token_iterator::pointer
- std::regex_token_iterator::reference
- regex/std::regex_token_iterator::reference
- std::regex_token_iterator::operator==
- regex/std::regex_token_iterator::operator==
- std::regex_token_iterator::operator!=
- regex/std::regex_token_iterator::operator!=
- std::regex_token_iterator::operator*
- regex/std::regex_token_iterator::operator*
- std::regex_token_iterator::operator->
- regex/std::regex_token_iterator::operator->
- std::regex_token_iterator::operator++
- regex/std::regex_token_iterator::operator++
- std::regex_token_iterator::operator!=
- regex/std::regex_token_iterator::operator!=
dev_langs:
- C++
helpviewer_keywords:
- regex_token_iterator class
ms.assetid: a213ba48-8e4e-4b6b-871a-2637acf05f15
caps.latest.revision: 15
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
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: 55da414f0a743fab278cb47441efe04e82ac3279
ms.lasthandoff: 02/24/2017

---
# <a name="regextokeniterator-class"></a>regex_token_iterator (Clase)
Clase de iterador para subcoincidencias.  
  
## <a name="syntax"></a>Sintaxis  
```  
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_token_iterator {  
public:  
   typedef basic_regex<Elem, RXtraits> regex_type;  
   typedef sub_match<BidIt> value_type;  
   typedef std::forward_iterator_tag iterator_category;  
   typedef std::ptrdiff_t difference_type;  
   typedef const sub_match<BidIt> *pointer;  
   typedef const sub_match<BidIt>& reference;  
   regex_token_iterator();
   regex_token_iterator(
      BidIt first, BidIt last,  
      const regex_type& re, int submatch = 0,  
      regex_constants::match_flag_type f = regex_constants::match_default);
   regex_token_iterator(
      BidIt first, BidIt last,  
      const regex_type& re, const std::vector<int> submatches,  
      regex_constants::match_flag_type f = regex_constants::match_default);
   template <std::size_t N>  
   regex_token_iterator(
      BidIt first, BidIt last,  
      const regex_type& re, const int (&submatches)[N],  
      regex_constants::match_flag_type f = regex_constants::match_default);
   bool operator==(const regex_token_iterator& right);
   bool operator!=(const regex_token_iterator& right);
   const basic_string<Elem>& operator*();
   const basic_string<Elem> * operator->();
   regex_token_iterator& operator++();
   regex_token_iterator& operator++(int);
private:  
   regex_iterator<BidIt, Elem, RXtraits> it; // exposition only  
   vector<int> subs;   // exposition only  
   int pos;  // exposition only  
   };  
```  
#### <a name="parameters"></a>Parámetros  
 `BidIt`  
 El tipo de iterador para subcoincidencias.  
  
 `Elem`  
 Tipo de los elementos que debe coincidir.  
  
 `RXtraits`  
 Clase Traits para los elementos.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla describe un objeto constante de iterador hacia delante. Conceptualmente, contiene un objeto `regex_iterator` que usa para buscar coincidencias de expresiones regulares en una secuencia de caracteres. Extrae objetos del tipo `sub_match<BidIt>` que representan las subcoincidencias identificadas por los valores de índice en el vector almacenado `subs` para cada coincidencia de expresión regular.  
  
 Un valor de índice de -1 señala la secuencia de caracteres que empieza inmediatamente después del final de la coincidencia de expresión regular anterior (o comienza al principio de la secuencia de caracteres si no había ninguna coincidencia de expresión regular anterior) y que se extiende, aunque sin incluirlo, al primer carácter de la coincidencia de expresión regular actual o hasta el final de la secuencia de caracteres si no hay una coincidencia actual. Cualquier otro valor de índice `idx` señala el contenido del grupo de capturas incluido en `it.match[idx]`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<regex>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-nameregextokeniteratordifferencetypea--regextokeniteratordifferencetype"></a><a name="regex_token_iterator__difference_type"></a>  regex_token_iterator::difference_type  
 El tipo de diferencia de un iterador.  
  
```  
typedef std::ptrdiff_t difference_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `std::ptrdiff_t`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp    
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
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
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
```  
  
##  <a name="a-nameregextokeniteratoriteratorcategorya--regextokeniteratoriteratorcategory"></a><a name="regex_token_iterator__iterator_category"></a>  regex_token_iterator::iterator_category  
 Tipo de la categoría del iterador.  
  
```  
typedef std::forward_iterator_tag iterator_category;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `std::forward_iterator_tag`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_token_iterator_iterator_category.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
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
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="a-nameregextokeniteratoroperatorneqa--regextokeniteratoroperator"></a><a name="regex_token_iterator__operator_neq"></a>  regex_token_iterator::operator!=  
 Compara iteradores para buscar desigualdad.  
  
```  
bool operator!=(const regex_token_iterator& right);
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Iterador con el que se compara.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve `!(*this == right)`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_token_iterator_operator_ne.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
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
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="a-nameregextokeniteratoroperatorstara--regextokeniteratoroperator"></a><a name="regex_token_iterator__operator_star"></a>  regex_token_iterator::operator*  
 Tiene acceso a la subcoincidencia designada.  
  
```  
const sub_match<BidIt>& operator*();
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un objeto `sub_match<BidIt>` que representa el grupo de capturas identificado por el valor de índice `subs[pos]`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_token_iterator_operator_star.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
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
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="a-nameregextokeniteratoroperatoraddadda--regextokeniteratoroperator"></a><a name="regex_token_iterator__operator_add_add"></a>  regex_token_iterator::operator++  
 Incrementa el iterador almacenado.  
  
```  
regex_token_iterator& operator++();

regex_token_iterator& operator++(int);
```  
  
### <a name="remarks"></a>Comentarios  
 Si el iterador almacenado `it` es un iterador de final de secuencia, el primer operador establece el valor almacenado `pos` en el valor de `subs.size()` (lo que lo convierte en un iterador de fin de secuencia). En caso contrario, el operador incrementa el valor almacenado `pos`; si el resultado es igual al valor `subs.size()`, establece el valor almacenado `pos` en cero e incrementa el iterador almacenado `it`. Si al incrementar el iterador almacenado no queda igual que un iterador de final de secuencia, el operador no hace nada más. De lo contrario, si el final de la coincidencia precedente no estaba al final de la secuencia de caracteres, el operador establece el valor almacenado de `pos` en `subs.size()`. De lo contrario, el operador incrementa repetidamente el valor almacenado `pos` hasta `pos == subs.size()` o `subs[pos] == -1` (lo que garantiza que la siguiente desreferencia del iterador devolverá el final de la secuencia de caracteres si uno de los valores de índice es -1). En todos los casos, el operador devuelve el objeto.  
  
 El segundo operador realiza una copia del objeto, incrementa el objeto y devuelve la copia.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_token_iterator_operator_inc.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
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
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="a-nameregextokeniteratoroperatoreqeqa--regextokeniteratoroperator"></a><a name="regex_token_iterator__operator_eq_eq"></a>  regex_token_iterator::operator==  
 Compara iteradores para buscar igualdad.  
  
```  
bool operator==(const regex_token_iterator& right);
```  
  
### <a name="parameters"></a>Parámetros  
 right  
 Iterador con el que se compara.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve `it == right.it && subs == right.subs && pos == right.pos`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_token_iterator_operator_eq.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
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
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="a-nameregextokeniteratoroperator-gta--regextokeniteratoroperator-gt"></a><a name="regex_token_iterator__operator-_gt_"></a>  regex_token_iterator::operator-&gt;  
 Tiene acceso a la subcoincidencia designada.  
  
```  
const sub_match<BidIt> * operator->();
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un puntero al objeto `sub_match<BidIt>` que representa el grupo de capturas identificado por el valor de índice `subs[pos]`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_token_iterator_operator_arrow.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
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
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="a-nameregextokeniteratorpointera--regextokeniteratorpointer"></a><a name="regex_token_iterator__pointer"></a>  regex_token_iterator::pointer  
 El tipo de un puntero a una coincidencia.  
  
```  
typedef sub_match<BidIt> *pointer;  
```  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_token_iterator_pointer.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
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
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `sub_match<BidIt>*`, donde `BidIt` es el parámetro de plantilla.  
  
##  <a name="a-nameregextokeniteratorreferencea--regextokeniteratorreference"></a><a name="regex_token_iterator__reference"></a>  regex_token_iterator::reference  
 El tipo de una referencia a una subcoincidencia.  
  
```  
typedef sub_match<BidIt>& reference;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `sub_match<BidIt>&`, donde `BidIt` es el parámetro de plantilla.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_token_iterator_reference.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
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
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="a-nameregextokeniteratorregextokeniteratora--regextokeniteratorregextokeniterator"></a><a name="regex_token_iterator__regex_token_iterator"></a>  regex_token_iterator::regex_token_iterator  
 Construye el iterador.  
  
```  
regex_token_iterator();

regex_token_iterator(BidIt first, BidIt last,  
    const regex_type& re, int submatch = 0,  
    regex_constants::match_flag_type f = regex_constants::match_default);

regex_token_iterator(BidIt first, BidIt last,  
    const regex_type& re, const vector<int> submatches,  
    regex_constants::match_flag_type f = regex_constants::match_default);

template <std::size_t N>  
regex_token_iterator(BidIt first, BidIt last,  
    const regex_type& re, const int (&submatches)[N],  
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
 El primer constructor crea un iterador de final de secuencia.  
  
 El segundo constructor crea un objeto cuyo iterador almacenado `it` se inicializa en `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, cuyo vector almacenado `subs` contiene exactamente un número entero, con el valor `submatch`, y cuyo valor almacenado `pos` es cero. Nota: el objeto resultante extrae la subcoincidencia identificada por el valor de índice `submatch` por cada coincidencia de expresión regular correcta.  
  
 El tercer constructor crea un objeto cuyo iterador almacenado `it` se inicializa en `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, cuyo vector almacenado `subs` contiene una copia del argumento `submatches`de constructor y cuyo valor almacenado `pos` es cero.  
  
 El cuarto constructor crea un objeto cuyo iterador almacenado `it` se inicializa en `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, cuyo vector almacenado `subs` contiene los valores de `N` señalados por el argumento `submatches`de constructor y cuyo valor almacenado `pos` es cero.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_token_iterator_construct.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
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
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="a-nameregextokeniteratorregextypea--regextokeniteratorregextype"></a><a name="regex_token_iterator__regex_type"></a>  regex_token_iterator::regex_type  
 El tipo de expresión regular que debe coincidir.  
  
```  
typedef basic_regex<Elem, RXtraits> regex_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 La definición de tipo es un sinónimo de `basic_regex<Elem, RXtraits>`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_token_iterator_regex_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
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
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
##  <a name="a-nameregextokeniteratorvaluetypea--regextokeniteratorvaluetype"></a><a name="regex_token_iterator__value_type"></a>  regex_token_iterator::value_type  
 El tipo de una subcoincidencia.  
  
```  
typedef sub_match<BidIt> value_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `sub_match<BidIt>`, donde `BidIt` es el parámetro de plantilla.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_token_iterator_value_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_token_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "aaxaayaaz";   
    Myiter::regex_type rx("(a)a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
// show whole match   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefix before match   
    next = Myiter(pat, pat + strlen(pat), rx, -1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show (a) submatch only   
    next = Myiter(pat, pat + strlen(pat), rx, 1);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and submatches   
    std::vector<int> vec;   
    vec.push_back(-1);   
    vec.push_back(1);   
    next = Myiter(pat, pat + strlen(pat), rx, vec);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
// show prefixes and whole matches   
    int arr[] = {-1, 0};   
    next = Myiter(pat, pat + strlen(pat), rx, arr);   
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
    std::cout << std::endl;   
  
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
match == aa  
match == aa  
match == aa  
  
match ==   
match == x  
match == y  
match == z  
  
match == a  
match == a  
match == a  
  
match ==   
match == a  
match == x  
match == a  
match == y  
match == a  
match == z  
  
match ==   
match == aa  
match == x  
match == aa  
match == y  
match == aa  
match == z  
  
```  
  
## <a name="see-also"></a>Vea también  
[\<regex>](../standard-library/regex.md)  
[regex_constants (Clase)](../standard-library/regex-constants-class.md)  
[regex_error (Clase)](../standard-library/regex-error-class.md)  
[Funciones de \<regex>](../standard-library/regex-functions.md)  
[regex_iterator (Clase)](../standard-library/regex-iterator-class.md)  
[Operadores de \<regex>](../standard-library/regex-operators.md)  
[regex_traits (Clase)](../standard-library/regex-traits-class.md)  
[Definiciones de tipo \<regex>](../standard-library/regex-typedefs.md)  


