---
title: Usar expresiones lambda, objetos de función y funciones restringidas
ms.date: 11/04/2016
ms.assetid: 25346cc9-869d-4ada-aad3-e2228cad3d6c
ms.openlocfilehash: 819605eac6408751456479fbc3daa38aac1418ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629403"
---
# <a name="using-lambdas-function-objects-and-restricted-functions"></a>Usar expresiones lambda, objetos de función y funciones restringidas

El código de C++ AMP que se desea ejecutar en el Acelerador se especifica como un argumento en una llamada a la [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) método. Puede proporcionar una expresión lambda o un objeto de función (functor) como ese argumento. Además, el objeto de función o expresión lambda puede llamar a una función con restricción AMP de C++. En este tema utiliza un algoritmo de suma de la matriz para demostrar las expresiones lambda, objetos de función y funciones restringidas. El ejemplo siguiente muestra el algoritmo sin código AMP de C++. Se crean dos dimensiones 1 matrices de igual longitud. Los elementos enteros correspondientes se agregan y se almacenan en una tercera matriz dimensional 1. No se utiliza C++ AMP.

```cpp
void CpuMethod() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    for (int idx = 0; idx <5; idx++)
    {
        sumCPP[idx] = aCPP[idx] + bCPP[idx];
    }

    for (int idx = 0; idx <5; idx++)
    {
        std::cout <<sumCPP[idx] <<"\n";
    }
}
```

## <a name="lambda-expression"></a>Expresión lambda

Usar una expresión lambda es la forma más directa al utilizar C++ AMP para reescribir el código.

```cpp
void AddArraysWithLambda() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    array_view<const int, 1> a(5, aCPP);

    array_view<const int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
             sum[idx] = a[idx] + b[idx];
        });

    for (int i = 0; i <5; i++) {
        std::cout <<sum[i] <<"\n";
    }
}
```

La expresión lambda debe incluir un parámetro de indexación y debe incluir `restrict(amp)`. En el ejemplo, el [array_view](../../parallel/amp/reference/array-view-class.md) `sum` objeto tiene un rango de 1. Por lo tanto, el parámetro de la expresión lambda es una [índice](../../parallel/amp/reference/index-class.md) objeto que tiene rango 1. En tiempo de ejecución, la expresión lambda se ejecuta una vez para cada elemento de la [array_view](../../parallel/amp/reference/array-view-class.md) objeto. Para obtener más información, consulte [sintaxis de expresión Lambda](../../cpp/lambda-expression-syntax.md).

## <a name="function-object"></a>Function (Objeto)

Puede factorizar el código del acelerador en un objeto de función.

```cpp
class AdditionFunctionObject
{
public:
    AdditionFunctionObject(const array_view<int, 1>& a,
    const array_view<int, 1>& b,
    const array_view<int, 1>& sum)
    : a(a), b(b), sum(sum)
    {
    }

    void operator()(index<1> idx) restrict(amp)
    {
        sum[idx] = a[idx] + b[idx];
    }

private:
    array_view<int, 1> a;
    array_view<int, 1> b;
    array_view<int, 1> sum;
};

void AddArraysWithFunctionObject() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    array_view<const int, 1> a(5, aCPP);

    array_view<const int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

    parallel_for_each(
        sum.extent,
        AdditionFunctionObject(a, b, sum));

    for (int i = 0; i <5; i++) {
        std::cout <<sum[i] <<"\n";
    }
}
```

El objeto de función debe incluir un constructor y debe incluir una sobrecarga del operador de llamada de función. El operador de llamada de función debe incluir un parámetro de indexación. Una instancia del objeto de función se pasa como segundo argumento de la [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) método. En este ejemplo, tres [array_view](../../parallel/amp/reference/array-view-class.md) objetos que se pasan al constructor de objeto de función. El [array_view](../../parallel/amp/reference/array-view-class.md) objeto `sum` tiene un rango de 1. Por lo tanto, el parámetro del operador de llamada de función es un [índice](../../parallel/amp/reference/index-class.md) objeto que tiene rango 1. En tiempo de ejecución, la función se ejecuta una vez para cada elemento de la [array_view](../../parallel/amp/reference/array-view-class.md) objeto. Para obtener más información, consulte [llamadas a función](../../cpp/function-call-cpp.md) y [objetos de función en la biblioteca estándar de C++](../../standard-library/function-objects-in-the-stl.md).

## <a name="c-amp-restricted-function"></a>Función de restricción de AMP de C++

Puede factorizar el código del Acelerador mediante la creación de una función restringida y llamarlo desde una expresión lambda o un objeto de función. El ejemplo de código siguiente muestra cómo llamar a una función restringida desde una expresión lambda.

```cpp
void AddElementsWithRestrictedFunction(index<1> idx, array_view<int, 1> sum, array_view<int, 1> a, array_view<int, 1> b) restrict(amp)
{
    sum[idx] = a[idx] + b[idx];
}

void AddArraysWithFunction() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    array_view<int, 1> a(5, aCPP);

    array_view<int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
            AddElementsWithRestrictedFunction(idx, sum, a, b);
        });

    for (int i = 0; i <5; i++) {
        std::cout <<sum[i] <<"\n";
    }
}
```

La función restringida debe incluir `restrict(amp)` y ajustarse a las restricciones que se describen en [restringir (C++ AMP)](../../cpp/restrict-cpp-amp.md).

## <a name="see-also"></a>Vea también

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Sintaxis de la expresión lambda](../../cpp/lambda-expression-syntax.md)<br/>
[Llamada a función](../../cpp/function-call-cpp.md)<br/>
[Objetos de función en la biblioteca estándar de C++](../../standard-library/function-objects-in-the-stl.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)