---
title: constexpr (C++)
ms.date: 08/05/2019
f1_keywords:
- constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
ms.openlocfilehash: 5c98436f537b34b1c9050e057971938d48792db1
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821098"
---
# <a name="constexpr-c"></a>constexpr (C++)

La palabra clave **constexpr** se presentó en c++ 11 y se mejoró en c++ 14. Significa *expresión constante*. Como **const**, se puede aplicar a variables para que se produzca un error del compilador si algún código intenta modificar el valor. A diferencia de **const**, **constexpr** también se puede aplicar a funciones y constructores de clase. **constexpr** indica que el valor, o el valor devuelto, es constante y, si es posible, se calcula en tiempo de compilación.

Se puede usar un valor integral de **constexpr** siempre que se requiera un entero const, como en los argumentos de plantilla y las declaraciones de matriz. Y cuando un valor se puede calcular en tiempo de compilación en lugar de en tiempo de ejecución, puede ayudar a que el programa se ejecute más rápido y use menos memoria.

Para limitar la complejidad de los cálculos constantes en tiempo de compilación y sus posibles impactos en el tiempo de compilación, el estándar de C++ 14 requiere que los tipos de expresiones constantes sean [tipos literales](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Sintaxis

> **constexpr** *literal de tipo* *identificador* **=** *expresión-constante* **;** 
>  **constexpr** *literal de tipo* *identificador* **{** *expresión constante * **}** **;** 
>  **constexpr** *literal de tipo* *identificador* **(** *params* **)** **;** 
>  **constexpr** *ctor* **(** *params* **)** **;**

## <a name="parameters"></a>Parámetros

*params*<br/>
Uno o más parámetros, cada uno de los cuales debe ser un tipo literal y debe ser una expresión constante.

## <a name="return-value"></a>Valor devuelto

Una función o variable constexpr debe devolver un [tipo literal](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="constexpr-variables"></a>Variables constexpr

La principal diferencia entre las variables const y constexpr es que la inicialización de una variable const se puede diferir hasta el tiempo de ejecución. Una variable constexpr debe inicializarse en tiempo de compilación.  Todas las variables constexpr son const.

- Una variable se puede declarar con **constexpr**, si tiene un tipo literal y se inicializa. Si un constructor realiza la inicialización, el constructor debe declararse como **constexpr**.

- Una referencia puede declararse como constexpr si el objeto al que hace referencia se ha inicializado mediante una expresión constante y todas las conversiones implícitas que se invoquen durante la inicialización son también expresiones constantes.

- Todas las declaraciones de una variable o función **constexpr** deben tener el especificador **constexpr** .

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a>funciones constexpr

Una función **constexpr** es aquella cuyo valor devuelto se puede calcular en tiempo de compilación cuando el código utilizado lo requiere. El código de consumo requiere el valor devuelto en tiempo de compilación, por ejemplo, para inicializar una variable **constexpr** o proporcionar un argumento de plantilla sin tipo. Cuando sus argumentos son valores **constexpr** , una función **constexpr** genera una constante en tiempo de compilación. Cuando se llama con argumentos que no son**constexpr** , o cuando su valor no es necesario en tiempo de compilación, genera un valor en tiempo de ejecución como una función normal. (Este comportamiento dual evita tener que escribir las versiones **constexpr** y no**constexpr** de la misma función).

Una función o un constructor **constexpr** está implícitamente **alineado**.

Las siguientes reglas se aplican a las funciones constexpr:

- Una función **constexpr** debe aceptar y devolver solo [tipos literales](trivial-standard-layout-and-pod-types.md#literal_types).

- Una función **constexpr** puede ser recursiva.

- No puede ser [virtual](../cpp/virtual-cpp.md). Un constructor no se puede definir como constexpr si la clase envolvente tiene clases base virtuales.

- El cuerpo se puede definir como `= default` o `= delete`.

- El cuerpo no puede contener instrucciones **goto** ni bloques try.

- Una especialización explícita de una plantilla no constexpr se puede declarar como **constexpr**:

- Una especialización explícita de una plantilla **constexpr** no tiene que ser también **constexpr**:

Las siguientes reglas se aplican a las funciones **constexpr** en Visual Studio 2017 y versiones posteriores:

- Puede contener instrucciones **If** y **Switch** , así como todas las instrucciones **de**bucle, como for, basada en intervalo para, **While**y **do-while**.

- Puede contener declaraciones de variables locales, pero la variable debe inicializarse, debe ser un tipo literal y no puede ser estática o de subproceso local. No es necesario que la variable declarada localmente sea const y puede mutar.

- No es necesario que una función miembro no estática constexpr sea implícitamente const.

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

## <a name="extern-constexpr"></a>externo constexpr

La opción del compilador [/Zc: externConstexpr](../build/reference/zc-externconstexpr.md) hace que el compilador aplique una [vinculación externa](../c-language/external-linkage.md) a las variables declaradas mediante **extern constexpr**. En versiones anteriores de Visual Studio, y de forma predeterminada o si se especifica **/Zc: externConstexpr-** , Visual Studio aplica la vinculación interna a las variables **constexpr** incluso si se usa la palabra clave **extern** . La opción **/Zc: externConstexpr** está disponible a partir de la actualización 15,6 de Visual Studio 2017 y está desactivada de forma predeterminada. La opción/permissive-no habilita **/Zc: externConstexpr**.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran variables, funciones y un tipo definido por el usuario. En la última instrucción de Main (), la función miembro **Constexpr** GetValue () es una llamada en tiempo de ejecución porque no es necesario que el valor sea conocido en tiempo de compilación.

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

## <a name="requirements"></a>Requisitos

Visual Studio 2015 o posterior.

## <a name="see-also"></a>Vea también

[Declaraciones y definiciones](../cpp/declarations-and-definitions-cpp.md)\
[const](../cpp/const-cpp.md)
