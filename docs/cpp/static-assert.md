---
title: static_assert | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- C2338
- static_assert_cpp
- static_assert
dev_langs:
- C++
helpviewer_keywords:
- C++ keywords, static_assert
- C2338
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 1428d890fe079c7ac1fce175686e9776f9c21746
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="staticassert"></a>static_assert
Comprueba una aserción de software en tiempo de compilación. Si la expresión constante especificada es `false`, el compilador muestra el mensaje especificado, si se proporciona uno y la compilación se produce un error c2338 en; en caso contrario, la declaración no tiene ningún efecto.  
  
## <a name="syntax"></a>Sintaxis  
  
```   
static_assert( constant-expression, string-literal );  

**Visual Studio 2017 and later:**
static_assert( constant-expression ); 
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`constant-expression`|Una expresión constante entera que se puede convertir en un valor booleano.<br /><br /> Si la expresión evaluada es cero (false), aparecerá el parámetro `string-literal` y se producirá un error de compilación. Si la expresión es distinta de cero (true), la declaración `static_assert` no tiene ningún efecto.|  
|`string-literal`|Un mensaje que se muestra si el parámetro `constant-expression` es cero. El mensaje es una cadena de caracteres en el [basar el juego de caracteres](../c-language/ascii-character-set.md) del compilador; es decir, no [caracteres anchos o multibyte](../c-language/multibyte-and-wide-characters.md).|  
  
## <a name="remarks"></a>Comentarios  
 El `constant-expression` parámetro de un `static_assert` declaración representa un *aserción de software*. Una aserción de software especifica una condición que se espera que sea cierta (valor true) en un determinado punto del programa. Si la condición es true, la declaración `static_assert` no tiene ningún efecto. Si la condición es false, se produce un error en la aserción, el compilador muestra el mensaje en el parámetro `string-literal` y se produce un error de compilación. En Visual Studio de 2017 y versiones posteriores, el parámetro de literal de cadena es opcional. 
  
 La declaración `static_assert` comprueba una aserción de software en tiempo de compilación. En cambio, el [assert (macro), _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) macro comprueba una aserción de software en tiempo de ejecución y genera un gasto de tiempo de ejecución de espacio o tiempo. La declaración `static_assert` resulta especialmente útil para depurar plantillas, porque los argumentos de plantilla se pueden incluir en el parámetro `constant-expression`.  
  
 El compilador examina si hay errores de sintaxis en la declaración `static_assert` al encontrar dicha declaración. El compilador evalúa el parámetro `constant-expression` inmediatamente si este no depende de un parámetro de plantilla. De lo contrario, el compilador evalúa el parámetro `constant-expression` cuando se crea una instancia de la plantilla. Por consiguiente, el compilador puede emitir un mensaje de diagnóstico una vez cuando se encuentra la declaración y otra vez cuando se crea una instancia de la plantilla.  
  
 Puede usar la palabra clave `static_assert` en el ámbito de espacio de nombres, clase o bloque. (La palabra clave `static_assert` es técnicamente una declaración, aunque no introduce un nuevo nombre en el programa, porque se puede utilizar en el ámbito de espacio de nombres).  
  
## <a name="description"></a>Descripción  
 En el ejemplo siguiente, la declaración `static_assert` tiene ámbito de espacio de nombres. Dado que el compilador conoce el tamaño del tipo `void *`, la expresión se evalúa inmediatamente.  
  
## <a name="example"></a>Ejemplo  
  
```  
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");  
```  
  
## <a name="description"></a>Descripción  
 En el ejemplo siguiente, la declaración `static_assert` tiene ámbito de clase. El `static_assert` comprueba que un parámetro de plantilla es una *datos antiguos sin formato* tipo (POD). El compilador examina la declaración `static_assert` cuando se declara, pero no evalúa el parámetro `constant-expression` hasta que se crean instancias de la plantilla de clase `basic_string` en `main()`.  
  
## <a name="example"></a>Ejemplo  
  
```  
#include <type_traits>  
#include <iosfwd>  
namespace std {  
template <class CharT, class Traits = std::char_traits<CharT> >  
class basic_string {  
    static_assert(std::is_pod<CharT>::value,  
                  "Template argument CharT must be a POD type in class template basic_string");  
    // ...  
    };  
}  
  
struct NonPOD {  
    NonPOD(const NonPOD &) {}  
    virtual ~NonPOD() {}  
};  
  
int main()  
{  
    std::basic_string<char> bs;  
}  
```  
  
## <a name="description"></a>Descripción  
 En el ejemplo siguiente, la declaración `static_assert` tiene ámbito de bloque. `static_assert` comprueba que el tamaño de la estructura de VMPage sea igual al valor pagesize de la memoria virtual del sistema.  
  
## <a name="example"></a>Ejemplo  
  
```  
#include <sys/param.h> // defines PAGESIZE  
class VMMClient {  
public:  
    struct VMPage { // ...   
           };  
    int check_pagesize() {  
    static_assert(sizeof(VMPage) == PAGESIZE,  
        "Struct VMPage must be the same size as a system virtual memory page.");  
    // ...  
    }  
// ...  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [Aserción y mensajes proporcionados por el usuario (C++)](../cpp/assertion-and-user-supplied-messages-cpp.md)   
 [#error (directiva) (C/C ++)](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [Plantillas](../cpp/templates-cpp.md)   
 [Juego de caracteres ASCII](../c-language/ascii-character-set.md)   
 [Declaraciones y definiciones](declarations-and-definitions-cpp.md)
