---
title: static_assert | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- static_assert_cpp
dev_langs:
- C++
helpviewer_keywords:
- C++ keywords, static_assert
- C2338
- assertions [C++], static_assert
- static_assert
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc51fab2dade4c6bed0456dd353258df82722de5
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944751"
---
# <a name="staticassert"></a>static_assert
Comprueba una aserción de software en tiempo de compilación. Si la expresión constante especificada es FALSE, el compilador muestra el mensaje especificado, si se proporciona uno, y se produce un error en la compilación con el error C2338; en caso contrario, la declaración no tiene ningún efecto.  
  
## <a name="syntax"></a>Sintaxis  
  
```   
static_assert( constant-expression, string-literal );  

**Visual Studio 2017 and later:**
static_assert( constant-expression ); 
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`constant-expression`|Una expresión constante entera que se puede convertir en un valor booleano.<br /><br /> Si la expresión evaluada es cero (false), aparecerá el parámetro `string-literal` y se producirá un error de compilación. Si la expresión es distinto de cero (true), el **static_assert** declaración no tiene ningún efecto.|  
|`string-literal`|Un mensaje que se muestra si el parámetro `constant-expression` es cero. El mensaje es una cadena de caracteres en el [basar el juego de caracteres](../c-language/ascii-character-set.md) de que el compilador; es decir, no [caracteres anchos o multibyte](../c-language/multibyte-and-wide-characters.md).|  
  
## <a name="remarks"></a>Comentarios  
 El `constant-expression` parámetro de un **static_assert** declaración representa un *aserción de software*. Una aserción de software especifica una condición que se espera que sea cierta (valor true) en un determinado punto del programa. Si la condición es true, el **static_assert** declaración no tiene ningún efecto. Si la condición es false, se produce un error en la aserción, el compilador muestra el mensaje en el parámetro `string-literal` y se produce un error de compilación. En Visual Studio 2017 y versiones posteriores, el parámetro de literal de cadena es opcional. 
  
 El **static_assert** declaración comprueba una aserción de software en tiempo de compilación. En cambio, el [assert (macro), _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) macro comprueba una aserción de software en tiempo de ejecución y genera un gasto de tiempo de ejecución de espacio o tiempo. El **static_assert** declaración es especialmente útil para depurar plantillas, porque los argumentos de plantilla se pueden incluir en el `constant-expression` parámetro.  
  
 El compilador examina la **static_assert** declaración errores de sintaxis cuando se encuentra la declaración. El compilador evalúa el parámetro `constant-expression` inmediatamente si este no depende de un parámetro de plantilla. De lo contrario, el compilador evalúa el parámetro `constant-expression` cuando se crea una instancia de la plantilla. Por consiguiente, el compilador puede emitir un mensaje de diagnóstico una vez cuando se encuentra la declaración y otra vez cuando se crea una instancia de la plantilla.  
  
 Puede usar el **static_assert** palabra clave en el espacio de nombres, clase o ámbito de bloque. (El **static_assert** palabra clave es técnicamente una declaración, aunque no introduce un nuevo nombre en el programa, porque se puede usar en el ámbito del espacio de nombres.)  
  
## <a name="description"></a>Descripción  
 En el ejemplo siguiente, la **static_assert** declaración tiene ámbito de espacio de nombres. Dado que el compilador conoce el tamaño del tipo `void *`, la expresión se evalúa inmediatamente.  
  
## <a name="example"></a>Ejemplo  
  
```cpp 
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");  
```  
  
## <a name="description"></a>Descripción  
 En el ejemplo siguiente, la **static_assert** declaración tiene ámbito de clase. El **static_assert** comprueba que un parámetro de plantilla es un *datos antiguos* tipo (POD). El compilador examina la **static_assert** declaración cuando se declara, pero no evalúa el `constant-expression` parámetro hasta el `basic_string` se crea una instancia de plantilla de clase en `main()`.  
  
## <a name="example"></a>Ejemplo  
  
```cpp 
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
 En el ejemplo siguiente, la **static_assert** declaración tiene ámbito de bloque. El **static_assert** comprueba que el tamaño de la estructura de VMPage sea igual que el valor de pagesize de la memoria virtual del sistema.  
  
## <a name="example"></a>Ejemplo  
  
```cpp 
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