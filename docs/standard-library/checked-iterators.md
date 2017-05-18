---
title: Iteradores comprobados | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _SECURE_SCL_THROWS
dev_langs:
- C++
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
- iterators, checked
- checked iterators
ms.assetid: cfc87df8-e3d9-403b-ab78-e9483247d940
caps.latest.revision: 30
author: corob-msft
ms.author: corob
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 72fae545c992eb8b9bcaf7145702b7f92a7307d1
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="checked-iterators"></a>Checked Iterators
Los iteradores comprobados garantizan que los límites del contenedor no se han sobrescrito. Los iteradores comprobados se aplican a las compilaciones de depuración y de lanzamiento. Para obtener más información sobre cómo usar iteradores de depuración cuando se compila en modo depuración, vea [Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md).  
  
## <a name="remarks"></a>Comentarios  
Para obtener información sobre cómo deshabilitar las advertencias generadas por iteradores comprobados, vea [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).  
  
Puede usar la macro de preprocesador [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md) para habilitar o deshabilitar la característica de iteradores comprobados. Si `_ITERATOR_DEBUG_LEVEL` se define como 1 o 2, el uso no seguro de iteradores produce un error en tiempo de ejecución y el programa finaliza. Si se define como 0, se deshabilitan los iteradores comprobados. De manera predeterminada, el valor de `_ITERATOR_DEBUG_LEVEL` es 0 para las versiones de lanzamiento y 2 para las versiones de depuración.  
  
> [!IMPORTANT]
> La documentación y el código fuente antiguos pueden hacer referencia a la macro [_SECURE_SCL](../standard-library/secure-scl.md). Use `_ITERATOR_DEBUG_LEVEL` para controlar `_SECURE_SCL`. Para obtener más información, vea [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).  
  
Cuando `_ITERATOR_DEBUG_LEVEL` se define como 1 o 2, se realizan estas comprobaciones de iteradores:  
  
