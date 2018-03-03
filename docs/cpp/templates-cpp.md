---
title: Plantillas (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- template_cpp
dev_langs:
- C++
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 935bee8447ad0d49ae965fb92538d2e260ec68ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="templates-c"></a>Plantillas (C++)
Las plantillas son la base de programación genérica en C++. Como un lenguaje fuertemente tipado, C++ requiere que todas las variables que tienen un tipo específico, ya sea explícitamente declarado por el programador o deduce el compilador. Sin embargo, muchos algoritmos y estructuras de datos tenga el mismo aspecto independientemente del tipo que funcionan en. Habilitar plantillas para definir las operaciones de una clase o función y permitir al usuario especificar qué hormigón tipos esas operaciones debe funcionar en.  
  
## <a name="defining-and-using-templates"></a>Definición y uso de plantillas  
 Una plantilla es una construcción que genera un tipo normal o una función en tiempo de compilación en función de los argumentos que el usuario proporciona para los parámetros de plantilla. Por ejemplo, puede definir una plantilla de función similar al siguiente:  
  
```cpp  
template <typename T>  
T minimum(const T& lhs, const T& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 El código anterior describe una plantilla para una función genérica con un parámetro de tipo único `T`, cuyo valor devuelto y llamar a parámetros (lhs y rhs) son todas de este tipo. Puede asignar un parámetro de tipo que como, pero por convención solo mayúsculas se usa normalmente. `T`es un parámetro de plantilla; el `typename` palabra clave indica que este parámetro es un marcador de posición para un tipo. Cuando se llama a la función, el compilador reemplazará todas las instancias de `T` con el argumento de tipo concreto que es especificado por el usuario o deduce el compilador. El proceso en el que el compilador genera una clase o función de una plantilla se conoce como *crear instancias de plantillas*;   `minimum<int>` es una instancia de la plantilla `minimum<T>`.  
  
 En otra parte, un usuario puede declarar una instancia de la plantilla que está especializada para int. Supongamos que get_a() y get_b() son funciones que devuelven un valor int:  
  
```  
int a = get_a();  
int b = get_b();  
int i = minimum<int>(a, b);  
```  
  
 Sin embargo, dado que se trata de una plantilla de función y el compilador pueden deducir el tipo de `T` de los argumentos `a` y `b`, se le puede llamar como una función normal:  
  
```cpp  
int i = minimum(a, b);  
```  
  
 Cuando el compilador encuentra esa última instrucción, se genera una nueva función en que todas las apariciones de *T* en la plantilla se sustituye por `int`:  
  
```  
  
      int minimum(const int& lhs, const int& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 Las reglas de cómo el compilador realiza la deducción de tipos de plantillas de función se basan en las reglas para las funciones normales. Para obtener más información, consulte [sobrecarga resolución de plantilla de llamadas a funciones](../cpp/overload-resolution-of-function-template-calls.md).  
  
## <a id="type_parameters"></a>Parámetros de tipo  
 En el `minimum` plantilla anterior, tenga en cuenta que el parámetro de tipo `T` no está calificado de ninguna manera hasta que se usa en los parámetros de llamada de función, que se agregan las constante y calificadores de referencia.  
  
 No hay ningún límite práctico para el número de parámetros de tipo. Varios parámetros se separan por comas:  
  
```cpp  
template <typename T, typename U, typename V> class Foo{};  
  
```  
  
 La palabra clave `class` es equivalente a `typename` en este contexto. Puede expresar el ejemplo anterior como:  
  
```  
template <class T, class U, class V> class Foo{};   
```  
  
 Puede utilizar el operador de puntos suspensivos (...) para definir una plantilla que toma un número arbitrario de cero o más parámetros de tipo:  
  
```cpp  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
```  
  
 Puede utilizarse cualquier tipo integrado o definido por el usuario como un argumento de tipo. Por ejemplo, puede usar std:: vector en la biblioteca estándar para almacenar valores de tipo int, dobles y cadenas, MyClass, const MyClass *, MyClass &. La restricción principal cuando se utilizan plantillas es que un argumento de tipo debe admitir las operaciones que se aplican a los parámetros de tipo. Por ejemplo, si se llama al método mínima con MyClass como en este ejemplo:  
  
```cpp  
class MyClass  
{  
public:  
    int num;  
    std::wstring description;  
};  
  
int main()  
{      
    MyClass mc1 {1, L"hello"};  
    MyClass mc2 {2, L"goodbye"};  
    auto result = minimum(mc1, mc2); // Error! C2678  
}  
  
```  
  
 Se generará un error del compilador porque MyClass no proporciona una sobrecarga para el < operador.  
  
 No hay ningún requisito inherente a la que los argumentos de tipo para cualquier plantilla determinada todos pertenecen a la misma jerarquía de objetos, aunque se puede definir una plantilla que exige la restricción de este tipo. Puede combinar técnicas orientada a objetos con plantillas; Por ejemplo, puede almacenar un derivado * en un vector\<Base\*>.    Tenga en cuenta que los argumentos deben ser punteros  
  
```  
vector<MyClass*> vec;  
   MyDerived d(3, L"back again", time(0));  
   vec.push_back(&d);  
  
   // or more realistically:  
   vector<shared_ptr<MyClass>> vec2;  
   vec2.push_back(make_shared<MyDerived>());  
```  
  
 Los requisitos básicos que imponen vector y otros contenedores de la biblioteca estándar en los elementos de `T` es que `T` ser copia asignable y puede crear la copia.  
  
## <a name="non-type-parameters"></a>Parámetros sin tipo  
 A diferencia de los tipos genéricos en otros lenguajes como C# y Java, plantillas de C++ admiten parámetros sin tipo, que también se denominan parámetros de valor. Por ejemplo, puede proporcionar un valor entero constante para especificar la longitud de una matriz, al igual que con este ejemplo, es similar a la clase std:: Array en la biblioteca estándar:  
  
```  
template<typename T, size_t L>  
class MyArray  
{  
    T arr[L];  
public:  
    MyArray() { ... }  
};  
  
```  
  
 Tenga en cuenta la sintaxis de la declaración de plantilla. El valor size_t se pasa como un argumento de plantilla en tiempo de compilación y debe ser constante o una expresión de constexpr. Se usa como el siguiente:  
  
```cpp  
MyArray<MyClass*, 10> arr;  
```  
  
 Otros tipos de valores, incluidos los punteros y referencias se pueden pasar como parámetros sin tipo. Por ejemplo, puede pasar un puntero a una función o un objeto de función a personalizar alguna operación en el código de plantilla.  
  
## <a id="template_parameters"></a>Plantillas como parámetros de plantilla  
 Una plantilla puede ser un parámetro de plantilla. En este ejemplo, MyClass2 tiene dos parámetros de plantilla: un parámetro typename `T` y un parámetro de plantilla `Arr`:  
  
```cpp  
template<typename T, template<typename U, int I> class Arr>  
class MyClass2  
{  
    T t; //OK  
    Arr<T, 10> a;  
    U u; //Error. U not in scope  
};  
```  
  
 Dado que el `Arr` propio parámetro no tiene ningún cuerpo, sus nombres de parámetro no es necesario. De hecho, es un error para hacer referencia a `Arr`del nombre de tipo o clase nombres de parámetro desde dentro del cuerpo de `MyClass2`. Por esta razón, `Arr`de nombres de parámetro de tipo se pueden omitir, como se muestra en este ejemplo:  
  
```cpp  
template<typename T, template<typename, int> class Arr>  
class MyClass2  
{  
    T t; //OK  
    Arr<T, 10> a;  
};  
```  
  
## <a name="default-template-arguments"></a>Argumentos de plantilla predeterminados  
 Plantillas de clase y función pueden tener argumentos predeterminados. Cuando una plantilla tiene un argumento predeterminado que puede dejar sin especificar cuando se usa. Por ejemplo, la plantilla de std:: vector tiene un argumento predeterminado para el asignador:  
  
```cpp  
template <class T, class Allocator = allocator<T>> class vector;  
```  
  
 En la mayoría de los casos la clase de std:: Allocator predeterminada es aceptable, por lo que usar un vector similar al siguiente:  
  
```cpp  
vector<int> myInts;  
```  
  
 Pero si es necesario puede especificar un asignador personalizado similar a éste:  
  
```cpp  
vector<int, MyAllocator> ints;  
```  
  
 Para varios argumentos de plantilla, todos los argumentos después del primer argumento predeterminado deben tener argumentos predeterminados.  
  
 Cuando se usa una plantilla de cuyos parámetros son todos de forma predeterminadas, utilice corchetes angulares vacíos:  
  
```cpp  
template<typename A = int, typename B = double>  
class Bar  
{  
    //...  
};  
...  
int main()  
{  
    Bar<> bar; // use all default type arguments  
}  
  
```  
  
## <a name="template-specialization"></a>Especialización de plantilla  
 En algunos casos, no es posible o conveniente para una plantilla definir exactamente el mismo código para cualquier tipo. Por ejemplo, podría desea definir una ruta de acceso de código se ejecuta sólo si el argumento de tipo es un puntero o un std:: wstring o un tipo derivado de una clase base concreta.  En tales casos puede definir un *especialización* de la plantilla para ese tipo. Cuando un usuario crea una instancia de la plantilla con ese tipo, el compilador usa la especialización para generar la clase y, para todos los demás tipos, el compilador elige la plantilla más general. Las especializaciones de en el que están especializados todos los parámetros son *completar especializaciones*. Si solo algunos de los parámetros están especializados, se llama una *especialización parcial*.  
  
```cpp  
template <typename K, typename V>  
class MyMap{/*...*/};  
  
// partial specialization for string keys  
template<typename V>  
class MyMap<string, V> {/*...*/};  
...  
MyMap<int, MyClass> classes; // uses original template  
MyMap<string, MyClass> classes2; // uses the partial specialization  
  
```  
  
 Una plantilla puede tener cualquier número de especializaciones siempre que cada parámetro de tipo especializado que sea único.   Plantillas de clase solo se pueden especializar parcialmente. Todas las especializaciones completa y parciales de una plantilla deben declararse en el mismo espacio de nombres como la plantilla original.  
  
 Para obtener más información, consulte [especialización de plantilla](../cpp/template-specialization-cpp.md).