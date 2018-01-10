---
title: sub_match (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- regex/std::sub_match
- regex/std::sub_match::matched
- regex/std::sub_match::compare
- regex/std::sub_match::length
- regex/std::sub_match::str
- regex/std::sub_match::difference_type
- regex/std::sub_match::iterator
- regex/std::sub_match::value_type
dev_langs: C++
helpviewer_keywords:
- std::sub_match [C++]
- std::sub_match [C++], matched
- std::sub_match [C++], compare
- std::sub_match [C++], length
- std::sub_match [C++], str
- std::sub_match [C++], difference_type
- std::sub_match [C++], iterator
- std::sub_match [C++], value_type
ms.assetid: 804e2b9e-d16a-4c4c-ac60-024e0b2dd0e8
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0d26e17fd496507f6985f7896eb01f7a79c900e1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="submatch-class"></a>sub_match (Clase)
Describe a una subcoincidencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class BidIt>  
class sub_match  
 : public std::pair<BidIt, BidIt> {  
public:  
    bool matched;  
    int compare(const sub_match& right) const;  
    int compare(const basic_string<value_type>& right) const;   
    int compare(const value_type *right) const;   
    difference_type length() const;  
    operator basic_string<value_type>() const;
    basic_string<value_type> str() const;
  
    // typedefs
    typedef typename iterator_traits<BidIt>::value_type value_type;  
    typedef typename iterator_traits<BidIt>::difference_type difference_type;  
    typedef BidIt iterator;  
 };  
```  
  
#### <a name="parameters"></a>Parámetros  
 `BidIt`  
 El tipo de iterador para subcoincidencias.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla describe un objeto que designa una secuencia de caracteres que coinciden con un grupo de capturas en una llamada a [regex_match](../standard-library/regex-functions.md#regex_match) o [regex_search](../standard-library/regex-functions.md#regex_search). Los objetos del tipo [match_results (clase)](../standard-library/match-results-class.md) contienen una matriz de estos objetos, uno para cada grupo de capturas en la expresión regular usada en la búsqueda.  
  
 Si no hay coincidencia con el grupo de capturas, el miembro de datos `matched` del objeto se considera false y los dos iteradores `first` y `second` (heredados de la base `std::pair`) son iguales. Si hay coincidencia con el grupo de capturas, `matched` es true, el iterador `first` apunta al primer carácter de la secuencia de destino que coincide con el grupo de capturas y el iterador `second` apunta a una posición más allá del último carácter de la secuencia de destino que coincide con el grupo de capturas. Observe que para una coincidencia de longitud cero, el miembro `matched` es true, los dos iteradores son iguales y ambos apuntan a la posición de la coincidencia.  
  
 Una coincidencia de longitud cero puede aparecer cuando un grupo de capturas solo se compone de una aserción o de una repetición que permite que se repita cero. Por ejemplo:  
  
 "^" coincide con la secuencia "a" de destino; el objeto `sub_match` correspondiente al grupo de capturas 0 contiene iteradores que apuntan al primer carácter de la secuencia.  
  
 "b(a*)b" coincide con la secuencia "bb" de destino; el objeto `sub_match` correspondiente al grupo de capturas 1 contiene iteradores que apuntan al segundo carácter de la secuencia.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<regex>  
  
 **Espacio de nombres:** std  
  
##  <a name="compare"></a>  sub_match::compare  
 Comparar la subcoincidencia con una secuencia.  
  
```  
int compare(const sub_match& right) const;
int compare(const basic_string<value_type>& str) const;
int compare(const value_type *ptr) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `right`  
 Subcoincidencia con la que se va comparar.  
  
 `str`  
 Cadena con la que se va a comparar.  
  
 `ptr`  
 La secuencia terminada en un valor nulo con la que se va a comparar.  
  
### <a name="remarks"></a>Comentarios  
 La primera función miembro compara la secuencia coincidente `[first, second)` con la secuencia coincidente `[right.first, right.second)`. La segunda función miembro compara la secuencia coincidente `[first, second)` con la secuencia de caracteres `[right.begin(), right.end())`. La tercera función miembro compara la secuencia coincidente `[first, second)` con la secuencia de caracteres `[right, right + std::char_traits<value_type>::length(right))`.  
  
 Cada función devuelve lo siguiente:  
  
 un valor negativo si el primer valor diferente de la secuencia coincidente se es menor que el elemento correspondiente de la secuencia de operandos (según lo determinado por `std::char_traits<value_type>::compare`), o si los dos tienen un prefijo común pero la secuencia de destino es más larga  
  
 cero si los dos son iguales elemento a elemento y tienen la misma longitud  
  
 un valor positivo en caso contrario  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__sub_match_compare.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::csub_match sub = mr[1];   
    std::cout << "matched == " << std::boolalpha   
        << sub.matched << std::endl;   
    std::cout << "length == " << sub.length() << std::endl;   
  
    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);   
    std::cout << "difference == " << dif << std::endl;   
  
    std::csub_match::iterator first = sub.first;   
    std::csub_match::iterator last = sub.second;   
    std::cout << "range == " << std::string(first, last)   
        << std::endl;   
    std::cout << "string == " << sub << std::endl;   
  
    std::csub_match::value_type *ptr = "aab";   
    std::cout << "compare(\"aab\") == "   
        << sub.compare(ptr) << std::endl;   
    std::cout << "compare(string) == "   
        << sub.compare(std::string("AAA")) << std::endl;   
    std::cout << "compare(sub) == "   
        << sub.compare(sub) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
