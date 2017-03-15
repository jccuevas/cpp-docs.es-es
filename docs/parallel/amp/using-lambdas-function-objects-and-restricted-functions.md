---
title: "Usar expresiones lambda, objetos de funci&#243;n y funciones restringidas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 25346cc9-869d-4ada-aad3-e2228cad3d6c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Usar expresiones lambda, objetos de funci&#243;n y funciones restringidas
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El código AMP de C\+\+ que se desea ejecutar en el acelerador se especifica como un argumento en una llamada al método [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md).  Puede proporcionar o bien una expresión lambda o un objeto de función \(functor\) como argumento.  Además, la expresión lambda o el objeto de función pueden llamar a una función restringida por C\+\+ AMP.  Este tema utiliza un algoritmo de suma de vectores para demostrar las expresiones lambda, los objetos de función y las funciones restringidas.  El siguiente ejemplo muestra el algoritmo sin código AMP de C\+\+.  Se crean dos vectores unidimensionales de igual longitud.  Los elementos enteros correspondientes se agregan y se almacenan en un tercera vector unidimensional.  No se utiliza C\+\+ AMP.  
  
```cpp  
  
void CpuMethod() {  
  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5];  
  
    for (int idx = 0; idx < 5; idx++)  
    {  
        sumCPP[idx] = aCPP[idx] + bCPP[idx];  
    }  
  
    for (int idx = 0; idx < 5; idx++)  
    {  
        std::cout << sumCPP[idx] << "\n";  
    }  
}  
  
```  
  
## Expresión lambda  
 Emplear una expresión lambda es la manera más directa de utilizar C\+\+ AMP para reescribir el código.  
  
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
        }  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
 La expresión lambda debe incluir un parámetro de indexación y debe incluir `restrict(amp)`.  En el ejemplo, el objeto [array\_view](../../parallel/amp/reference/array-view-class.md) `sum` tiene un rango de 1.  Por tanto, el parámetro de la expresión lambda es un objeto [índice](../../parallel/amp/reference/index-class.md) que tiene rango 1.  En tiempo de ejecución, la expresión lambda se ejecuta una vez por cada elemento en el objeto [array\_view](../../parallel/amp/reference/array-view-class.md).  Para obtener más información, vea [Sintaxis de las expresiones lambda](../../cpp/lambda-expression-syntax.md).  
  
## Function \(Objeto\)  
 Puede factorizar el código del acelerador en un objeto de función.  
  
```cpp  
  
class AdditionFunctionObject  
{  
public:  
    AdditionFunctionObject(const array_view<int, 1>& a,  
        const array_view<int, 1>& b,  
        const array_view<int, 1>& sum  
    )  
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
        AdditionFunctionObject(a, b, sum)  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
 El objeto función debe incluir un constructor y también una sobrecarga del operador de llamada a función.  El operador de llamada a la función debe incluir un parámetro de indexación.  Una instancia del objeto función se pasa como segundo argumento al método [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md).  En este ejemplo, se pasan tres objetos [array\_view](../../parallel/amp/reference/array-view-class.md) al constructor del objeto de función.  El objeto [array\_view](../../parallel/amp/reference/array-view-class.md) `sum` tiene un rango de 1.  Por lo tanto, el parámetro del operador de llamada a función es un objeto [índice](../../parallel/amp/reference/index-class.md) que tiene rango 1.  En tiempo de ejecución, la función se ejecuta una vez por cada elemento en el objeto [array\_view](../../parallel/amp/reference/array-view-class.md).  Para obtener más información, vea [Llamada de función](../../cpp/function-call-cpp.md) y [Objetos de función en STL](../../standard-library/function-objects-in-the-stl.md).  
  
## Función restringida del Amp de C\+\+  
 Puede factorizar el código del acelerador mediante la creación de una función restringida y llamarlo a partir de una expresión lambda o un objeto de función.  El siguiente código de ejemplo muestra cómo llamar a una función restringida desde una expresión lambda.  
  
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
        }  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
 La función restringida debe incluir `restrict(amp)` y ajustarse a las restricciones que se describen en [restrict \(C\+\+ AMP\)](../../cpp/restrict-cpp-amp.md).  
  
## Vea también  
 [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Sintaxis de las expresiones lambda](../../cpp/lambda-expression-syntax.md)   
 [Llamada de función](../../cpp/function-call-cpp.md)   
 [Objetos de función en STL](../../standard-library/function-objects-in-the-stl.md)   
 [restrict \(C\+\+ AMP\)](../../cpp/restrict-cpp-amp.md)