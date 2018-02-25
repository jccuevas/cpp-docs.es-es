---
title: shared_ptr (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- memory/std::shared_ptr
- memory/std::shared_ptr::element_type
- memory/std::shared_ptr::get
- memory/std::shared_ptr::owner_before
- memory/std::shared_ptr::reset
- memory/std::shared_ptr::swap
- memory/std::shared_ptr::unique
- memory/std::shared_ptr::use_count
- memory/std::shared_ptr::operator boolean-type
- memory/std::shared_ptr::operator*
- memory/std::shared_ptr::operator=
- memory/std::shared_ptr::operator->
dev_langs:
- C++
helpviewer_keywords:
- std::shared_ptr [C++]
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
- std::shared_ptr [C++], element_type
- std::shared_ptr [C++], get
- std::shared_ptr [C++], owner_before
- std::shared_ptr [C++], reset
- std::shared_ptr [C++], swap
- std::shared_ptr [C++], unique
- std::shared_ptr [C++], use_count
ms.assetid: 1469fc51-c658-43f1-886c-f4530dd84860
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ef826862d49b5661b57faf3db1322cd91b273f9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="sharedptr-class"></a>shared_ptr (Clase)
Encapsula un puntero inteligente en el que se cuentan las referencias alrededor de un objeto asignado dinámicamente.  
  
## <a name="syntax"></a>Sintaxis  
```
template <class T>
class shared_ptr; 
```  
  
## <a name="remarks"></a>Comentarios  
 La clase shared_ptr describe un objeto que usa el recuento de referencias para administrar recursos. Un objeto `shared_ptr` contiene eficazmente un puntero al recurso que posee o contiene un puntero null. Un recurso puede ser propiedad de más de un objeto `shared_ptr`; cuando se destruye el último objeto `shared_ptr` que posee un recurso determinado, se libera el recurso.  
  
 Un `shared_ptr` deja de ser el propietario de un recurso cuando se reasigna o se restablece.  
  
 El argumento de plantilla `T` puede ser un tipo incompleto, salvo lo indicado para ciertas funciones miembro.  
  
 Cuando se construye un objeto `shared_ptr<T>` desde un puntero de recursos de tipo `G*` o desde un `shared_ptr<G>`, el tipo de puntero `G*` debe poder convertirse a `T*`. Si no es así, el código no se compilará. Por ejemplo:  
  
```cpp  
#include <memory>  
using namespace std;  
  
class F {};  
class G : public F {};  
  
shared_ptr<G> sp0(new G);   // okay, template parameter G and argument G*  
shared_ptr<G> sp1(sp0);     // okay, template parameter G and argument shared_ptr<G>  
shared_ptr<F> sp2(new G);   // okay, G* convertible to F*  
shared_ptr<F> sp3(sp0);     // okay, template parameter F and argument shared_ptr<G>  
shared_ptr<F> sp4(sp2);     // okay, template parameter F and argument shared_ptr<F>  
shared_ptr<int> sp5(new G); // error, G* not convertible to int*  
shared_ptr<int> sp6(sp2);   // error, template parameter int and argument shared_ptr<F>  
```  
  
 Un objeto `shared_ptr` posee un recurso:  
  
-   si se construyó con un puntero a ese recurso,  
  
-   si se construyó desde un objeto `shared_ptr` que posee ese recurso,  
  
-   si se construyó desde un objeto [weak_ptr (Clase)](../standard-library/weak-ptr-class.md) que apunta a ese recurso, o  
  
-   si se le asignó la propiedad de ese recurso, ya sea con [shared_ptr::operator=](#op_eq) o mediante una llamada a la función miembro [shared_ptr::reset](#reset).  
  
 Los objetos `shared_ptr` que poseen un recurso comparten un bloque de control. El bloque de control contiene:  
  
-   el número de objetos `shared_ptr` que poseen el recurso,  
  
-   el número de objetos `weak_ptr` que apuntan al recurso,  
  
-   el eliminador para ese recurso, si existe,  
  
-   el asignador personalizado para el bloque de control, si tiene alguno.  
  
 Un objeto `shared_ptr` que se inicializa mediante un puntero NULL tiene un bloque de control y no está vacío. Después de que un objeto `shared_ptr` libera un recurso, ya no posee ese recurso. Después de que un objeto `weak_ptr` libera un recurso, ya no apunta a ese recurso.  
  
 Cuando el número de objetos `shared_ptr` que poseen un recurso es cero, el recurso se libera eliminándolo o pasando su dirección a un eliminador, según cómo se creara originalmente la propiedad del recurso. Cuando el número de objetos `shared_ptr` que poseen un recurso es cero, y el número de objetos `weak_ptr` que apuntan a ese recurso es cero, el bloque de control se libera, utilizando el asignador personalizado para el bloque de control si tiene alguno.  
  
 Un objeto `shared_ptr` vacío no posee ningún recurso y no tiene ningún bloque de control.  
  
 Un eliminador es un objeto de función que tiene una función miembro `operator()`. Su tipo se debe poder construir mediante copia, y su constructor y destructor de copias no deben producir excepciones. Acepta un parámetro: el objeto que se va a eliminar.  
  
 Algunas funciones toman una lista de argumentos que define propiedades del objeto `shared_ptr<T>` o `weak_ptr<T>` resultante. Hay varias maneras de especificar esta lista de argumentos:  
  
 sin argumentos: el objeto resultante es un objeto `shared_ptr` o `weak_ptr` vacío.  
  
 `ptr`: puntero de tipo `Other*` al recurso que se va a administrar. `T` debe ser un tipo completo. Si se produce un error en la función (porque no se puede asignar el bloque de control), evalúa la expresión `delete ptr`.  
  
 `ptr, dtor`: puntero de tipo `Other*` al recurso que se va a administrar y un eliminador para ese recurso. Si se produce un error en la función (porque no se puede asignar el bloque de control), llama a `dtor(ptr)`, que deben estar bien definido.  
  
 `ptr, dtor, alloc`: puntero de tipo `Other*` al recurso que se va a administrar, un eliminador para ese recurso y un asignador para administrar cualquier almacenamiento que se deba asignar y liberar. Si se produce un error en la función (porque no se puede asignar el bloque de control), llama a `dtor(ptr)`, que deben estar bien definido.  
  
 `sp`: objeto `shared_ptr<Other>` que posee el recurso que se va a administrar.  
  
 `wp`: objeto `weak_ptr<Other>` que apunta al recurso que se va a administrar.  
  
 `ap`: objeto `auto_ptr<Other>` que contiene un puntero al recurso que se va a administrar. Si la función se ejecuta correctamente, llama a `ap.release()`; de lo contrario, deja `ap` sin modificar.  
  
 En todos los casos, el tipo de puntero `Other*` debe poder convertirse a `T*`.  
  
## <a name="thread-safety"></a>Seguridad para subprocesos  
 Varios subprocesos pueden leer y escribir diferentes objetos `shared_ptr` al mismo tiempo, incluso cuando los objetos son copias que comparten la propiedad.  
  
## <a name="members"></a>Miembros  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[shared_ptr](#shared_ptr)|Construye un objeto `shared_ptr`.|  
|[shared_ptr::~shared_ptr](#dtorshared_ptr)|Destruye un objeto `shared_ptr`.|  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[element_type](#element_type)|El tipo de un elemento.|  
|[get](#get)|Obtiene la dirección del recurso propio.|  
|[owner_before](#owner_before)|Devuelve true si este `shared_ptr` está ordenado antes (o es menor que) que el puntero proporcionado.|  
|[reset](#reset)|Reemplaza el recurso propio.|  
|[swap](#swap)|Intercambia dos objetos `shared_ptr`.|  
|[unique](#unique)|Comprueba si el recurso propio es único.|  
|[use_count](#use_count)|Cuenta los números de propietarios del recurso.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[shared_ptr::operator boolean-type](#op_boolean-type)|Comprueba si existe un recurso propio.|  
|[shared_ptr::operator*](#op_star)|Obtiene el valor designado.|  
|[shared_ptr::operator=](#op_eq)|Reemplaza el recurso propio.|  
|[shared_ptr::operator-&gt;](#operator-_gt)|Obtiene un puntero al valor designado.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<memory>  
  
 **Espacio de nombres:** std  
  
##  <a name="element_type"></a>  shared_ptr::element_type  
 El tipo de un elemento.  
  
```  
typedef T element_type;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla `T`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__shared_ptr_element_type.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::shared_ptr<int> sp0(new int(5));
    std::shared_ptr<int>::element_type val = *sp0;

    std::cout << "*sp0 == " << val << std::endl;

    return (0);
}

```  
  
```Output  
*sp0 == 5  
```  
  
##  <a name="get"></a>  shared_ptr::get  
 Obtiene la dirección del recurso propio.  
  
```  
T *get() const;
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve la dirección del recurso propietario. Devuelve 0 si el objeto no dispone de un recurso.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__shared_ptr_get.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "sp0.get() == 0 == " << std::boolalpha
        << (sp0.get() == 0) << std::endl;
    std::cout << "*sp1.get() == " << *sp1.get() << std::endl;

    return (0);
}

```  
  
```Output  
sp0.get() == 0 == true  
*sp1.get() == 5  
```  
  
##  <a name="shared_ptr__operator_boolean-type"></a>  shared_ptr::operator boolean-type  
 Comprueba si existe un recurso propio.  
  
```  
operator boolean-type() const;
```  
  
### <a name="remarks"></a>Comentarios  
 El operador devuelve un valor de un tipo que pueda convertirse en `bool`. El resultado de la conversión en `bool` es `true` cuando `get() != 0`, si no `false`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__shared_ptr_operator_bool.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   

int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));

    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;
    std::cout << "(bool)sp1 == " << std::boolalpha
        << (bool)sp1 << std::endl;

    return (0);
}

```  
  
```Output  
(bool)sp0 == false  
(bool)sp1 == true  
```  
  
##  <a name="op_star"></a>  shared_ptr::operator*  
 Obtiene el valor designado.  
  
```  
T& operator*() const;
```  
  
### <a name="remarks"></a>Comentarios  
 El operador de direccionamiento indirecto devuelve `*get()`. Por tanto, el puntero almacenado no debe ser null.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__shared_ptr_operator_st.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::shared_ptr<int> sp0(new int(5));

    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}

```  
  
```Output  
*sp0 == 5  
```  
  
##  <a name="op_eq"></a>  shared_ptr::operator=  
 Reemplaza el recurso propio.  
  
```  
shared_ptr& operator=(const shared_ptr& sp);

template <class Other>  
shared_ptr& operator=(const shared_ptr<Other>& sp);

template <class Other>  
shared_ptr& operator=(auto_ptr<Other>& ap);

template <class Other>  
shared_ptr& operator=(auto_ptr<Other>& ap);

template <class Other>  
shared_ptr& operator=(auto_ptr<Other>&& ap);

template <class Other, class Deletor>  
shared_ptr& operator=(unique_ptr<Other, Deletor>&& ap);
```  
  
### <a name="parameters"></a>Parámetros  
 `sp`  
 El puntero compartido que se va a copiar.  
  
 `ap`  
 El puntero automático que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 Todos los operadores disminuyen el recuento de referencias para el recurso que posee actualmente `*this` y asignan la propiedad del recurso denominado por la secuencia de operandos a `*this`. Si el recuento de referencias llega a cero, se libera el recurso. Si un operador produce errores, deja a `*this` sin cambios.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__shared_ptr_operator_as.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::shared_ptr<int> sp0;
    std::shared_ptr<int> sp1(new int(5));
    std::auto_ptr<int> ap(new int(10));

    sp0 = sp1;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    sp0 = ap;
    std::cout << "*sp0 == " << *sp0 << std::endl;

    return (0);
}

```  
  
```Output  
*sp0 == 5  
*sp0 == 10  
```  
  
##  <a name="shared_ptr__operator-_gt"></a>  shared_ptr::operator-&gt;  
 Obtiene un puntero al valor designado.  
  
```  
T * operator->() const;
```  
  
### <a name="remarks"></a>Comentarios  
 El operador de selección devuelve `get()`, de modo que la expresión `sp->member` se comporta igual que `(sp.get())->member` donde `sp` es un objeto de clase `shared_ptr<T>`. Por tanto, el puntero almacenado no debe ser null, y `T` debe ser una clase, estructura o tipo de unión con un miembro `member`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__shared_ptr_operator_ar.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
typedef std::pair<int, int> Mypair;
int main()
{
    std::shared_ptr<Mypair> sp0(new Mypair(1, 2));

    std::cout << "sp0->first == " << sp0->first << std::endl;
    std::cout << "sp0->second == " << sp0->second << std::endl;

    return (0);
}
  
```  
  
```Output  
sp0->first == 1  
sp0->second == 2  
```  
  
##  <a name="owner_before"></a>  shared_ptr::owner_before  
 Devuelve true si este `shared_ptr` está ordenado antes (o es menor que) que el puntero proporcionado.  
  
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
 La función de miembro de plantilla devuelve true si `*this` es `ordered before` `ptr`.  
  
##  <a name="reset"></a>  shared_ptr::reset  
 Reemplaza el recurso propio.  
  
```  
void reset();

template <class Other>  
void reset(Other *ptr;);

template <class Other, class D>  
void reset(Other *ptr, D dtor);

template <class Other, class D, class A>  
void reset(Other *ptr, D dtor, A alloc);
```  
  
### <a name="parameters"></a>Parámetros  
 `Other`  
 Tipo controlado por el puntero de argumento.  
  
 `D`  
 Tipo del eliminador.  
  
 `ptr`  
 Puntero que se va a copiar.  
  
 `dtor`  
 El eliminador que se va a copiar.  
  
 `A`  
 Tipo del asignador.  
  
 `alloc`  
 El asignador que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 Todos los operadores disminuyen el recuento de referencias para el recurso que posee actualmente `*this` y asignan la propiedad del recurso denominado por la secuencia de operandos a `*this`. Si el recuento de referencias llega a cero, se libera el recurso. Si un operador produce errores, deja a `*this` sin cambios.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__shared_ptr_reset.cpp   
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
    std::shared_ptr<int> sp(new int(5));

    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset();
    std::cout << "(bool)sp == " << std::boolalpha
        << (bool)sp << std::endl;

    sp.reset(new int(10));
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    sp.reset(new int(15), deleter());
    std::cout << "*sp == " << std::boolalpha
        << *sp << std::endl;

    return (0);
}
  
```  
  
```Output  
*sp == 5  
(bool)sp == false  
*sp == 10  
*sp == 15  
```  
  
##  <a name="shared_ptr"></a>  shared_ptr::shared_ptr  
 Construye un objeto `shared_ptr`.  
  
```  
shared_ptr();

shared_ptr(nullptr_t);

shared_ptr(const shared_ptr& sp);

shared_ptr(shared_ptr&& sp);

template <class Other>  
explicit shared_ptr(Other* ptr);

template <class Other, class D>  
shared_ptr(Other* ptr, D dtor);

template <class D>  
shared_ptr(nullptr_t ptr, D dtor);

template <class Other, class D, class A>  
shared_ptr(Other* ptr, D dtor, A  alloc);

template <class D, class A>  
shared_ptr(nullptr_t ptr, D dtor, A alloc);

template <class Other>  
shared_ptr(const shared_ptr<Other>& sp);

template <class Other>  
shared_ptr(const weak_ptr<Other>& wp);

template <class &>  
shared_ptr(std::auto_ptr<Other>& ap);

template <class &>  
shared_ptr(std::auto_ptr<Other>&& ap);

template <class Other, class D>  
shared_ptr(unique_ptr<Other, D>&& up);

template <class Other>  
shared_ptr(const shared_ptr<Other>& sp, T* ptr);

template <class Other, class D>  
shared_ptr(const unique_ptr<Other, D>& up) = delete;  
```  
  
### <a name="parameters"></a>Parámetros  
 `Other`  
 Tipo controlado por el puntero de argumento.  
  
 `ptr`  
 Puntero que se va a copiar.  
  
 `D`  
 Tipo del eliminador.  
  
 `A`  
 Tipo del asignador.  
  
 `dtor`  
 Eliminador.  
  
 `ator`  
 Asignador.  
  
 `sp`  
 El puntero inteligente que se va a copiar.  
  
 `wp`  
 El puntero débil.  
  
 `ap`  
 El puntero automático que se va a copiar.  
  
### <a name="remarks"></a>Comentarios  
 Los constructores crean un objeto que posee el recurso denominado por la secuencia de operandos. El constructor `shared_ptr(const weak_ptr<Other>& wp)` inicia un objeto de excepción de tipo [bad_weak_ptr (Clase)](../standard-library/bad-weak-ptr-class.md) si `wp.expired()`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__shared_ptr_construct.cpp   
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
    std::shared_ptr<int> sp0;
    std::cout << "(bool)sp0 == " << std::boolalpha
        << (bool)sp0 << std::endl;

    std::shared_ptr<int> sp1(new int(5));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    std::shared_ptr<int> sp2(new int(10), deleter());
    std::cout << "*sp2 == " << *sp2 << std::endl;

    std::shared_ptr<int> sp3(sp2);
    std::cout << "*sp3 == " << *sp3 << std::endl;

    std::weak_ptr<int> wp(sp3);
    std::shared_ptr<int> sp4(wp);
    std::cout << "*sp4 == " << *sp4 << std::endl;

    std::auto_ptr<int> ap(new int(15));
    std::shared_ptr<int> sp5(ap);
    std::cout << "*sp5 == " << *sp5 << std::endl;

    return (0);
}

```  
  
```Output  
(bool)sp0 == false  
*sp1 == 5  
*sp2 == 10  
*sp3 == 10  
*sp4 == 10  
*sp5 == 15  
```  
  
##  <a name="dtorshared_ptr"></a>  shared_ptr::~shared_ptr  
 Destruye un objeto `shared_ptr`.  
  
```  
~shared_ptr();
```  
  
### <a name="remarks"></a>Comentarios  
 El destructor disminuye el recuento de referencias para el recurso que posee actualmente `*this`. Si el recuento de referencias llega a cero, se libera el recurso.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__shared_ptr_destroy.cpp   
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
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << "use count == " << sp1.use_count() << std::endl;

    {
        std::shared_ptr<int> sp2(sp1);
        std::cout << "*sp2 == " << *sp2 << std::endl;
        std::cout << "use count == " << sp1.use_count() << std::endl;
    }

    // check use count after sp2 is destroyed   
    std::cout << "use count == " << sp1.use_count() << std::endl;

    return (0);
}
  
```  
  
```Output  
*sp1 == 5  
use count == 1  
*sp2 == 5  
use count == 2  
use count == 1  
```  
  
##  <a name="swap"></a>  shared_ptr::swap  
 Intercambia dos objetos `shared_ptr`.  
  
```  
void swap(shared_ptr& sp);
```  
  
### <a name="parameters"></a>Parámetros  
 `sp`  
 El puntero compartido que se va a intercambiar.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro deja el recurso originalmente propiedad de `*this` para que ahora sea propiedad de `sp` y el recurso originalmente propiedad de `sp` para que ahora sea propiedad de `*this`. La función no modifica los recuentos de referencia para los dos recursos y no inicia ninguna excepción.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__shared_ptr_swap.cpp   
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
  
##  <a name="unique"></a>  shared_ptr::unique  
 Comprueba si el recurso propio es único.  
  
```  
bool unique() const;
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve `true` si ningún otro objeto `shared_ptr` posee el recurso que es propiedad de `*this`, de lo contrario, `false`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__shared_ptr_unique.cpp   
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
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.unique() == " << std::boolalpha
        << sp1.unique() << std::endl;

    return (0);
}

```  
  
```Output  
sp1.unique() == true  
sp1.unique() == false  
```  
  
##  <a name="use_count"></a>  shared_ptr::use_count  
 Cuenta los números de propietarios del recurso.  
  
```  
long use_count() const;
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve el número de objetos `shared_ptr` que poseen el recurso que es propiedad de `*this`.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// std__memory__shared_ptr_use_count.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    std::shared_ptr<int> sp2(sp1);
    std::cout << "sp1.use_count() == "
        << sp1.use_count() << std::endl;

    return (0);
}

```  
  
```Output  
sp1.use_count() == 1  
sp1.use_count() == 2  
```  
  
## <a name="see-also"></a>Vea también  
 [weak_ptr (Clase)](../standard-library/weak-ptr-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)




