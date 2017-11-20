---
title: constexpr (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: constexpr_cpp
dev_langs: C++
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4ff111b73d81fd3c008e53db0f5e41b82f9e3753
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="constexpr-c"></a>constexpr (C++)
La palabra clave `constexpr` se introdujo en C++11 y se mejoró en C++14. Significa *expresión constante*. Al igual que `const`, se puede aplicar a variables para que se genere un error del compilador si cualquier código intenta modificar el valor. A diferencia de `const`, `constexpr` también se puede aplicar a los constructores de clase y funciones. `constexpr` indica que el valor, o el valor devuelto, es una constante y, si es posible, se calculará en tiempo de compilación.  Un valor entero `constexpr` se puede utilizar donde se requiera un entero const, como es el caso de las declaraciones de matrices y los argumentos de plantillas. Y cuando un valor se puede calcular en tiempo de compilación en lugar de tiempo de ejecución, puede ayudar a su programa ejecutarse con mayor rapidez y utilizan menos memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
constexpr  literal-type  identifier = constant-expression;
constexpr  literal-type  identifier { constant-expression };
constexpr literal-type identifier(params );
constexpr ctor (params);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `params`  
 Uno o varios parámetros que deben ser un tipo literal (como se muestra a continuación) y que debe ser en sí mismo una expresión constante.  
  
## <a name="return-value"></a>Valor devuelto  
 Una función o variable constexpr debe devolver uno de los tipos literales, como se muestra a continuación.  
  
## <a name="literal-types"></a>Tipos literales  
 Para limitar la complejidad del cálculo de constantes en tiempo de compilación, así como su posible impacto en el tiempo de compilación, el estándar de C++14 requiere que los tipos implicados en expresiones constantes estén restringidos a tipos literales. Un tipo literal es aquel cuyo diseño se puede determinar en tiempo de compilación. Estos son los tipos literales:  
  
1.  void  
  
2.  tipos escalares  
  
3.  referencias  
  
4.  Matrices de void, tipos escalares o referencias.  
  
5.  Una clase que tiene un destructor trivial y uno o varios constructores constexpr que no son constructores de movimiento ni de copias. Además, todos sus miembros de datos no estáticos y sus clases base deben ser tipos literales y no volátiles.  
  
## <a name="constexpr-variables"></a>Variables constexpr  
 La principal diferencia entre las variables const y constexpr reside en que la inicialización de una variable const puede aplazarse hasta el tiempo de ejecución, mientras que una variable constexpr debe inicializarse en tiempo de compilación.  Todas las variables constexpr son const.  

-  Una variable se puede declarar con `constexpr` si tiene un tipo literal y está inicializada. Si el constructor realiza la inicialización, este debe declararse como `constexpr`.  
  
-   Una referencia puede declararse como constexpr si el objeto al que hace referencia se ha inicializado mediante una expresión constante y todas las conversiones implícitas que se invoquen durante la inicialización son también expresiones constantes.  
  
-   Todas las declaraciones de una función o variable `constexpr` deben tener el especificador `constexpr`.  
  
 
  
 
  
```cpp  
constexpr float x = 42.0;  
constexpr float y{108};  
constexpr float z = exp(5, 3);  
constexpr int i; // Error! Not initialized  
int j = 0;  
constexpr int k = j + 1; //Error! j not a constant expression  
```  
  
## <a name="constexpr-functions"></a>Funciones constexpr  
 Una función `constexpr` es aquella cuyo valor devuelto se puede calcular durante la compilación cuando el código usado lo requiere.  Cuando sus argumentos son valores `constexpr` y el código usado requiere el valor devuelto en tiempo de compilación, como por ejemplo para inicializar una variable `constexpr` o proporcionar un argumento de plantilla sin tipo, produce una constante en tiempo de compilación. Cuando se llama con argumentos que no sean `constexpr` o cuando su valor no se requiere en tiempo de compilación, genera un valor en tiempo de ejecución como una función normal.  (Este doble comportamiento le evita tener que escribir versiones `constexpr` y que no sean `constexpr` de la misma función).  
 
 Un constructor o una función `constexpr` es implícitamente `inline`. 
 
 Las siguientes reglas se aplican a las funciones de constexpr:

- Una función `constexpr` debe aceptar y devolver únicamente tipos literales. 

- Una función `constexpr` puede ser recursiva. 

- No puede ser [virtuales](../cpp/virtual-cpp.md). A un constructor no puede definirse como constexpr si la clase envolvente tiene alguna clase base virtual.

- El cuerpo se puede definir como `= default` o `= delete`. 

- No puede tener el cuerpo de `goto` instrucciones o bloques try. 

- Una especialización explícita de una plantilla que no sea constexpr no se puede declarar como `constexpr`:  
  
- Una especialización explícita de una plantilla `constexpr` no tiene que ser también `constexpr`: 


<!--conformance note-->
Las siguientes reglas se aplican a las funciones de constexpr en Visual Studio de 2017 y versiones posteriores: 

- Puede contener si y cambiar las instrucciones y todas las instrucciones bucles, incluidos, basada en intervalo, mientras y hacer-mientras
    
- Puede contener declaraciones de variables locales, pero la variable debe inicializarse, debe ser un tipo literal y no puede ser estáticas o locales de subproceso. La variable declarados localmente no tiene que ser const y puede mutar.

- Una función miembro no estático de constexpr no tiene que ser implícitamente const.

  
```cpp  
constexpr float exp(float x, int n)  
{  
    return n == 0 ? 1 :  
        n % 2 == 0 ? exp(x * x, n / 2) :  
        exp(x * x, (n - 1) / 2) * x;  
};  
```  
  
> [!TIP]
>  Nota: En el depurador de Visual Studio, puede indicar si una función `constexpr` se evalúa en tiempo de compilación colocando un punto de interrupción en su interior. Si se alcanza el punto de interrupción, significa que se llamó a la función en tiempo de ejecución.  En caso contrario, significa que se llamó a la función en tiempo de compilación.  
  
 
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestran funciones, un tipo definido por usuario y variables `constexpr`. Tenga en cuenta que en la última instrucción en main(), la función miembro `constexpr` GetValue() es una llamada en tiempo de ejecución porque no es necesario conocer el valor en tiempo de compilación.  
  
```  
#include <iostream>  
  
using namespace std;  
  
// Pass by value   
constexpr float exp(float x, int n)  
{  
    return n == 0 ? 1 :  
        n % 2 == 0 ? exp(x * x, n / 2) :  
        exp(x * x, (n - 1) / 2) * x;  
};  
  
// Pass by reference  
constexpr float exp2(const float& x, const int& n)  
{  
    return n == 0 ? 1 :  
        n % 2 == 0 ? exp2(x * x, n / 2) :  
        exp2(x * x, (n - 1) / 2) * x;  
};  
  
// Compile time computation of array length  
template<typename T, int N>  
constexpr int length(const T(&ary)[N])   
{   
    return N;   
}   
  
// Recursive constexpr function  
constexpr int fac(int n)  
{   
    return n == 1 ? 1 : n*fac(n - 1);   
}  
  
// User-defined type  
class Foo  
{  
public:  
    constexpr explicit Foo(int i) : _i(i) {}  
    constexpr int GetValue()  
    {  
        return _i;  
    }  
private:  
    int _i;  
};  
  
int main()  
{  
    //foo is const:  
    constexpr Foo foo(5);   
    // foo = Foo(6); //Error!  
  
    //Compile time:  
    constexpr float x = exp(5, 3);   
    constexpr float y { exp(2, 5) };  
    constexpr int val = foo.GetValue();   
    constexpr int f5 = fac(5);  
    const int nums[] { 1, 2, 3, 4 };  
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };  
  
    //Run time:   
    cout << "The value of foo is " << foo.GetValue() << endl;   
  
}  
  
```  
  
## <a name="requirements"></a>Requisitos  
 Visual Studio 2015  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones y definiciones](../cpp/declarations-and-definitions-cpp.md)   
 [const](../cpp/const-cpp.md)