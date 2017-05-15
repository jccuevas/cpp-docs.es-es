---
title: weak_ptr (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- weak_ptr
- memory/std::weak_ptr
- memory/std::weak_ptr::element_type
- memory/std::weak_ptr::expired
- memory/std::weak_ptr::lock
- memory/std::weak_ptr::owner_before
- memory/std::weak_ptr::reset
- memory/std::weak_ptr::swap
- memory/std::weak_ptr::use_count
- memory/std::weak_ptr::operator=
- memory/std::weak_ptr::element_type
- memory/std::weak_ptr::expired
- memory/std::weak_ptr::lock
- memory/std::weak_ptr::owner_before
- memory/std::weak_ptr::reset
- memory/std::weak_ptr::swap
- memory/std::weak_ptr::use_count
dev_langs:
- C++
helpviewer_keywords:
- weak_ptr class
ms.assetid: 2db4afb2-c7be-46fc-9c20-34ec2f8cc7c2
caps.latest.revision: 22
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
ms.openlocfilehash: f7e4ff26f4d98dc677483f8526c17474aecc81dc
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="weakptr-class"></a>weak_ptr (Clase)
Contiene un puntero débilmente vinculado.  
  
## <a name="syntax"></a>Sintaxis  
```    
template<class _Ty>
   class weak_ptr {  
public:  
   typedef Ty element_type;  
   weak_ptr();
   weak_ptr(const weak_ptr&);
   template <class Other>  
      weak_ptr(const weak_ptr<Other>&);
   template <class Other>  
      weak_ptr(const shared_ptr<Other>&);
   weak_ptr& operator=(const weak_ptr&);
   template <class Other>  
      weak_ptr& operator=(const weak_ptr<Other>&);
   template <class Other>  
      weak_ptr& operator=(shared_ptr<Other>&);
   void swap(weak_ptr&);
   void reset();
   long use_count() const;
   bool expired() const;
   shared_ptr<Ty> lock() const;
   };  
```    
#### <a name="parameters"></a>Parámetros  
 `Ty`  
 Tipo controlado por el puntero débil.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla describe un objeto que apunta a un recurso administrado por uno o varios objetos [shared_ptr (Clase)](../standard-library/shared-ptr-class.md). Los objetos `weak_ptr` que apuntan a un recurso no afectan al recuento de referencias del recurso. Por lo tanto, cuando se destruye el último objeto `shared_ptr` que administra dicho recurso, este se libera, aunque haya objetos `weak_ptr` apuntando a él. Esto es esencial para evitar ciclos en estructuras de datos.  
  
 Un objeto `weak_ptr` apunta a un recurso si se construyó a partir de un objeto `shared_ptr` que posee ese recurso, si se construyó a partir de un objeto `weak_ptr` que apunta a ese recurso o si se le asignó ese recurso con [operator=](#op_eq). Un objeto `weak_ptr` no proporciona acceso directo al recurso al que apunta. El código que debe usar el recurso lo hace a través de un objeto `shared_ptr` que posee ese recurso, creado mediante una llamada a la función miembro [lock](#lock). Un objeto `weak_ptr` expira cuando se libera el recurso al que apunta porque todos los objetos `shared_ptr` que poseen el recurso se han destruido. Llamar a `lock` en un objeto `weak_ptr` que ha expirado crea un objeto shared_ptr vacío.  
  
 Un objeto weak_ptr vacío no apunta a ningún recurso y no tiene ningún bloque de control. Su función miembro `lock` devuelve un objeto shared_ptr vacío.  
  
 Un ciclo se produce cuando dos o más recursos controlados por objetos `shared_ptr` contienen objetos `shared_ptr` que se hacen referencia mutuamente. Por ejemplo, una lista vinculada circular con tres elementos tiene un nodo principal `N0`; ese nodo contiene un objeto `shared_ptr` que posee el siguiente nodo, `N1`; ese nodo contiene un objeto `shared_ptr` que posee el siguiente nodo, `N2`; ese nodo, a su vez, contiene un objeto `shared_ptr` que posee el nodo principal, `N0`, que cierra el ciclo. En esta situación, ninguno de los recuentos de referencia será cero en ningún momento y no se liberarán los nodos del ciclo. Para eliminar el ciclo, el último nodo `N2` debe contener un objeto `weak_ptr` que apunte a `N0` en lugar de un objeto `shared_ptr`. Puesto que el objeto `weak_ptr` no posee `N0`, no afecta al recuento de referencias de `N0`, y cuando se destruya la última referencia al nodo principal del programa, también se destruirán los nodos de la lista.  
  
## <a name="members"></a>Miembros  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[weak_ptr](#weak_ptr)|Construye un objeto `weak_ptr`.|  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[element_type](#element_type)|Tipo del elemento.|  
|[expired](#expired)|Comprueba si la propiedad ha caducado.|  
|[lock](#lock)|Obtiene la propiedad exclusiva de un recurso.|  
|[owner_before](#owner_before)|Devuelve `true` si este `weak_ptr` está ordenado antes (o es menor que) que el puntero proporcionado.|  
|[reset](#reset)|Libera el recurso poseído.|  
|[swap](#swap)|Intercambia dos objetos `weak_ptr`.|  
|[use_count](#use_count)|Cuenta el número de objetos `shared_ptr` designados.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator=](#op_eq)|Reemplaza el recurso poseído.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<memory>  
  
 **Espacio de nombres:** std  
  
##  <a name="element_type"></a>  element_type  
 Tipo del elemento.  
  
```  
typedef Ty element_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla `Ty`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__weak_ptr_element_type.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()   
    {   
    std::shared_ptr<int> sp0(new int(5));   
    std::weak_ptr<int> wp0(sp0);   
    std::weak_ptr<int>::element_type val = *wp0.lock();   
  
    std::cout << "*wp0.lock() == " << val << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
*wp0.lock() == 5  
```  
  
##  <a name="expired"></a>  expired  
 Comprueba si la propiedad ha caducado.  
  
```  
bool expired() const;
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve `true` si `*this` expiró, de lo contrario, `false`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__weak_ptr_expired.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed   
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
  
```  
  
```Output  
wp.expired() == false  
*wp.lock() == 10  
wp.expired() == true  
(bool)wp.lock() == false  
```  
  
##  <a name="lock"></a>  lock  
 Obtiene la propiedad exclusiva de un recurso.  
  
```  
shared_ptr<Ty> lock() const;
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve un objeto shared_ptr vacío si `*this` expiró. De lo contrario, devuelve un objeto [shared_ptr (Clase)](../standard-library/shared-ptr-class.md)`<Ty>` que posee el recurso al que apunta `*this`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__weak_ptr_lock.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::weak_ptr<int> wp;

    {
        std::shared_ptr<int> sp(new int(10));
        wp = sp;
        std::cout << "wp.expired() == " << std::boolalpha
            << wp.expired() << std::endl;
        std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    }

    // check expired after sp is destroyed   
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;
    std::cout << "(bool)wp.lock() == " << std::boolalpha
        << (bool)wp.lock() << std::endl;

    return (0);
}
  
```  
  
```Output  
wp.expired() == false  
*wp.lock() == 10  
wp.expired() == true  
(bool)wp.lock() == false  
```  
  
##  <a name="op_eq"></a>  operator=  
 Reemplaza el recurso poseído.  
  
```  
weak_ptr& operator=(const weak_ptr& wp);

template <class Other>  
weak_ptr& operator=(const weak_ptr<Other>& wp);

template <class Other>  
weak_ptr& operator=(const shared_ptr<Other>& sp);
```  
  
### <a name="parameters"></a>Parámetros  
 `Other`  
 El tipo controlado por el puntero compartido o débil de argumento.  
  
 `wp`  
 El puntero débil que se va a copiar.  
  
 `sp`  
 El puntero compartido que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 Todos los operadores liberan el recurso al que apunta actualmente `*this` y asignan la propiedad del recurso denominado por la secuencia de operandos a `*this`. Si un operador produce errores, deja a `*this` sin cambios.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__weak_ptr_operator_as.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::weak_ptr<int> wp0(sp0);
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::shared_ptr<int> sp1(new int(10));
    wp0 = sp1;
    std::cout << "*wp0.lock() == " << *wp0.lock() << std::endl;

    std::weak_ptr<int> wp1;
    wp1 = wp0;
    std::cout << "*wp1.lock() == " << *wp1.lock() << std::endl;

    return (0);
}
  
```  
  
```Output  
*wp0.lock() == 5  
*wp0.lock() == 10  
*wp1.lock() == 10  
```  
  
##  <a name="owner_before"></a>  owner_before  
 Devuelve `true` si este `weak_ptr` está ordenado antes (o es menor que) que el puntero proporcionado.  
  
```  
template <class Other>  
bool owner_before(const shared_ptr<Other>& ptr);

template <class Other>  
bool owner_before(const weak_ptr<Other>& ptr);
```  
  
### <a name="parameters"></a>Parámetros  
 `ptr`  
 Una referencia `lvalue` a un `shared_ptr` o un `weak_ptr`.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro de plantilla devuelve `true` si `*this` es `ordered before``ptr`.  
  
##  <a name="reset"></a>  reset  
 Libera el recurso poseído.  
  
```  
void reset();
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro libera el recurso al que apunta `*this` y convierte `*this` en un objeto weak_ptr vacío.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__weak_ptr_reset.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::shared_ptr<int> sp(new int(5));
    std::weak_ptr<int> wp(sp);
    std::cout << "*wp.lock() == " << *wp.lock() << std::endl;
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    wp.reset();
    std::cout << "wp.expired() == " << std::boolalpha
        << wp.expired() << std::endl;

    return (0);
}

```  
  
```Output  
*wp.lock() == 5  
wp.expired() == false  
wp.expired() == true  
```  
  
##  <a name="swap"></a>  swap  
 Intercambia dos objetos `weak_ptr`.  
  
```  
void swap(weak_ptr& wp);
```  
  
### <a name="parameters"></a>Parámetros  
 `wp`  
 El puntero débil que se va a intercambiar.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro deja el recurso al que apuntaba originalmente `*this` para que ahora sea señalado por `wp`, y el recurso al que originalmente apuntaba `wp` para que ahora sea señalado por `*this`. La función no modifica los recuentos de referencia para los dos recursos y no inicia ninguna excepción.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__weak_ptr_swap.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
 
struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}

```  
  
```Output  
*sp1 == 5  
*sp1 == 10  
*sp1 == 5  
  
*wp1 == 5  
*wp1 == 10  
*wp1 == 5  
```  
  
##  <a name="use_count"></a>  use_count  
 Cuenta el número de objetos `shared_ptr` designados.  
  
```  
long use_count() const;
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve el número de objetos `shared_ptr` que poseen el recurso al que apuntaba `*this`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__weak_ptr_use_count.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "wp.use_count() == "
        << wp.use_count() << std::endl;

    return (0);
} 
  
```  
  
```Output  
wp.use_count() == 1  
wp.use_count() == 2  
```  
  
##  <a name="weak_ptr"></a>  weak_ptr  
 Construye un objeto `weak_ptr`.  
  
```  
weak_ptr();

weak_ptr(const weak_ptr& wp);

template <class Other>  
weak_ptr(const weak_ptr<Other>& wp);

template <class Other>  
weak_ptr(const shared_ptr<Other>& sp);
```  
  
### <a name="parameters"></a>Parámetros  
 `Other`  
 El tipo controlado por el puntero compartido o débil de argumento.  
  
 `wp`  
 El puntero débil que se va a copiar.  
  
 `sp`  
 El puntero compartido que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 Los constructores crean un objeto que apunta al recurso denominado por la secuencia de operandos.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__weak_ptr_construct.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::weak_ptr<int> wp0;
    std::cout << "wp0.expired() == " << std::boolalpha
        << wp0.expired() << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::weak_ptr<int> wp1(sp1);
    std::cout << "*wp1.lock() == "
        << *wp1.lock() << std::endl;

    std::weak_ptr<int> wp2(wp1);
    std::cout << "*wp2.lock() == "
        << *wp2.lock() << std::endl;

    return (0);
}
  
```  
  
```Output  
wp0.expired() == true  
*wp1.lock() == 5  
*wp2.lock() == 5  
```  
  
## <a name="see-also"></a>Vea también  
 [shared_ptr (Clase)](../standard-library/shared-ptr-class.md)


