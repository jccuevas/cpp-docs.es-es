---
title: 'Operador de resolución de ámbito::: | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '::'
dev_langs:
- C++
helpviewer_keywords:
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- ':: operator'
ms.assetid: fd5de9d3-c716-4e12-bae9-03a16fd79a50
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7caea3a32c0bb983518f7610918c78c8c31c63a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="scope-resolution-operator-"></a>Operador de resolución de ámbito: ::
El operador de resolución de ámbito `::` se usa para identificar los identificadores usados en distintos ámbitos y eliminar la ambigüedad entre ellos. Para obtener más información acerca del ámbito, consulte [ámbito](../cpp/scope-visual-cpp.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
:: identifier  
class-name :: identifier  
namespace :: identifier  
enum class :: identifier  
enum struct :: identifier  
```  
  
## <a name="remarks"></a>Comentarios  
 El `identifier` puede ser una variable, una función o un valor de enumeración.  
  
## <a name="with-classes-and-namespaces"></a>Con clases y espacios de nombres  
 En el ejemplo siguiente se muestra cómo se usa el operador de resolución con clases y espacios de nombres:  
  
```cpp  
namespace NamespaceA{  
    int x;  
    class ClassA {  
    public:  
        int x;  
    };  
}  
  
int main() {  
  
    // A namespace name used to disambiguate  
    NamespaceA::x = 1;  
  
    // A class name used to disambiguate  
    NamespaceA::ClassA a1;  
    a1.x = 2;  
  
}  
  
```  
  
 Un operador de resolución de ámbito sin un calificador de ámbito hace referencia al espacio de nombres global.  
  
```cpp  
namespace NamespaceA{  
    int x;  
}  
  
int x;   
  
int main() {  
    int x;  
  
    // the x in main()  
    x = 0;   
    // The x in the global namespace  
    ::x = 1;   
  
    // The x in the A namespace  
    NamespaceA::x = 2;   
}  
```  
  
 El operador de resolución de ámbito se puede usar para identificar a un miembro de un espacio de nombres o para identificar un espacio de nombres que menciona el espacio de nombres del miembro en una directiva de uso. En el ejemplo siguiente, se puede usar `NamespaceC` para calificar `ClassB` a pesar de que `ClassB` se declaró en el espacio de nombres `NamespaceB`, ya que una directiva de uso mencionó `NamespaceB` en `NamespaceC`.  
  
```cpp  
namespace NamespaceB {  
    class ClassB {  
    public:  
        int x;  
    };  
}  
  
namespace NamespaceC{  
    using namespace B;  
  
}  
int main() {  
    NamespaceB::ClassB c_b;  
    NamespaceC::ClassB c_c;  
  
    c_b.x = 3;  
    c_c.x = 4;  
}  
  
```  
  
 Se pueden usar cadenas de operadores de resolución de ámbito. En el ejemplo siguiente, `NamespaceD::NamespaceD1` identifica el espacio de nombres anidado `NamespaceD1` y `NamespaceE::ClassE::ClassE1` identifica la clase anidada `ClassE1`.  
  
```cpp  
namespace NamespaceD{  
    namespace NamespaceD1{  
        int x;  
    }  
}  
  
namespace NamespaceE{  
  
    class ClassE{  
    public:  
        class ClassE1{  
        public:  
            int x;  
        };  
    };  
}  
  
int main() {  
    NamespaceD:: NamespaceD1::x = 6;  
    NamespaceE::ClassE::ClassE1 e1;  
    e1.x = 7  ;  
}  
  
```  
  
## <a name="with-static-members"></a>Con miembros estáticos  
 Debe usar el operador de resolución de ámbito para llamar a miembros estáticos de clases.  
  
```cpp  
class ClassG {  
public:  
    static int get_x() { return x;}  
    static int x;  
};  
  
int ClassG::x = 6;  
  
int main() {  
  
    int gx1 = ClassG::x;  
    int gx2 = ClassG::get_x();   
}  
  
```  
  
## <a name="with-scoped-enumerations"></a>Con enumeraciones de ámbito  
 El operador de resolución de ámbito también se utiliza con los valores de una enumeración de ámbito [declaraciones de enumeración](../cpp/enumerations-cpp.md), como en el ejemplo siguiente:  
  
```cpp  
enum class EnumA{  
    First,  
    Second,  
    Third  
};  
  
int main() {  
  
    EnumA enum_value = EnumA::First;  
}  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Los operadores integrados de C++, prioridad y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Espacios de nombres](../cpp/namespaces-cpp.md)   