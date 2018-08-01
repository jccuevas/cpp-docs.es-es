---
title: Control de acceso de miembro (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- access control [C++]
- member access [C++]
- member-access control [C++]
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28f0cedbe20ebea21b3b10e5016605c1bce51383
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407392"
---
# <a name="member-access-control-c"></a>Control de acceso a miembros (C++)
Controles de acceso le permiten separar el [pública](../cpp/public-cpp.md) interfaz de una clase desde el [privada](../cpp/private-cpp.md) los detalles de implementación y la [protegido](../cpp/protected-cpp.md) usando los miembros que son únicamente para clases derivadas. El especificador de acceso se aplica a todos los miembros declarados después de él hasta que se encuentra el especificador de acceso siguiente.  
  
```cpp 
class Point  
{  
public:                   
    Point( int, int ) // Declare public constructor.;  
    Point();// Declare public default constructor.  
    int &x( int ); // Declare public accessor.  
    int &y( int ); // Declare public accessor.  
  
private:                 // Declare private state variables.  
    int _x;  
    int _y;  
  
protected:      // Declare protected function for derived classes only.  
    Point ToWindowCoords();  
};  
``` 
  
 El acceso predeterminado es **privada** en una clase, y **pública** en una estructura o unión. Los especificadores de acceso de una clase se pueden usar cualquier número de veces en cualquier orden. La asignación de almacenamiento para objetos de tipos de clase depende de la implementación, pero se garantiza que a los miembros se les asignen direcciones de memoria sucesivamente superiores entre los especificadores de acceso.  
  
### <a name="member-access-control"></a>Control de acceso a miembros  
  
|Tipo de Acceso|Significado|  
|--------------------|-------------|  
|[private](../cpp/private-cpp.md)|Miembros de clase declarados como **privada** puede usarse únicamente por las funciones miembro y Friend (clases o funciones) de la clase.|  
|[protected](../cpp/protected-cpp.md)|Miembros de clase declarados como **protegido** puede usar las funciones miembro y Friend (clases o funciones) de la clase. Además, las clases derivadas de la clase también pueden usarlos.|  
|[public](../cpp/public-cpp.md)|Miembros de clase declarados como **pública** se puede usar cualquier función.|  
  
 El control de acceso impiden usar objetos de manera diferente a la que están destinados. Esta protección se pierde cuando se realizan conversiones de tipos explícitas.  
  
> [!NOTE]
>  El control de acceso también es aplicable a todos los nombres: funciones miembro, datos de miembro, clases anidadas y enumeradores.  
  
## <a name="access-control-in-derived-classes"></a>Control de acceso en clases derivadas  
 Dos factores controlan los miembros de una clase base que están accesibles en una clase derivada; estos mismos factores controlan el acceso a los miembros heredados en la clase derivada:  
  
-   Si la clase derivada declara la clase base mediante la **pública** especificador de acceso.  
  
-   Que el acceso al miembro esté en la clase base.  
  
 En la tabla siguiente se muestra la interacción entre estos factores y cómo se determina el acceso a miembros de clase base.  
  
### <a name="member-access-in-base-class"></a>Acceso a miembros de clase base  
  
|private|protected|Public|  
|-------------|---------------|------------|  
|Siempre inaccesible independientemente del acceso de derivación|Privado en la clase derivada si se utiliza la derivación privada|Privado en la clase derivada si se utiliza la derivación privada|  
||Protegido en la clase derivada si se utiliza la derivación protegida|Protegido en la clase derivada si se utiliza la derivación protegida|  
||Protegido en la clase derivada si se utiliza la derivación pública|Público en la clase derivada si se utiliza la derivación pública|  
  
 Esto se ilustra en el siguiente ejemplo:  
  
```cpp 
// access_specifiers_for_base_classes.cpp  
class BaseClass  
{  
public:  
    int PublicFunc();    // Declare a public member.  
protected:  
    int ProtectedFunc(); // Declare a protected member.  
private:  
    int PrivateFunc();   // Declare a private member.  
};  
  
// Declare two classes derived from BaseClass.  
class DerivedClass1 : public BaseClass  
{  
};  
  
class DerivedClass2 : private BaseClass  
{  
};  
  
int main()  
{  
}  
```  
  
 En `DerivedClass1`, la función miembro `PublicFunc` es un miembro público y `ProtectedFunc` es un miembro protegido porque `BaseClass` es una clase base pública. `PrivateFunc` es privado para `BaseClass`, y es inaccesible en cualquiera de sus clases derivadas.  
  
 En `DerivedClass2`, las funciones `PublicFunc` y `ProtectedFunc` se consideran miembros privados porque `BaseClass` es una clase base privada. De nuevo, `PrivateFunc` es privado para `BaseClass`, y es inaccesible en cualquiera de sus clases derivadas.  
  
 Puede declarar una clase derivada sin un especificador de acceso de clase base. En tal caso, la derivación se considera privada si la declaración de clase derivada utiliza la **clase** palabra clave. La derivación se considera pública si la declaración de clase derivada utiliza la **struct** palabra clave. Por ejemplo, el código siguiente:  
  
```cpp 
class Derived : Base  
...  
```  
  
 equivale a:  
  
```cpp 
class Derived : private Base  
...  
```  
  
 De igual forma, el código siguiente:  
  
```cpp 
struct Derived : Base  
...  
```  
  
 equivale a:  
  
```cpp 
struct Derived : public Base  
...  
```  
  
 Tenga en cuenta que los miembros declarados como si tuviera acceso privado no son accesibles a las funciones o clases derivadas a menos que esas funciones o clases se declaran mediante la **friend** declaración de la clase base.  
  
 Un **unión** tipo no puede tener una clase base.  
  
> [!NOTE]
>  Al especificar una clase base privada, es aconsejable usar explícitamente la **privada** palabra clave para que los usuarios de la clase derivada sepan el acceso a miembros.  
  
## <a name="access-control-and-static-members"></a>Control de acceso y miembros estáticos  
 Cuando se especifica una clase base como **privada**, afecta a solo los miembros no estáticos. Los miembros estáticos públicos siguen siendo accesibles en las clases derivadas. Sin embargo, el acceso a los miembros de la clase base mediante el uso de punteros, referencias u objetos puede requerir una conversión en la que se aplica de nuevo el control de acceso de tiempo. Considere el ejemplo siguiente:  
  
```cpp 
// access_control.cpp  
class Base  
{  
public:  
    int Print();             // Nonstatic member.  
    static int CountOf();    // Static member.  
};  
  
// Derived1 declares Base as a private base class.  
class Derived1 : private Base  
{  
};  
// Derived2 declares Derived1 as a public base class.  
class Derived2 : public Derived1  
{  
    int ShowCount();    // Nonstatic member.  
};  
// Define ShowCount function for Derived2.  
int Derived2::ShowCount()  
{  
   // Call static member function CountOf explicitly.  
    int cCount = Base::CountOf();     // OK.  
  
   // Call static member function CountOf using pointer.  
    cCount = this->CountOf();  // C2247. Conversion of  
                               //  Derived2 * to Base * not  
                               //  permitted.  
    return cCount;  
}  
```  
  
 En el código anterior, el control de acceso prohíbe la conversión de un puntero a `Derived2` en un puntero a `Base`. El **esto** puntero es implícitamente del tipo `Derived2 *`. Para seleccionar el `CountOf` función, **esto** debe convertirse al tipo `Base *`. Este tipo de conversión no está permitido porque `Base` es una clase base indirecta privada a `Derived2`. La conversión a un tipo de clase base privada solo es aceptable para punteros a clases derivadas inmediatas. Por lo tanto, los punteros de tipo `Derived1 *` pueden convertirse al tipo `Base *`.  
  
 Observe que la llamada explícita a la función `CountOf`, sin utilizar un puntero, una referencia o un objeto para seleccionarla, no implica ninguna conversión. Por lo tanto, se permite la llamada.  
  
 Los miembros y objetos friend de una clase derivada, `T`, pueden convertir un puntero a `T` en un puntero a una clase base directa privada de `T`.  
  
## <a name="access-to-virtual-functions"></a>Acceso a funciones virtuales  
 El control de acceso se aplica a [virtual](../cpp/virtual-cpp.md) funciones viene determinada por el tipo utilizado para llamar a la función. El reemplazo de las declaraciones de la función no afecta al control de acceso para un tipo determinado. Por ejemplo:  
  
```cpp 
// access_to_virtual_functions.cpp  
class VFuncBase  
{  
public:  
    virtual int GetState() { return _state; }  
protected:  
    int _state;  
};  
  
class VFuncDerived : public VFuncBase  
{  
private:  
    int GetState() { return _state; }  
};  
  
int main()  
{  
   VFuncDerived vfd;             // Object of derived type.  
   VFuncBase *pvfb = &vfd;       // Pointer to base type.  
   VFuncDerived *pvfd = &vfd;    // Pointer to derived type.  
   int State;  
  
   State = pvfb->GetState();     // GetState is public.  
   State = pvfd->GetState();     // C2248 error expected; GetState is private;  
}  
```  
  
 En el ejemplo anterior, al llamar a la función virtual `GetState` mediante un puntero al tipo `VFuncBase`, se llama a `VFuncDerived::GetState`, y `GetState` se trata como public. Sin embargo, la llamada a `GetState` mediante un puntero al tipo `VFuncDerived` se considera una infracción del control de acceso, porque `GetState` se declara private en la clase `VFuncDerived`.  
  
> [!CAUTION]
>  La función virtual `GetState` se puede llamar mediante un puntero a la clase base `VFuncBase`. Esto no significa que la función llamada sea la versión de la clase base de esa función.  
  
## <a name="access-control-with-multiple-inheritance"></a>Control de acceso con herencia múltiple  
 En los entramados de herencia múltiple con clases base virtuales, se puede acceder a un nombre determinado a través de más de una ruta. Dado que se puede aplicar un control de acceso diferente en estas rutas de acceso diferentes, el compilador elige la ruta de acceso que proporciona el mejor acceso. Vea la ilustración siguiente.  
  
 ![Acceso a lo largo de rutas de acceso de un gráfico de herencia](../cpp/media/vc38v91.gif "vc38V91")  
Acceso a través de las rutas de acceso de un gráfico de herencia  
  
 En la ilustración, se accede a un nombre declarado en la clase `VBase` siempre a través de la clase `RightPath`. La ruta de acceso derecha es más accesible porque `RightPath` declara `VBase` como clase base pública, mientras que `LeftPath` declara `VBase` como private.  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)