matched == true  
length == 3  
difference == 3  
range == aaa  
string == aaa  
compare("aab") == -1  
compare(string) == 1  
compare(sub) == 0  
```  
  
##  <a name="difference_type"></a>  sub_match::difference_type  
 El tipo de diferencia de un iterador.  
  
```  
typedef typename iterator_traits<BidIt>::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 La definición de tipo es un sinónimo de `iterator_traits<BidIt>::difference_type`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__sub_match_difference_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::csub_match sub = mr[1];   
    std::cout << "matched == " << std::boolalpha   
        << sub.matched << std::endl;   
    std::cout << "length == " << sub.length() << std::endl;   
  
    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);   
    std::cout << "difference == " << dif << std::endl;   
  
    std::csub_match::iterator first = sub.first;   
    std::csub_match::iterator last = sub.second;   
    std::cout << "range == " << std::string(first, last)   
        << std::endl;   
    std::cout << "string == " << sub << std::endl;   
  
    std::csub_match::value_type *ptr = "aab";   
    std::cout << "compare(\"aab\") == "   
        << sub.compare(ptr) << std::endl;   
    std::cout << "compare(string) == "   
        << sub.compare(std::string("AAA")) << std::endl;   
    std::cout << "compare(sub) == "   
        << sub.compare(sub) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
matched == true  
length == 3  
difference == 3  
range == aaa  
string == aaa  
compare("aab") == -1  
compare(string) == 1  
compare(sub) == 0  
```  
  
##  <a name="iterator"></a>  sub_match::iterator  
 Tipo de un iterador.  
  
```  
typedef BidIt iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del argumento de tipo de plantilla `Bidit`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__sub_match_iterator.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::csub_match sub = mr[1];   
    std::cout << "matched == " << std::boolalpha   
        << sub.matched << std::endl;   
    std::cout << "length == " << sub.length() << std::endl;   
  
    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);   
    std::cout << "difference == " << dif << std::endl;   
  
    std::csub_match::iterator first = sub.first;   
    std::csub_match::iterator last = sub.second;   
    std::cout << "range == " << std::string(first, last)   
        << std::endl;   
    std::cout << "string == " << sub << std::endl;   
  
    std::csub_match::value_type *ptr = "aab";   
    std::cout << "compare(\"aab\") == "   
        << sub.compare(ptr) << std::endl;   
    std::cout << "compare(string) == "   
        << sub.compare(std::string("AAA")) << std::endl;   
    std::cout << "compare(sub) == "   
        << sub.compare(sub) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
matched == true  
length == 3  
difference == 3  
range == aaa  
string == aaa  
compare("aab") == -1  
compare(string) == 1  
compare(sub) == 0  
```  
  
##  <a name="length"></a>  sub_match::length  
 Devuelve la longitud de una subcoincidencia.  
  
```  
difference_type length() const;
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve la longitud de la secuencia coincidente, o cero si no se ha producido ninguna secuencia coincidente.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__sub_match_length.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::csub_match sub = mr[1];   
    std::cout << "matched == " << std::boolalpha   
        << sub.matched << std::endl;   
    std::cout << "length == " << sub.length() << std::endl;   
  
    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);   
    std::cout << "difference == " << dif << std::endl;   
  
    std::csub_match::iterator first = sub.first;   
    std::csub_match::iterator last = sub.second;   
    std::cout << "range == " << std::string(first, last)   
        << std::endl;   
    std::cout << "string == " << sub << std::endl;   
  
    std::csub_match::value_type *ptr = "aab";   
    std::cout << "compare(\"aab\") == "   
        << sub.compare(ptr) << std::endl;   
    std::cout << "compare(string) == "   
        << sub.compare(std::string("AAA")) << std::endl;   
    std::cout << "compare(sub) == "   
        << sub.compare(sub) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
