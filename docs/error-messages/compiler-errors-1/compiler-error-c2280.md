---
title: Compilador Error C2280 | Documentos de Microsoft
ms.custom: 
ms.date: 04/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2280
helpviewer_keywords: C2280
dev_langs: C++
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: af19f0a0c347ab0f898a3a3d72b8cca5cb07dad8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2280"></a>C2280 de Error del compilador  
  
'*declaración*': intentando hacer referencia a una función eliminada  
  
El compilador detectó un intento de hacer referencia a un `deleted` función. Este error puede deberse a una llamada a una función miembro que se ha marcado explícitamente como `= deleted` en el código fuente. Este error también puede deberse a una llamada a una función miembro especial implícito de una clase o estructura que se declara automáticamente y se marcan como `deleted` por el compilador. Para obtener más información acerca de si el compilador genera automáticamente `default` o `deleted` funciones miembro especiales, consulte [funciones miembro especiales](../../cpp/special-member-functions.md).  
  
## <a name="example-explicitly-deleted-functions"></a>Ejemplo: Las funciones eliminadas explícitamente  

Una llamada a un explícitamente `deleted` función provoca este error. Una forma explícita `deleted` función miembro implica que la clase o estructura se ha diseñado específicamente para impedir su uso, por lo tanto, para corregir este problema, debe cambiar el código para evitar esta situación.  
  
```cpp  
// C2280_explicit.cpp
// compile with: cl /c /W4 C2280_explicit.cpp
struct A {
    A();
    A(int) = delete;
};

struct B {
    A a1;
    A a2 = A(3); // C2280, calls deleted A::A(int)
    // To fix, remove the call to A(int)
};

void f() {
    B b;    // calls implicit B::B(void)
}
```  
  
## <a name="example-uninitialized-data-members"></a>Ejemplo: Los miembros de datos sin inicializar  
  
Un miembro de datos de tipo de referencia sin inicializar o `const` miembro de datos hace que el compilador declarar implícitamente un `deleted` constructor predeterminado. Para corregir este problema, inicialice al miembro de datos cuando se declara.  
  
```cpp  
// C2280_uninit.cpp
// compile with: cl /c C2280_uninit.cpp
struct A {
    const int i; // uninitialized const-qualified data
    // members or reference type data members cause
    // the implicit default constructor to be deleted.
    // To fix, initialize the value in the declaration:
    // const int i = 42;
} a;    // C2280
```  
  
## <a name="example-reference-and-const-data-members"></a>Ejemplo: Referencia y constantes miembros de datos  
  
A `const` o miembro de datos de tipo de referencia hace que el compilador declarar un `deleted` operador de asignación de copia. Una vez inicializado, estos miembros no se puede asignar, por lo que una simple copia o movimiento no puede funcionar. Para corregir este problema, le recomendamos que cambie la lógica para quitar las operaciones de asignación que producen el error.  
  
```cpp  
// C2280_ref.cpp
// compile with: cl /c C2280_ref.cpp
extern int k;
struct A {
    A();
    int& ri = k; // a const or reference data member causes 
    // implicit copy assignment operator to be deleted.
};

void f() {
    A a1, a2;
    // To fix, consider removing this assignment.
    a2 = a1;    // C2280
}
```  
  
## <a name="example-movable-deletes-implicit-copy"></a>Ejemplo: Móvil elimina copia implícita  
  
Si una clase declara un constructor de movimiento o un operador de asignación de movimiento, pero no declara explícitamente un constructor de copias, el compilador implícitamente declara un constructor de copias y que se define como `deleted`. De forma similar, si una clase declara un constructor de movimiento o un operador de asignación de movimiento, pero no declara explícitamente un operador de asignación de copia, el compilador implícitamente declara un operador de asignación de copia y lo define como `deleted`. Para corregir este problema, debe declarar explícitamente estos miembros.  
 
Cuando aparezca el error C2280 en relación con un `unique_ptr`, es casi seguro porque está intentando invocar su constructor de copias, que es un `deleted` función. De forma predeterminada, un `unique_ptr` no se pueden copiar. Utilice un constructor de movimiento para transferir la propiedad en su lugar.  

```cpp  
// C2280_move.cpp
// compile with: cl /c C2280_move.cpp
class base  
{  
public:  
    base();  
    ~base(); 
    base(base&&); 
    // Move constructor causes copy constructor to be
    // implicitly declared as deleted. To fix this 
    // issue, you can explicitly declare a copy constructor:
    // base(base&);
    // If you want the compiler default version, do this:
    // base(base&) = default;
};  

void copy(base *p)  
{  
    base b{*p};  // C2280
}  
```  

## <a name="example-variant-and-volatile-members"></a>Ejemplo: Los miembros de tipo Variant y volatile  
  
Las versiones del compilador antes de Visual Studio 2015 Update 2 eran constructores y destructores para uniones anónimas predeterminados generados y no conformes. Estos ahora se declaran implícitamente como `deleted`. Esas versiones también permiten la definición implícita que no cumple las especificaciones de `default` copiar y constructores de movimiento y `default` copiar y mover los operadores de asignación de clases y estructuras que tienen `volatile` variables de miembro. El compilador ahora tiene en cuenta que tienen constructores no triviales y operadores de asignación y no genera `default` implementaciones. Cuando esta clase es un miembro de una unión o una unión anónima dentro de una clase, los constructores de copia y movimiento y operadores de asignación de copia y movimiento de la unión o clase se definen implícitamente como `deleted`. Para corregir este problema, debe declarar explícitamente las funciones miembro especiales necesarios.  
  
```cpp  
// C2280_variant.cpp
// compile with: cl /c C2280_variant.cpp
struct A {  
    A() = default;
    A(const A&);
};  

struct B {  
    union {  
        A a;  
        int i;  
    };
    // To fix this issue, declare the required 
    // special member functions:
    // B(); 
    // B(const B& b);
};  

int main() {
    B b1;  
    B b2(b1);  // C2280  
}
```  
  
## <a name="example-indirect-base-members-deleted"></a>Ejemplo: Miembros de base indirectos eliminar  
  
Las versiones del compilador antes de Visual Studio 2015 Update 2 se no conformes y permite una clase derivada para llamar a funciones de derivadas indirectamente miembro especial `private virtual` clases base. El compilador emite ahora el error del compilador C2280 cuando se realiza una llamada de este tipo.  
  
En este ejemplo, la clase `top` deriva indirectamente privada virtual `base`. En el código que cumplan el estándar, esto hace que los miembros de `base` inaccesible para `top`; un objeto de tipo `top` no puede ser predeterminado construya o se destruya. Para corregir este problema en el código que dependiera del comportamiento anterior del compilador, cambie la clase intermedia para usar `protected virtual` derivación o cambiar la `top` clase utiliza la derivación directa:  

```cpp  
// C2280_indirect.cpp
// compile with: cl /c C2280_indirect.cpp
class base  
{  
protected:  
    base();  
    ~base();  
};  

class middle : private virtual base {}; 
// Possible fix: Replace line above with:
// class middle : protected virtual base {};
class top : public virtual middle {};    // C4594, C4624
// Another possible fix: use direct derivation:
// class top : public virtual middle, private virtual base {};   

void destroy(top *p)  
{  
    delete p;  // C2280  
}  
```  
  