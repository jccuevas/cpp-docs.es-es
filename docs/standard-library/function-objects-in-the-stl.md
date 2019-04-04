---
title: Objetos de función en la biblioteca estándar de C++
ms.date: 03/15/2019
helpviewer_keywords:
- functors
- C++ Standard Library, functors
- C++ Standard Library, function objects
- function objects
ms.assetid: 85f8a735-2c7b-4f10-9c4d-95c666ec4192
ms.openlocfilehash: 310d846285612ad94ec9d66672fcb996557b07e2
ms.sourcegitcommit: 9e85c2e029d06b4c1c69837437468718b4d54908
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58172964"
---
# <a name="function-objects-in-the-c-standard-library"></a>Objetos de función en la biblioteca estándar de C++

Un *objeto de función*, o *functor*, es cualquier tipo que implementa operator(). Este operador se conoce como el *operador de llamada* o a veces el *operador de la aplicación*. La biblioteca estándar de C++ usa objetos de función principalmente como criterios de ordenación para los contenedores y en algoritmos.

Los objetos de función proporcionan dos ventajas principales en comparación con una llamada de función sencilla. La primera es que un objeto de función puede contener el estado. La segunda es que un objeto de función es un tipo y, por tanto, puede usarse como un parámetro de plantilla.

## <a name="creating-a-function-object"></a>Crear un objeto de función

Para crear un objeto de función, cree un tipo e implemente operator(), por ejemplo:

```cpp
class Functor
{
public:
    int operator()(int a, int b)
    {
        return a < b;
    }
};

int main()
{
    Functor f;
    int a = 5;
    int b = 7;
    int ans = f(a, b);
}
```

La última línea de la función `main` muestra cómo llamar al objeto de función. Esta llamada es similar de una llamada a una función, pero de lo que realmente realiza la llamada operator() del tipo Functor. Esta similitud entre llamar a un objeto de función y una función dio origen al término objeto de función.

## <a name="function-objects-and-containers"></a>Contenedores y objetos de función

La biblioteca estándar de C++ contiene varios objetos de función en el archivo de encabezado [\<functional>](../standard-library/functional.md). Uno de los usos de estos objetos de función es como criterio de ordenación para los contenedores. Por ejemplo, el contenedor `set` se declara de la siguiente manera:

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

El segundo argumento de plantilla es el objeto de función `less`. Este objeto de función devuelve **true** si el primer parámetro es menor que el segundo parámetro. Puesto que algunos contenedores ordenan sus elementos, el contenedor necesita una manera de comparar dos elementos. La comparación se realiza mediante el objeto de función. Puede definir sus propios criterios de clasificación para los contenedores mediante la creación de un objeto de función y especificar en la lista de plantillas para el contenedor.

## <a name="function-objects-and-algorithms"></a>Algoritmos y objetos de función

Otro uso de los objetos de función es en los algoritmos. Por ejemplo, el algoritmo `remove_if` se declara de la siguiente forma:

```cpp
template <class ForwardIterator, class Predicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    Predicate pred);
```

El último argumento `remove_if` es un objeto de función que devuelve un valor booleano (un *predicado*). Si el resultado del objeto de función es **true**, a continuación, se quita el elemento contenedor al que acceden los iteradores `first` y `last`. Puede usar los objetos de función binarios declarados en el encabezado [\<functional>](../standard-library/functional.md) para el argumento `pred` o crear sus propios objetos.

## <a name="see-also"></a>Vea también

[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
