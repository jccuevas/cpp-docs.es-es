---
title: regex_error (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
dev_langs:
- C++
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1cc2861da5e133754459d6721c3ce528eaab5897
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="regexerror-class"></a>regex_error (Clase)
Informa de un objeto basic_regex incorrecto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class regex_error  
 : public std::runtime_error {  
public:  
    explicit regex_error(regex_constants::error_code error);

    regex_constants::error_code code() const;

 
 };  
```  
  
## <a name="remarks"></a>Comentarios  
 La clase describe un objeto de excepción que se produce para notificar un error en la construcción o el uso de un objeto `basic_regex` .  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<regex>  
  
 **Espacio de nombres:** std  
  
##  <a name="code"></a> regex_error::code  
 Devuelve el código de error.  
  
```  
regex_constants::error_code code() const;
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve el valor que se pasó al constructor del objeto.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_error_code.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex_error paren(std::regex_constants::error_paren);   
  
    try   
        {   
        std::regex rx("(a");   
        }   
    catch (const std::regex_error& rerr)   
        {   
        std::cout << "regex error: "   
            << (rerr.code() == paren.code()   
                 "unbalanced parentheses" : "")   
            << std::endl;   
        }   
    catch (...)   
        {   
        std::cout << "unknown exception" << std::endl;   
        }   
  
    return (0);   
    }  
  
```  
  
```Output  
regex error: unbalanced parentheses  
```  
  
##  <a name="regex_error"></a> regex_error::regex_error  
 Construye el objeto.  
  
```  
regex_error(regex_constants::error_code error);
```  
  
### <a name="parameters"></a>Parámetros  
 `error`  
 Código de error.  
  
### <a name="remarks"></a>Comentarios  
 El constructor crea un objeto que contiene el valor `error`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__regex__regex_error_construct.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
int main()   
    {   
    std::regex_error paren(std::regex_constants::error_paren);   
  
    try   
        {   
        std::regex rx("(a");   
        }   
    catch (const std::regex_error& rerr)   
        {   
        std::cout << "regex error: "   
            << (rerr.code() == paren.code()   
                 "unbalanced parentheses" : "")   
            << std::endl;   
        }   
    catch (...)   
        {   
        std::cout << "unknown exception" << std::endl;   
        }   
  
    return (0);   
    }  
  
```  
  
```Output  
regex error: unbalanced parentheses  
```  
  
## <a name="see-also"></a>Vea también  
[\<regex>](../standard-library/regex.md)  
[regex_constants (Clase)](../standard-library/regex-constants-class.md)  
[Funciones de \<regex>](../standard-library/regex-functions.md)  
[regex_iterator (Clase)](../standard-library/regex-iterator-class.md)  
[Operadores de \<regex>](../standard-library/regex-operators.md)  
[regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md)  
[regex_traits (Clase)](../standard-library/regex-traits-class.md)  
[Definiciones de tipo \<regex>](../standard-library/regex-typedefs.md)  
