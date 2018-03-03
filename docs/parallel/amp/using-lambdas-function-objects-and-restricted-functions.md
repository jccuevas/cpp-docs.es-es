---
title: "Usar expresiones lambda, objetos de función y funciones restringidas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 25346cc9-869d-4ada-aad3-e2228cad3d6c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afec84ba6e3c007e576c37b4a7afc71fe62691ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-lambdas-function-objects-and-restricted-functions"></a>Usar expresiones lambda, objetos de función y funciones restringidas
El código de C++ AMP que se va a ejecutar en el Acelerador se especifica como un argumento en una llamada a la [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) método. Puede proporcionar una expresión lambda o un objeto de función (functor) como argumento. Además, el objeto de función o expresión lambda puede llamar a una función de C++ AMP restringido. En este tema se utiliza un algoritmo de suma de matriz para mostrar las expresiones lambda, objetos de función y funciones restringidas. En el ejemplo siguiente se muestra el algoritmo sin código de C++ AMP. Se crean dos matrices unidimensionales 1 de la misma longitud. Los elementos correspondientes de entero se agregan y se almacenan en una tercera matriz dimensional 1. No se utiliza C++ AMP.  
  
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
 Usar una expresión lambda es la forma más directa de usar C++ AMP para volver a escribir el código.  
  
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
  
 La expresión lambda debe incluir un parámetro de indización y debe incluir `restrict(amp)`. En el ejemplo, el [array_view](../../parallel/amp/reference/array-view-class.md) `sum` objeto tiene un rango de 1. Por lo tanto, el parámetro a la instrucción de expresión lambda es una [índice](../../parallel/amp/reference/index-class.md) objeto que tiene el rango 1. En tiempo de ejecución, la expresión lambda se ejecuta una vez para cada elemento de la [array_view](../../parallel/amp/reference/array-view-class.md) objeto. Para obtener más información, consulte [sintaxis de expresiones Lambda](../../cpp/lambda-expression-syntax.md).  
  
## <a name="function-object"></a>Function (Objeto)  
 El código de acelerador se pueden incluir en un objeto de función.  
  
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

 El objeto de función debe incluir un constructor y debe incluir una sobrecarga del operador de llamada de función. El operador de llamada de función debe incluir un parámetro de indización. Una instancia del objeto de función se pasa como segundo argumento de la [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) método. En este ejemplo, tres [array_view](../../parallel/amp/reference/array-view-class.md) objetos se pasan al constructor de objeto de función. El [array_view](../../parallel/amp/reference/array-view-class.md) objeto `sum` tiene un rango de 1. Por lo tanto, el parámetro del operador de llamada de función es un [índice](../../parallel/amp/reference/index-class.md) objeto que tiene el rango 1. En tiempo de ejecución, la función se ejecuta una vez para cada elemento de la [array_view](../../parallel/amp/reference/array-view-class.md) objeto. Para obtener más información, consulte [llamadas a función](../../cpp/function-call-cpp.md) y [objetos de función en la biblioteca estándar de C++](../../standard-library/function-objects-in-the-stl.md).  
  
## <a name="c-amp-restricted-function"></a>Función de C++ AMP restringido  
 Puede incluir el código de aceleración mediante la creación de una función restringida y llamarlo desde una expresión lambda o un objeto de función. En el ejemplo de código siguiente se muestra cómo llamar a una función restringida de una expresión lambda.  
  
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
  
 Debe incluir la función restringida `restrict(amp)` y cumplir las restricciones que se describen en [restringir (C++ AMP)](../../cpp/restrict-cpp-amp.md).  
  
## <a name="see-also"></a>Vea también  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Sintaxis de expresiones lambda](../../cpp/lambda-expression-syntax.md)   
 [Llamada de función](../../cpp/function-call-cpp.md)   
 [Objetos de función en la biblioteca estándar de C++](../../standard-library/function-objects-in-the-stl.md)   
 [restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

