---
title: Enumeraciones [C++] | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- enum_cpp
dev_langs:
- C++
helpviewer_keywords:
- declarations, enumerations
- enumerators, declaring
- enum keyword [C++]
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: 081829db-5dca-411e-a53c-bffef315bcb3
caps.latest.revision: 27
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
ms.openlocfilehash: 5a28ef1a4330f3519a1084921d493b6595f31112
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="enumerations-c"></a>Enumeraciones [C++]
Una enumeración es un tipo definido por el usuario que consta de un conjunto de constantes enteras con nombre conocidas como enumeradores.  
  
> [!NOTE]
>  Este artículo trata el tipo `enum` del lenguaje C++ estándar de ISO y el tipo de ámbito (o fuertemente tipado) `enum class`, que se introdujo en C++11. Para obtener información sobre la `public enum class` o `private enum class` tipos en C++ / CLI y C++ / CX, consulte [clase enum](../windows/enum-class-cpp-component-extensions.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
// unscoped enum:  
enum [identifier] [: type]  
{enum-list};   
  
// scoped enum:  
enum [class|struct]   
[identifier] [: type]   
{enum-list};  
```  
  
```  
// Forward declaration of enumerations  (C++11):  
enum A : int; // non-scoped enum must have type specified
enum class B; // scoped enum defaults to int but ...
enum class C : short;  // ... may have any integral underlying type
```  
  
## <a name="parameters"></a>Parámetros  
 `identifier`  
 Nombre del tipo dado a la enumeración.  
  
 `type`  
 El tipo subyacente de los enumeradores; cada enumerador tiene el mismo tipo subyacente. Puede ser cualquier tipo entero.  
  
 `enum-list`  
 Una lista delimitada por comas de los enumeradores en la enumeración. Cada enumerador o nombre de variable en el ámbito debe ser único. Sin embargo, los valores pueden estar duplicados. En una enumeración sin ámbito, el ámbito es el ámbito adyacente; en una enumeración con ámbito, el ámbito es el mismo `enum-list`.  En una enumeración con ámbito, la lista puede estar vacía en vigor que define un nuevo tipo entero.
  
 `class`  
 Al usar esta palabra clave en la declaración, especifica que la enumeración se incluye en el ámbito, por lo que es necesario proporcionar un `identifier`. También puede usar la palabra clave `struct` en lugar de `class`, ya que son equivalentes semánticamente en este contexto.  
  
## <a name="enumerator-scope"></a>Ámbito de enumerador  
 Una enumeración proporciona contexto para describir un intervalo de valores que se representan como constantes con nombre, y también se denominan enumeradores. En los tipos de enumeración original de C y C++, los enumeradores incompletos están visibles en el ámbito en el que se declara enum. En enumeraciones de ámbito, el nombre del enumerador debe calificarse con el nombre de tipo enum. El ejemplo siguiente muestra esta diferencia básica entre las dos clases de enumeraciones:  
  
```cpp  
namespace CardGame_Scoped  
{  
    enum class Suit { Diamonds, Hearts, Clubs, Spades };  
  
    void PlayCard(Suit suit)  
    {  
        if (suit == Suit::Clubs) // Enumerator must be qualified by enum type  
        { /*...*/}  
    }  
}  
  
namespace CardGame_NonScoped  
{  
    enum Suit { Diamonds, Hearts, Clubs, Spades };  
  
    void PlayCard(Suit suit)  
    {  
        if (suit == Clubs) // Enumerator is visible without qualification  
        { /*...*/  
        }  
    }  
}  
```  
  
 A cada nombre de la enumeración se le asigna un valor entero que corresponde al lugar que ocupa en el orden de los valores de la enumeración. De forma predeterminada, al primer valor se asigna 0, al siguiente se asigna 1 y así sucesivamente, pero puede establecer explícitamente el valor de un enumerador, como se muestra aquí:  
  
```cpp  
enum Suit { Diamonds = 1, Hearts, Clubs, Spades };  
  
```  
  
 El enumerador `Diamonds` tiene asignado el valor `1`. Los enumeradores subsiguientes, si no se les asigna un valor explícito, reciben el valor del enumerador anterior más uno. En el ejemplo anterior, `Hearts` tendría el valor 2, `Clubs` tendría 3, etc.  
  
 Cada enumerador se trata como una constante y debe tener un nombre único dentro del ámbito, donde `enum` está definido (para las enumeraciones sin ámbito) o en la enumeración propia (para las enumeraciones de ámbito). Los valores especificados en los nombres no tienen que ser únicos. Por ejemplo, si la declaración de una enumeración sin ámbito `Suit` es esta:  
  
```cpp  
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };  
```  
  
 Los valores de `Diamonds`, `Hearts`, `Clubs` y `Spades` son 5, 6, 4 y 5, respectivamente. Observe que 5 se utiliza más de una vez; esto se permite incluso aunque pueda no ser intencionado. Estas reglas son las mismas para las enumeraciones de ámbito.  
  
 ## <a name="casting-rules"></a>Reglas de conversión  
  
 Las constantes de enumeración sin ámbito se pueden convertir implícitamente a `int`, pero `int` nunca es implícitamente convertible a un valor enum. El ejemplo siguiente muestra lo que ocurre si intenta asignar a `hand` un valor que no sea `Suit`:  
  
```cpp  
int account_num = 135692;  
Suit hand;  
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'  
  
