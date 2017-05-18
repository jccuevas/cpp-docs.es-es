---
title: Asignadores | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- allocators
- C++ Standard Library, allocators
ms.assetid: ac95023b-9e7d-49f5-861a-bf7a9a340746
caps.latest.revision: 8
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
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 74e453298857b94c2c4eb62c5387d4e727f7bb7c
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="allocators"></a>Asignadores
La biblioteca estándar de C++ usa los asignadores para controlar la asignación y desasignación de elementos almacenados en contenedores. Todos los contenedores de la biblioteca estándar de C++ excepto std::array tienen un parámetro de plantilla de tipo `allocator<Type>`, donde `Type` representa el tipo del elemento contenedor. Por ejemplo, la clase vector se declara como sigue:  
  
```  
template <  
    class Type,  
    class Allocator = allocator<Type>  
>  
class vector  
```  
  
 La biblioteca estándar de C++ proporciona una implementación predeterminada para un asignador. En C++11 y versiones posteriores, el asignador predeterminado se actualiza para exponer una interfaz más pequeña. El nuevo asignador se denomina *asignador mínimo*. En particular, el miembro del asignador mínimo `construct()` admite la semántica de movimiento, que puede mejorar considerablemente el rendimiento. En la mayoría de los casos, este asignador predeterminado debería ser suficiente. En C++11 todos los tipos y las funciones de la biblioteca estándar con un parámetro de tipo de asignador admiten la interfaz del asignador mínimo, incluyendo `std::function`, `shared_ptr, allocate_shared()` y `basic_string`.  Para más información sobre el asignador predeterminado, vea [allocator (Clase)](../standard-library/allocator-class.md).  
  
## <a name="writing-your-own-allocator-c11"></a>Escribir su propio asignador (C++11)  
 El asignador predeterminado usa `new` y `delete` para asignar y desasignar memoria. Si quiere emplear otro método de asignación de memoria, como el uso de memoria compartida, debe crear su propio asignador. Si quiere usar C++11 y tiene que escribir un asignador personalizado nuevo, haga que sea un asignador mínimo si es posible. Si ya ha implementado un asignador de estilo antiguo, considere la posibilidad de modificarlo para que sea un *asignador mínimo* y aprovechar la mayor eficacia del método `construct()` que se proporcionará automáticamente.  
  
 Un asignador mínimo requiere mucha menos repetición y le permite centrarse en las funciones miembro `allocate` y `deallocate`, que hacen todo el trabajo. Al crear un asignador mínimo, implemente solo los miembros que se muestran en el ejemplo siguiente:  
  
1.  un constructor de copias de conversión (vea el ejemplo)  
  
2.  operator==  
  
3.  operator!=  
  
4.  allocate  
  
5.  deallocate  
  
 El miembro `construct()` predeterminado de C++11 que se proporcionará reenvía directamente y habilita la semántica de transferencia; es mucho más eficaz en muchos casos que la versión anterior.  
  
> [!WARNING]
>  En tiempo de compilación, la biblioteca estándar de C++ usa la clase allocator_traits para detectar los miembros que se hayan proporcionado explícitamente y proporciona una implementación predeterminada para todos los miembros que no están presentes. No interfiera en este mecanismo proporcionando una especialización de allocator_traits para su asignador.  
  
 En el ejemplo siguiente se muestra una implementación mínima de un asignador que usa `malloc` y `free`. Tenga en cuenta el uso del nuevo tipo de excepción `std::bad_array_new_length` que se produce si el tamaño de la matriz es menor que cero o mayor que el tamaño máximo permitido.  
  
```  
#pragma once  
#include <stdlib.h> //size_t, malloc, free  
#include <new> // bad_alloc, bad_array_new_length  
#include <memory>  
template <class T>  
struct Mallocator  
{  
    typedef T value_type;  
    Mallocator() noexcept {} //default ctor not required by C++ Standard Library  
  
    // A converting copy constructor:  
    template<class U> Mallocator(const Mallocator<U>&) noexcept {}  
    template<class U> bool operator==(const Mallocator<U>&) const noexcept  
    {  
        return true;  
    }  
    template<class U> bool operator!=(const Mallocator<U>&) const noexcept  
    {  
        return false;  
    }  
    T* allocate(const size_t n) const;  
    void deallocate(T* const p, size_t) const noexcept;  
};  
  
template <class T>  
T* Mallocator<T>::allocate(const size_t n) const  
{  
    if (n == 0)  
    {  
        return nullptr;  
    }  
    if (n > static_cast<size_t>(-1) / sizeof(T))  
    {  
        throw std::bad_array_new_length();  
    }  
    void* const pv = malloc(n * sizeof(T));  
    if (!pv) { throw std::bad_alloc(); }  
    return static_cast<T*>(pv);  
}  
  
template<class T>  
void Mallocator<T>::deallocate(T * const p, size_t) const noexcept  
{  
    free(p);  
}  
```  
  
## <a name="writing-your-own-allocator-c03"></a>Escribir su propio asignador (C++03)  
 En C ++03, cualquier asignador usado con contenedores de la biblioteca estándar de C++ debe implementar las definiciones de tipo siguientes:  
  
|||  
|-|-|  
|`const_pointer`|`rebind`|  
|`const_reference`|`reference`|  
|`difference_type`|`size_type`|  
|`pointer`|`value_type`|  
  
 Además, cualquier asignador usado con contenedores de la biblioteca estándar de C++ debe implementar los siguientes métodos:  
  
|||  
|-|-|  
|Constructor|`deallocate`|  
|Constructor de copias|`destroy`|  
|Destructor|`max_size`|  
|`address`|`operator==`|  
|`allocate`|`operator!=`|  
|`construct`||  
  
 Para más información sobre estas definiciones de tipos y métodos, vea [allocator (Clase)](../standard-library/allocator-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)





