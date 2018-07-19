---
title: Plantillas (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- template_cpp
dev_langs:
- C++
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 673eadf3651d15f480ee2cff9ef3f7319dee4d84
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944552"
---
# <a name="templates-c"></a>Plantillas (C++)
Las plantillas son la base para la programación genérica en C++. Como un lenguaje fuertemente tipado, C++ requiere que todas las variables que tienen un tipo específico, ya sea explícitamente declarado por el programador o por el compilador puede deducir. Sin embargo, muchos algoritmos y estructuras de datos tengan el mismo aspecto independientemente del tipo están trabajando en. Las plantillas permiten definir las operaciones de una clase o función, y permitir al usuario especificar qué hormigón tipos esas operaciones deben funcionar en.  
  
## <a name="defining-and-using-templates"></a>Definición y uso de plantillas  
 Una plantilla es una construcción que genera un tipo normal o una función en tiempo de compilación en función de los argumentos que el usuario proporciona para los parámetros de plantilla. Por ejemplo, puede definir una plantilla de función como esta:  
  
```cpp  
template <typename T>  
T minimum(const T& lhs, const T& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 El código anterior describe una plantilla para una función con un único parámetro de tipo genérica `T`, cuyo valor devuelto y parámetros (lhs y rhs) de llamada son todas de este tipo. Puede asignar un parámetro de tipo que le guste, pero por convención solo mayúsculas se usa con más frecuencia. `T` es un parámetro de plantilla; el **typename** palabra clave indica que este parámetro es un marcador de posición para un tipo. Cuando se llama a la función, el compilador reemplazará todas las instancias de `T` con el argumento de tipo concreto especificado por el usuario o por el compilador puede deducir. El proceso en el que el compilador genera una clase o función desde una plantilla se conoce como *crear instancias de plantillas*;   `minimum<int>` es una instancia de la plantilla `minimum<T>`.  
  
 En otra parte, un usuario puede declarar una instancia de la plantilla que sirve para int. Supongamos que get_a() y get_b() son funciones que devuelven un valor int:  
  
```cpp 
int a = get_a();  
int b = get_b();  
int i = minimum<int>(a, b);  
```  
  
 Sin embargo, dado que se trata de una plantilla de función y el compilador pueden deducir el tipo de `T` argumentech `a` y `b`, puede llamarlo como una función normal:  
  
```cpp  
int i = minimum(a, b);  
```  
  
 Cuando el compilador encuentra la última instrucción, se genera una nueva función en que todas las apariciones de *T* en la plantilla se sustituye por **int**:  
  
```cpp 
  
      int minimum(const int& lhs, const int& rhs)  
{  
    return lhs < rhs ? lhs : rhs;  
}  
```  
  
 Las reglas de cómo el compilador realiza la deducción de tipos en las plantillas de función se basan en las reglas para las funciones normales. Para obtener más información, consulte [sobrecargar la resolución de función de plantilla llama a](../cpp/overload-resolution-of-function-template-calls.md).  
  
## <a id="type_parameters"></a> Parámetros de tipo  
 En el `minimum` plantilla anterior, tenga en cuenta que el parámetro de tipo `T` no está calificado de ninguna manera hasta que se usa en los parámetros de llamada de función, donde se agregan los const y calificadores de referencia.  
  
 No hay ningún límite práctico para el número de parámetros de tipo. Separe varios parámetros con comas:  
  
```cpp  
template <typename T, typename U, typename V> class Foo{};  
  
```  
  
 La palabra clave **clase** es equivalente a **typename** en este contexto. Puede expresar en el ejemplo anterior, como:  
  
```cpp 
template <class T, class U, class V> class Foo{};   
```  
  
 Puede utilizar el operador de puntos suspensivos (...) para definir una plantilla que toma un número arbitrario de cero o más parámetros de tipo:  
  
```cpp  
template<typename... Arguments> class vtclass;  
  
vtclass< > vtinstance1;  
vtclass<int> vtinstance2;  
vtclass<float, bool> vtinstance3;  
```  
  
 Cualquier tipo integrado o definido por el usuario puede utilizarse como un argumento de tipo. Por ejemplo, puede usar std:: vector en la biblioteca estándar para almacenar enteros, dobles y cadenas, MyClass, MyClass const *, MyClass &. La principal restricción al utilizar plantillas es que un argumento de tipo debe admitir las operaciones que se aplican a los parámetros de tipo. Por ejemplo, si se llama a mínimos mediante MyClass como en este ejemplo:  
  
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
  
 No hay ningún requisito inherente que los argumentos de tipo para cualquier plantilla determinada todas pertenecen a la misma jerarquía de objetos, aunque puede definir una plantilla que se aplica esta restricción. Puede combinar técnicas orientadas a objetos con plantillas; Por ejemplo, puede almacenar un derivado * en un vector\<Base\*>.    Tenga en cuenta que los argumentos deben ser punteros  
  
```cpp 
vector<MyClass*> vec;  
   MyDerived d(3, L"back again", time(0));  
   vec.push_back(&d);  
  
   // or more realistically:  
   vector<shared_ptr<MyClass>> vec2;  
   vec2.push_back(make_shared<MyDerived>());  
```  
  
 Los requisitos básicos que vector y otros contenedores de la biblioteca estándar se imponen en elementos de `T` es que `T` ser copia asignable y construir de la copia.  
  
## <a name="non-type-parameters"></a>Parámetros sin tipo  
 A diferencia de los tipos genéricos en otros lenguajes como C# y Java, las plantillas de C++ admiten parámetros sin tipo, que también se denominan parámetros de valor. Por ejemplo, puede proporcionar un valor entero constante para especificar la longitud de una matriz, al igual que con este ejemplo, es similar a la clase std:: Array en la biblioteca estándar:  
  
```cpp 
template<typename T, size_t L>  
class MyArray  
{  
    T arr[L];  
public:  
    MyArray() { ... }  
};  
  
```  
  
 Tenga en cuenta la sintaxis en la declaración de plantilla. El valor de size_t se pasa como un argumento de plantilla en tiempo de compilación y debe ser constante o una expresión constexpr. Se usa como esta:  
  
```cpp  
MyArray<MyClass*, 10> arr;  
```  
  
 Otros tipos de valores, incluidos los punteros y referencias pueden pasarse como parámetros sin tipo. Por ejemplo, puede pasar un puntero a una función o un objeto de función para personalizar alguna operación dentro del código de plantilla.  
  
## <a id="template_parameters"></a> Plantillas como parámetros de plantilla  
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
  
 Dado que el `Arr` propio parámetro no tiene ningún cuerpo, sus nombres de parámetro no son necesarios. De hecho, es un error para hacer referencia a `Arr`del nombre de tipo o clase los nombres de parámetro desde dentro del cuerpo de `MyClass2`. Por este motivo, `Arr`de se pueden omitir los nombres de parámetro de tipo, como se muestra en este ejemplo:  
  
```cpp  
template<typename T, template<typename, int> class Arr>  
class MyClass2  
{  
    T t; //OK  
    Arr<T, 10> a;  
};  
```  
  
## <a name="default-template-arguments"></a>Argumentos de plantilla predeterminados  
 Las plantillas de clase y función pueden tener argumentos predeterminados. Cuando una plantilla tiene un argumento predeterminado que puede dejar sin especificar cuando se usa. Por ejemplo, la plantilla de std:: vector tiene un argumento predeterminado para el asignador:  
  
```cpp  
template <class T, class Allocator = allocator<T>> class vector;  
```  
  
 En la mayoría de los casos, la clase std:: Allocator predeterminada es aceptable, por lo que usar un vector similar al siguiente:  
  
```cpp  
vector<int> myInts;  
```  
  
 Pero si es necesario puede especificar un asignador personalizado así:  
  
```cpp  
vector<int, MyAllocator> ints;  
```  
  
 Para varios argumentos de plantilla, todos los argumentos después del primer argumento predeterminado deben tener argumentos predeterminados.  
  
 Cuando se usa una plantilla cuyos parámetros son todos de forma predeterminadas, utilice corchetes angulares vacíos:  
  
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
 En algunos casos, no es posible o conveniente para una plantilla definir exactamente el mismo código para cualquier tipo. Por ejemplo, es posible que desea definir una ruta de acceso del código que se ejecutará solo si el argumento de tipo es un puntero o un std:: wstring o un tipo derivado de una clase base concreta.  En tales casos puede definir un *especialización* de la plantilla para ese tipo. Cuando un usuario crea una instancia de la plantilla con ese tipo, el compilador usa la especialización para generar la clase, y para todos los demás tipos, el compilador elige la plantilla más general. Especializaciones en el que están especializados en todos los parámetros son *completar especializaciones*. Si solo algunos de los parámetros están especializadas, se llama a un *especialización parcial*.  
  
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
  
 Una plantilla puede tener cualquier número de especializaciones siempre que sea único cada parámetro de tipo especializado.   Solo las plantillas de clase se pueden especializar parcialmente. Todas las especializaciones parciales y completadas de una plantilla se deben declarar en el mismo espacio de nombres como la plantilla original.  
  
 Para obtener más información, consulte [especialización de plantilla](../cpp/template-specialization-cpp.md).