```  
  
 Se requiere una conversión para convertir un `int` a un enumerador con ámbito o sin ámbito. Sin embargo, puede promover un enumerador sin ámbito a un valor entero sin una conversión.  
  
```cpp  
int account_num = Hearts; //OK if Hearts is in a unscoped enum  
```  
  
 Utilizar conversiones implícitas de esta manera puede provocar efectos secundarios imprevistos. Para ayudar a eliminar los errores de programación asociados a las enumeraciones sin ámbito, los valores de ámbito de enumeración están fuertemente tipados. Los enumeradores con ámbito deben calificarse por el nombre de tipo enumeración (identificador) y no pueden convertirse implícitamente, como se muestra en el ejemplo siguiente:  
  
```cpp  
namespace ScopedEnumConversions  
{  
    enum class Suit { Diamonds, Hearts, Clubs, Spades };  
  
    void AttemptConversions()  
    {  
        Suit hand;   
        hand = Clubs; // error C2065: 'Clubs' : undeclared identifier  
        hand = Suit::Clubs; //Correct.  
        int account_num = 135692;  
        hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'  
        hand = static_cast<Suit>(account_num); // OK, but probably a bug!!!  
  
        account_num = Suit::Hearts; // error C2440: '=' : cannot convert from 'Suit' to 'int'  
        account_num = static_cast<int>(Suit::Hearts); // OK  
}  
  
```  
  
 Observe que la línea `hand = account_num;` aún produce el error que se produce con enumeraciones sin ámbito, como se muestra anteriormente. Esto se permite con una conversión explícita. Sin embargo, con las enumeraciones con ámbito, la conversión que se ha intentado en la siguiente instrucción, `account_num = Suit::Hearts;`, ya no se permite sin una conversión explícita. 

## <a name="enums-with-no-enumerators"></a>Enumeraciones con ningún enumeradores
**Visual Studio 2017 15,3 y versiones posteriores** (disponible con [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): mediante la definición de una enumeración (normal o ámbito) con un tipo subyacente explícito y no los enumeradores, puede en vigor introducir un nuevo tipo de entero no tiene ninguna conversión implícita a ningún otro tipo. Mediante el uso de este tipo en lugar de su tipo subyacente integrado, puede eliminar la posibilidad de errores sutiles causados por involuntarias conversiones implícitas.  


```cpp
enum class byte : unsigned char { };
```

El nuevo tipo es una copia exacta del tipo subyacente y, por tanto, tiene la misma convención de llamada, lo que significa que puede utilizarse en ABIs sin una disminución del rendimiento. Se requiere ninguna conversión cuando se inicializan las variables del tipo mediante la inicialización de la lista de direct. En el ejemplo siguiente se muestra cómo inicializar enumeraciones con ningún enumeradores en diversos contextos:

```cpp
enum class byte : unsigned char { };

enum class E : int { };
E e1{ 0 };
E e2 = E{ 0 };

struct X 
{
    E e{ 0 };
    X() : e{ 0 } { }
};

E* p = new E{ 0 }; 

void f(E e) {};

int main()
{
    f(E{ 0 });
    byte i{ 42 };
    byte j = byte{ 42 };

    // unsigned char c = j; // C2440: 'initializing': cannot convert from 'byte' to 'unsigned char'
    return 0;
}
``` 
  
## <a name="see-also"></a>Vea también  
 [Declaraciones de enumeración de C](../c-language/c-enumeration-declarations.md)   
 [Palabras clave](../cpp/keywords-cpp.md)