matched == true  
length == 3  
difference == 3  
range == aaa  
string == aaa  
compare("aab") == -1  
compare(string) == 1  
compare(sub) == 0  
```  
  
##  <a name="matched"></a>  sub_match::matched  
 Indica si la coincidencia se realizó correctamente.  
  
```  
bool matched;  
```  
  
### <a name="remarks"></a>Comentarios  
 El miembro contiene `true` solo si el grupo de capturas asociado a `*this` formaba parte de la coincidencia de expresión regular.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__sub_match_matched.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::csub_match sub = mr[1];   
    std::cout << "matched == " << std::boolalpha   
        << sub.matched << std::endl;   
    std::cout << "length == " << sub.length() << std::endl;   
  
    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);   
    std::cout << "difference == " << dif << std::endl;   
  
    std::csub_match::iterator first = sub.first;   
    std::csub_match::iterator last = sub.second;   
    std::cout << "range == " << std::string(first, last)   
        << std::endl;   
    std::cout << "string == " << sub << std::endl;   
  
    std::csub_match::value_type *ptr = "aab";   
    std::cout << "compare(\"aab\") == "   
        << sub.compare(ptr) << std::endl;   
    std::cout << "compare(string) == "   
        << sub.compare(std::string("AAA")) << std::endl;   
    std::cout << "compare(sub) == "   
        << sub.compare(sub) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
matched == true  
length == 3  
difference == 3  
range == aaa  
string == aaa  
compare("aab") == -1  
compare(string) == 1  
compare(sub) == 0  
```  
  
##  <a name="op_basic_string_lt_value_type_gt"></a>  sub_match::operator basic_string&lt;value_type&gt;  
 Convierte la subcoincidencia en una cadena.  
  
```  
operator basic_string<value_type>() const;
```  
  
### <a name="remarks"></a>Comentarios  
 El operador miembro devuelve `str()`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__sub_match_operator_str.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::csub_match sub = mr[1];   
    std::cout << "matched == " << std::boolalpha   
        << sub.matched << std::endl;   
    std::cout << "length == " << sub.length() << std::endl;   
  
    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);   
    std::cout << "difference == " << dif << std::endl;   
  
    std::csub_match::iterator first = sub.first;   
    std::csub_match::iterator last = sub.second;   
    std::cout << "range == " << std::string(first, last)   
        << std::endl;   
    std::cout << "string == " << sub << std::endl;   
  
    std::csub_match::value_type *ptr = "aab";   
    std::cout << "compare(\"aab\") == "   
        << sub.compare(ptr) << std::endl;   
    std::cout << "compare(string) == "   
        << sub.compare(std::string("AAA")) << std::endl;   
    std::cout << "compare(sub) == "   
        << sub.compare(sub) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
matched == true  
length == 3  
difference == 3  
range == aaa  
string == aaa  
compare("aab") == -1  
compare(string) == 1  
compare(sub) == 0  
```  
  
##  <a name="str"></a>  sub_match::str  
 Convierte la subcoincidencia a una cadena.  
  
```  
basic_string<value_type> str() const;
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve `basic_string<value_type>(first, second)`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__sub_match_str.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::csub_match sub = mr[1];   
    std::cout << "matched == " << std::boolalpha   
        << sub.matched << std::endl;   
    std::cout << "length == " << sub.length() << std::endl;   
  
    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);   
    std::cout << "difference == " << dif << std::endl;   
  
    std::csub_match::iterator first = sub.first;   
    std::csub_match::iterator last = sub.second;   
    std::cout << "range == " << std::string(first, last)   
        << std::endl;   
    std::cout << "string == " << sub << std::endl;   
  
    std::csub_match::value_type *ptr = "aab";   
    std::cout << "compare(\"aab\") == "   
        << sub.compare(ptr) << std::endl;   
    std::cout << "compare(string) == "   
        << sub.compare(std::string("AAA")) << std::endl;   
    std::cout << "compare(sub) == "   
        << sub.compare(sub) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
matched == true  
length == 3  
difference == 3  
range == aaa  
string == aaa  
compare("aab") == -1  
compare(string) == 1  
compare(sub) == 0  
```  
  
##  <a name="value_type"></a>  sub_match::value_type  
 El tipo de un elemento.  
  
```  
typedef typename iterator_traits<BidIt>::value_type value_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 La definición de tipo es un sinónimo de `iterator_traits<BidIt>::value_type`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__sub_match_value_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex rx("c(a*)|(b)");   
    std::cmatch mr;   
  
    std::regex_search("xcaaay", mr, rx);   
  
    std::csub_match sub = mr[1];   
    std::cout << "matched == " << std::boolalpha   
        << sub.matched << std::endl;   
    std::cout << "length == " << sub.length() << std::endl;   
  
    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);   
    std::cout << "difference == " << dif << std::endl;   
  
    std::csub_match::iterator first = sub.first;   
    std::csub_match::iterator last = sub.second;   
    std::cout << "range == " << std::string(first, last)   
        << std::endl;   
    std::cout << "string == " << sub << std::endl;   
  
    std::csub_match::value_type *ptr = "aab";   
    std::cout << "compare(\"aab\") == "   
        << sub.compare(ptr) << std::endl;   
    std::cout << "compare(string) == "   
        << sub.compare(std::string("AAA")) << std::endl;   
    std::cout << "compare(sub) == "   
        << sub.compare(sub) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
matched == true  
length == 3  
difference == 3  
range == aaa  
string == aaa  
compare("aab") == -1  
compare(string) == 1  
compare(sub) == 0  
```  
  
## <a name="see-also"></a>Vea también  
 [\<regex>](../standard-library/regex.md)   
 [sub_match](../standard-library/sub-match-class.md)
