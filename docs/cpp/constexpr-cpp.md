---
title: constexpr (C++)
description: Guía de la C++ palabra clave Language constexpr.
ms.date: 01/28/2020
f1_keywords:
- constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
no-loc:
- constexpr
- const
- inline
- goto
- try
- if
- switch
- for
- while
ms.openlocfilehash: 4f34eef3217377ab50a2d80d42b5bea4b054c5be
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821784"
---
# <a name="opno-locconstexpr-c"></a>constexpr (C++)

La palabra clave **constexpr** se presentó en c++ 11 y se mejoró en c++ 14. Significa *expresión constante*. Como **const** , se puede aplicar a las variables: se genera un error del compilador cuando cualquier código intenta modificar el valor. A diferencia de **const** , **constexpr** se puede aplicar también a funciones y constructores de clase. **constexpr** indica que el valor, o el valor devuelto, es constante y, siempre que sea posible, se calcula en tiempo de compilación.

Se puede utilizar un valor entero **constexpr** siempre que se requiera un entero const, como en los argumentos de plantilla y en las declaraciones de matriz. Y cuando un valor se calcula en tiempo de compilación en lugar de en tiempo de ejecución, ayuda a que el programa se ejecute más rápido y use menos memoria.

Para limitar la complejidad de los cálculos constantes en tiempo de compilación y sus posibles impactos en el tiempo de compilación, el estándar de C++ 14 requiere que los tipos de expresiones constantes sean [tipos literales](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Sintaxis

> **constexpr** identificador *de tipo literal* **=** *Constant-Expression* **;** \
> **constexpr** identificador *de tipo literal* **{** *Constant-Expression* **}** **;** \
> **constexpr** *identificador de tipo literal* **(** *params* **)** **;** \
> **constexpr** *ctor* **(** *params* **)** **;**

## <a name="parameters"></a>Parameters

*params*\
Uno o más parámetros, cada uno de los cuales debe ser un tipo literal y debe ser una expresión constante.

## <a name="return-value"></a>Valor devuelto

Una variable o función **constexpr** debe devolver un [tipo literal](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="opno-locconstexpr-variables"></a>Variables constexpr

La diferencia principal entre las variables **const** y **constexpr** es que la inicialización de una variable **const** se puede diferir hasta el tiempo de ejecución. Una variable **constexpr** debe inicializarse en tiempo de compilación.  Se **constn** todas **constexpr** variables.

- Una variable se puede declarar con **constexpr** , cuando tiene un tipo literal y se inicializa. Si un constructor realiza la inicialización, el constructor debe declararse como **constexpr** .

- Una referencia puede declararse como **constexpr** cuando se cumplen estas condiciones: el objeto al que se hace referencia se inicializa con una expresión constante y cualquier conversión implícita invocada durante la inicialización también son expresiones constantes.

- Todas las declaraciones de una variable o función **constexpr** deben tener el especificador **constexpr** .

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a>funciones de constexpr

Una función **constexpr** es aquella cuyo valor devuelto es calculable en tiempo de compilación cuando el código utilizado lo requiere. El código de consumo requiere el valor devuelto en tiempo de compilación para inicializar una variable de **constexpr** , o para proporcionar un argumento de plantilla sin tipo. Cuando sus argumentos son **constexpr** valores, una función **constexpr** genera una constante en tiempo de compilación. Cuando se llama con argumentos que no son de **constexpr** , o cuando su valor no es necesario en tiempo de compilación, genera un valor en tiempo de ejecución como una función normal. (Este comportamiento dual evita tener que escribir **constexpr** y versiones no **constexpr** de la misma función).

Una **constexpr** función o constructor se **inline** implícitamente.

Las siguientes reglas se aplican a las funciones de constexpr:

- Una función **constexpr** debe aceptar y devolver solo [tipos literales](trivial-standard-layout-and-pod-types.md#literal_types).

- Una función **constexpr** puede ser recursiva.

- No puede ser [virtual](../cpp/virtual-cpp.md). Un constructor no se puede definir como **constexpr** cuando la clase envolvente tiene cualquier clase base virtual.

- El cuerpo se puede definir como `= default` o `= delete`.

- El cuerpo no puede contener instrucciones **goto** ni bloques de **try** .

- Una especialización explícita de una plantilla que no es de **constexpr** se puede declarar como **constexpr** :

- Una especialización explícita de una plantilla de **constexpr** no tiene que ser **constexpr** :

Las siguientes reglas se aplican a las funciones de **constexpr** en Visual Studio 2017 y versiones posteriores:

- Puede contener **if** y **switch** instrucciones, y todas las instrucciones de bucle, incluidas **for** , **for** basadas en intervalos, **while** y **while** .

- Puede contener declaraciones de variables locales, pero se debe inicializar la variable. Debe ser un tipo literal y no puede ser **estático** o local de subproceso. No es necesario que la variable declarada localmente sea **const** y puede ser mutada.

- No es necesario que una función miembro no**estática** **constexpr** sea implícitamente **const** .

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> En el depurador de Visual Studio, al depurar una compilación de depuración no optimizada, puede saber si una función **constexpr** se está evaluando en tiempo de compilación colocando un punto de interrupción dentro de ella. Si se alcanza el punto de interrupción, significa que se llamó a la función en tiempo de ejecución.  En caso contrario, significa que se llamó a la función en tiempo de compilación.

## <a name="extern-opno-locconstexpr"></a>constexpr extern

La opción del compilador [/Zc: externConstexpr](../build/reference/zc-externconstexpr.md) hace que el compilador aplique una [vinculación externa](../c-language/external-linkage.md) a las variables declaradas mediante **extern constexpr** . En versiones anteriores de Visual Studio, de forma predeterminada o cuando se especifica **/Zc: externConstexpr-** , Visual Studio aplica la vinculación interna a las variables de **constexpr** incluso cuando se usa la palabra clave **extern** . La opción **/Zc: externConstexpr** está disponible a partir de la actualización 15,6 de Visual Studio 2017 y está desactivada de forma predeterminada. La opción [/permissive-](../build/reference/permissive-standards-conformance.md) no habilita **/Zc: externConstexpr**.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra **constexpr** variables, funciones y un tipo definido por el usuario. En la última instrucción de `main()`, la función miembro **constexpr** `GetValue()` es una llamada en tiempo de ejecución porque no es necesario que el valor sea conocido en tiempo de compilación.

```cpp
// constexpr.cpp
// Compile with: cl /EHsc /W4 constexpr.cpp
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

// Compile-time computation of array length
template<typename T, int N>
constexpr int length(const T(&)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n * fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue() const
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;
}
```

## <a name="requirements"></a>Requisitos de

Visual Studio 2015 o posterior.

## <a name="see-also"></a>Vea también

[Declaraciones y definiciones](../cpp/declarations-and-definitions-cpp.md)\
[const](../cpp/const-cpp.md)
