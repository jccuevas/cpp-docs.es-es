---
title: "static_assert | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "C2338"
  - "static_assert_cpp"
  - "static_assert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aserciones [C++], static_assert"
  - "palabras clave de C++, static_assert"
  - "C2338"
  - "static_assert"
ms.assetid: 28dd3668-e78c-4de8-ba68-552084743426
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# static_assert
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba una aserción de software en tiempo de compilación.  Si la expresión constante especificada es `false`, el compilador muestra el mensaje especificado y se produce un error C2338 en la compilación; de lo contrario, la declaración no tiene ningún efecto.  
  
## Sintaxis  
  
```  
static_assert(   
    constant-expression,   
    string-literal   
);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`constant-expression`|Una expresión constante entera que se puede convertir en un valor booleano.<br /><br /> Si la expresión evaluada es cero \(false\), aparecerá el parámetro `string-literal` y se producirá un error de compilación.  Si la expresión es distinta de cero \(true\), la declaración `static_assert` no tiene ningún efecto.|  
|`string-literal`|Un mensaje que se muestra si el parámetro `constant-expression` es cero.  El mensaje es una cadena de caracteres del [juego de caracteres base](../c-language/ascii-character-set.md) del compilador; es decir, no de [caracteres anchos o multibyte](../c-language/multibyte-and-wide-characters.md).|  
  
## Comentarios  
 El parámetro `constant-expression` de una declaración `static_assert` representa una *aserción de software*.  Una aserción de software especifica una condición que se espera que sea cierta \(valor true\) en un determinado punto del programa.  Si la condición es true, la declaración `static_assert` no tiene ningún efecto.  Si la condición es false, se produce un error en la aserción, el compilador muestra el mensaje en el parámetro `string-literal` y se produce un error de compilación.  
  
 La declaración `static_assert` comprueba una aserción de software en tiempo de compilación.  En cambio, la macro [assert \(macro\), \_assert, \_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) comprueba una aserción de software en tiempo de ejecución y produce un costo de espacio o tiempo en tiempo de ejecución.  La declaración `static_assert` resulta especialmente útil para depurar plantillas, porque los argumentos de plantilla se pueden incluir en el parámetro `constant-expression`.  
  
 El compilador examina si hay errores de sintaxis en la declaración `static_assert` al encontrar dicha declaración.  El compilador evalúa el parámetro `constant-expression` inmediatamente si este no depende de un parámetro de plantilla.  De lo contrario, el compilador evalúa el parámetro `constant-expression` cuando se crea una instancia de la plantilla.  Por consiguiente, el compilador puede emitir un mensaje de diagnóstico una vez cuando se encuentra la declaración y otra vez cuando se crea una instancia de la plantilla.  
  
 Puede usar la palabra clave `static_assert` en el ámbito de espacio de nombres, clase o bloque. \(La palabra clave `static_assert` es técnicamente una declaración, aunque no introduce un nuevo nombre en el programa, porque se puede utilizar en el ámbito de espacio de nombres\).  
  
## Descripción  
 En el ejemplo siguiente, la declaración `static_assert` tiene ámbito de espacio de nombres.  Dado que el compilador conoce el tamaño del tipo `void *`, la expresión se evalúa inmediatamente.  
  
## Ejemplo  
  
```  
static_assert(sizeof(void *) == 4, "64-bit code generation is not supported.");  
```  
  
## Descripción  
 En el ejemplo siguiente, la declaración `static_assert` tiene ámbito de clase.  `static_assert` comprueba si un parámetro de plantilla es de un tipo de *datos antiguos de nivel* \(POD\).  El compilador examina la declaración `static_assert` cuando se declara, pero no evalúa el parámetro `constant-expression` hasta que se crean instancias de la plantilla de clase `basic_string` en `main()`.  
  
## Ejemplo  
  
```  
#include <type_traits>  
#include <iosfwd>  
namespace std {  
template <class CharT, class Traits = std::char_traits<CharT> >  
class basic_string {  
    static_assert(tr1::is_pod<CharT>::value,  
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
  
## Descripción  
 En el ejemplo siguiente, la declaración `static_assert` tiene ámbito de bloque.  `static_assert` comprueba que el tamaño de la estructura de VMPage sea igual al valor pagesize de la memoria virtual del sistema.  
  
## Ejemplo  
  
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
  
## Vea también  
 [Aserción y mensajes proporcionados por el usuario \(C\+\+\)](../cpp/assertion-and-user-supplied-messages-cpp.md)   
 [\#error \(Directiva\)](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert \(macro\), \_assert, \_wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [Plantillas](../cpp/templates-cpp.md)   
 [Juego de caracteres ASCII](../c-language/ascii-character-set.md)   
 [Declaraciones](../misc/declarations.md)