-   Se comprueban todos los iteradores estándar (por ejemplo, [vector::iterator](../standard-library/vector-class.md#iterator)).  
  
-   Si un iterador de salida es un iterador comprobado, las llamadas a funciones de la biblioteca estándar como [std::copy](../standard-library/algorithm-functions.md#copy) obtienen un comportamiento comprobado.  
  
-   Si un iterador de salida es un iterador no comprobado, las llamadas a funciones de la biblioteca estándar producirán advertencias del compilador.  
  
-   Las siguientes funciones producen un error en tiempo de ejecución si hay algún acceso que sobrepase los límites del contenedor:  
  
|||||  
|-|-|-|-|  
|[basic_string::operator\[\]](../standard-library/basic-string-class.md#op_at)|[bitset::operator\[\]](../standard-library/bitset-class.md#op_at)|[back](../standard-library/deque-class.md#back)|[front](../standard-library/deque-class.md#front)|  
|[deque::operator\[\]](../standard-library/deque-class.md#op_at)|[back](../standard-library/list-class.md#back)|[front](../standard-library/list-class.md#front)|[back](../standard-library/queue-class.md#back)|  
|[front](../standard-library/queue-class.md#front)|[vector::operator\[\]](../standard-library/vector-class.md#op_at)|[back](../standard-library/vector-class.md#back)|[front](../standard-library/vector-class.md#front)|  
  
Cuando `_ITERATOR_DEBUG_LEVEL` se define como 0:  
  
-   Todos los iteradores estándar están sin comprobar. Los iteradores pueden moverse más allá de los límites del contenedor, lo que da lugar a un comportamiento no definido.  
  
-   Si un iterador de salida es un iterador comprobado, las llamadas a funciones de la biblioteca estándar como `std::copy` obtienen un comportamiento comprobado.  
  
-   Si un iterador de salida es un iterador no comprobado, las llamadas a funciones de la biblioteca estándar obtienen un comportamiento no comprobado.  
  
Un iterador comprobado hace referencia a un iterador que llama a `invalid_parameter_handler` si intenta sobrepasar los límites del contenedor. Para obtener más información sobre `invalid_parameter_handler`, vea [Validación de parámetros](../c-runtime-library/parameter-validation.md).  
  
Los adaptadores de iterador que admiten iteradores comprobados son [checked_array_iterator (clase)](../standard-library/checked-array-iterator-class.md) y [unchecked_array_iterator (clase)](../standard-library/unchecked-array-iterator-class.md).  
  
## <a name="example"></a>Ejemplo  
  
Al compilar con `_ITERATOR_DEBUG_LEVEL` establecido en 1 o 2, se producirá un error en tiempo de ejecución si intenta acceder a un elemento que está fuera de los límites del contenedor mediante el operador de indexación de algunas clases.  
  
```cpp  
// checked_iterators_1.cpp  
// cl.exe /Zi /MDd /EHsc /W4  
  
#define _ITERATOR_DEBUG_LEVEL 1  
  
#include <vector>  
#include <iostream>  
  
using namespace std;  
  
int main()  
{  
   vector<int> v;  
   v.push_back(67);  
  
   int i = v[0];  
   cout << i << endl;  
  
   i = v[1]; //triggers invalid parameter handler  
}  
```  
  
Este programa imprimirá "67" y después mostrará un cuadro de diálogo de error de aserción con información adicional sobre el error.  
  
## <a name="example"></a>Ejemplo  
  
De igual forma, al compilar con `_ITERATOR_DEBUG_LEVEL` establecido en 1 o 2, se producirá un error en tiempo de ejecución si intenta tener acceso a un elemento usando `front` o `back` en clases de contenedor cuando el contenedor está vacío.  
  
```cpp  
// checked_iterators_2.cpp  
// cl.exe /Zi /MDd /EHsc /W4  
#define _ITERATOR_DEBUG_LEVEL 1  
  
#include <vector>  
#include <iostream>  
  
using namespace std;  
  
int main()  
{  
   vector<int> v;  
  
   int& i = v.front(); // triggers invalid parameter handler  
}  
```  
  
Este programa muestra un cuadro de diálogo de error de aserción con información adicional sobre el error.  
  
## <a name="example"></a>Ejemplo  
  
En el código siguiente se muestran distintos escenarios de casos de uso de un iterador con comentarios sobre cada uno. De manera predeterminada, `_ITERATOR_DEBUG_LEVEL` se establece en 2 en compilaciones de depuración y en 0 en compilaciones comerciales.  
  
```cpp  
// checked_iterators_3.cpp  
// cl.exe /MTd /EHsc /W4  
  
#include <algorithm>  
#include <array>  
#include <iostream>  
#include <iterator>  
#include <numeric>  
#include <string>  
#include <vector>  
  
using namespace std;  
  
template <typename C> 
void print(const string& s, const C& c)  
{  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    vector<int> v(16);  
    iota(v.begin(), v.end(), 0);  
    print("v: ", v);  
  
    // OK: vector::iterator is checked in debug mode  
    // (i.e. an overrun causes a debug assertion)  
    vector<int> v2(16);  
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });  
    print("v2: ", v2);  
  
    // OK: back_insert_iterator is marked as checked in debug mode  
    // (i.e. an overrun is impossible)  
    vector<int> v3;  
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });  
    print("v3: ", v3);  
  
    // OK: array::iterator is checked in debug mode  
    // (i.e. an overrun causes a debug assertion)  
    array<int, 16> a4;  
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });  
    print("a4: ", a4);  
  
    // OK: Raw arrays are checked in debug mode  
    // (an overrun causes a debug assertion)  
    // NOTE: This applies only when raw arrays are given to C++ Standard Library algorithms!  
    int a5[16];  
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });  
    print("a5: ", a5);  
  
    // WARNING C4996: Pointers cannot be checked in debug mode  
    // (an overrun causes undefined behavior)  
    int a6[16];  
    int * p6 = a6;  
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });  
    print("a6: ", a6);  
  
    // OK: stdext::checked_array_iterator is checked in debug mode  
    // (an overrun causes a debug assertion)  
    int a7[16];  
    int * p7 = a7;  
    transform(v.begin(), v.end(), stdext::make_checked_array_iterator(p7, 16), [](int n) { return n * 7; });  
    print("a7: ", a7);  
  
    // WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode  
    // (it performs no checking, so an overrun causes undefined behavior)  
    int a8[16];  
    int * p8 = a8;  
    transform(v.begin(), v.end(), stdext::make_unchecked_array_iterator(p8), [](int n) { return n * 8; });  
    print("a8: ", a8);  
}  
  
```  
  
Al compilar este código con `cl.exe /EHsc /W4 /MTd checked_iterators_3.cpp`, el compilador emite una advertencia, pero se compila sin errores en un archivo ejecutable:  
  
```Output  
algorithm(1026) : warning C4996: 'std::_Transform1': Function call with parameters 
that may be unsafe - this call relies on the caller to check that the passed values 
are correct. To disable this warning, use -D_SCL_SECURE_NO_WARNINGS. See documentation 
on how to use Visual C++ 'Checked Iterators'  
```  
  
Cuando se ejecuta en la línea de comandos, el ejecutable genera este resultado:  
  
```Output  
v: 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15  
v2: 0 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30  
v3: 0 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45  
a4: 0 4 8 12 16 20 24 28 32 36 40 44 48 52 56 60  
a5: 0 5 10 15 20 25 30 35 40 45 50 55 60 65 70 75  
a6: 0 6 12 18 24 30 36 42 48 54 60 66 72 78 84 90  
a7: 0 7 14 21 28 35 42 49 56 63 70 77 84 91 98 105  
a8: 0 8 16 24 32 40 48 56 64 72 80 88 96 104 112 120  
```  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre la biblioteca estándar de C++](../standard-library/cpp-standard-library-overview.md)   
 [Compatibilidad de los iteradores de depuración](../standard-library/debug-iterator-support.md)


