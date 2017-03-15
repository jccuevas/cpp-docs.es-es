---
title: "Control de acceso a miembros (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de acceso [C++]"
  - "acceso a miembros [C++]"
  - "control de acceso a miembro [C++]"
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Control de acceso a miembros (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los controles de acceso le permiten separar la interfaz [pública](../cpp/public-cpp.md) de una clase de los detalles de implementación [privados](../cpp/private-cpp.md) y los miembros [protegidos](../cpp/protected-cpp.md) que están destinados solo para su uso por parte de clases derivadas.  El especificador de acceso se aplica a todos los miembros declarados después de él hasta que se encuentra el especificador de acceso siguiente.  
  
```  
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
  
 El acceso predeterminado es `private` en una clase y `public` en una estructura o unión.  Los especificadores de acceso de una clase se pueden usar cualquier número de veces en cualquier orden.  La asignación de almacenamiento para objetos de tipos de clase depende de la implementación, pero se garantiza que a los miembros se les asignen direcciones de memoria sucesivamente superiores entre los especificadores de acceso.  
  
### Control de acceso a miembros  
  
|Tipo de Acceso|Significado|  
|--------------------|-----------------|  
|[private](../cpp/private-cpp.md)|Las funciones y las clases o funciones friend de la clase pueden usar los miembros de clase declarados como `private`.|  
|[protected](../cpp/protected-cpp.md)|Solo las funciones y las clases o funciones friend de la clase pueden usar los miembros de clase declarados como `protected`.  Además, las clases derivadas de la clase también pueden usarlos.|  
|[public](../cpp/public-cpp.md)|Cualquier función puede usar los miembros de clase declarados como **public**.|  
  
 El control de acceso impiden usar objetos de manera diferente a la que están destinados.  Esta protección se pierde cuando se realizan conversiones de tipos explícitas.  
  
> [!NOTE]
>  El control de acceso también es aplicable a todos los nombres: funciones miembro, datos de miembro, clases anidadas y enumeradores.  
  
## Control de acceso en clases derivadas  
 Dos factores controlan los miembros de una clase base que están accesibles en una clase derivada; estos mismos factores controlan el acceso a los miembros heredados en la clase derivada:  
  
-   Si la clase derivada declara la clase base mediante el especificador de acceso **public** en el elemento de encabezado de clase *class\-head* \(el elemento *class\-head* se describe en la sección de gramática del tema sobre [Definir tipos de clase](http://msdn.microsoft.com/es-es/e8c65425-0f3a-4dca-afc2-418c3b1e57da)\).  
  
-   Que el acceso al miembro esté en la clase base.  
  
 En la tabla siguiente se muestra la interacción entre estos factores y cómo se determina el acceso a miembros de clase base.  
  
### Acceso a miembros de clase base  
  
|private|protected|Público|  
|-------------|---------------|-------------|  
|Siempre inaccesible independientemente del acceso de derivación|Privado en la clase derivada si se utiliza la derivación privada|Privado en la clase derivada si se utiliza la derivación privada|  
||Protegido en la clase derivada si se utiliza la derivación protegida|Protegido en la clase derivada si se utiliza la derivación protegida|  
||Protegido en la clase derivada si se utiliza la derivación pública|Público en la clase derivada si se utiliza la derivación pública|  
  
 Esto se ilustra en el siguiente ejemplo:  
  
```  
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
  
 En `DerivedClass1`, la función miembro `PublicFunc` es un miembro público y `ProtectedFunc` es un miembro protegido porque `BaseClass` es una clase base pública.  `PrivateFunc` es privado para `BaseClass`, y es inaccesible en cualquiera de sus clases derivadas.  
  
 En `DerivedClass2`, las funciones `PublicFunc` y `ProtectedFunc` se consideran miembros privados porque `BaseClass` es una clase base privada.  De nuevo, `PrivateFunc` es privado para `BaseClass`, y es inaccesible en cualquiera de sus clases derivadas.  
  
 Puede declarar una clase derivada sin un especificador de acceso de clase base.  En tal caso, la derivación se considera privada si la declaración de clase derivada utiliza la palabra clave **class**.  La derivación se considera pública si la declaración de clase derivada utiliza la palabra clave `struct`.  Por ejemplo, el código siguiente:  
  
```  
class Derived : Base  
...  
```  
  
 equivale a:  
  
```  
class Derived : private Base  
...  
```  
  
 De igual forma, el código siguiente:  
  
```  
struct Derived : Base  
...  
```  
  
 equivale a:  
  
```  
struct Derived : public Base  
...  
```  
  
 Tenga en cuenta que los miembros que se declaran con acceso privado no tienen acceso a las funciones ni a las clases derivadas a menos que esas funciones o clases se declaren mediante la declaración `friend` en la clase base.  
  
 Un tipo **union** no puede tener una clase base.  
  
> [!NOTE]
>  Al especificar una clase base privada, es aconsejable usar explícitamente la palabra clave `private` para que los usuarios de la clase derivada sepan cómo es el acceso a los miembros.  
  
## Control de acceso y miembros estáticos  
 Cuando se especifica una clase base como `private`, solo afecta a los miembros no estáticos.  Los miembros estáticos públicos siguen siendo accesibles en las clases derivadas.  Sin embargo, el acceso a los miembros de la clase base mediante el uso de punteros, referencias u objetos puede requerir una conversión en la que se aplica de nuevo el control de acceso de tiempo.  Considere el ejemplo siguiente:  
  
```  
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
  
 En el código anterior, el control de acceso prohíbe la conversión de un puntero a `Derived2` en un puntero a `Base`.  El puntero **this** es implícitamente de tipo `Derived2 *`.  Para seleccionar la función `CountOf`, **this** se debe convertir al tipo `Base *`.  Este tipo de conversión no está permitido porque `Base` es una clase base indirecta privada a `Derived2`.  La conversión a un tipo de clase base privada solo es aceptable para punteros a clases derivadas inmediatas.  Por lo tanto, los punteros de tipo `Derived1 *` pueden convertirse al tipo `Base *`.  
  
 Observe que la llamada explícita a la función `CountOf`, sin utilizar un puntero, una referencia o un objeto para seleccionarla, no implica ninguna conversión.  Por lo tanto, se permite la llamada.  
  
 Los miembros y objetos friend de una clase derivada, `T`, pueden convertir un puntero a `T` en un puntero a una clase base directa privada de `T`.  
  
## Acceso a funciones virtuales  
 El control de acceso que se aplica a las funciones [virtual](../cpp/virtual-cpp.md) viene determinado por el tipo que se usa para realizar la llamada a función.  El reemplazo de las declaraciones de la función no afecta al control de acceso para un tipo determinado.  Por ejemplo:  
  
```  
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
  
 En el ejemplo anterior, al llamar a la función virtual `GetState` mediante un puntero al tipo `VFuncBase`, se llama a `VFuncDerived::GetState`, y `GetState` se trata como public.  Sin embargo, la llamada a `GetState` mediante un puntero al tipo `VFuncDerived` se considera una infracción del control de acceso, porque `GetState` se declara private en la clase `VFuncDerived`.  
  
> [!CAUTION]
>  La función virtual `GetState` se puede llamar mediante un puntero a la clase base `VFuncBase`.  Esto no significa que la función llamada sea la versión de la clase base de esa función.  
  
## Control de acceso con herencia múltiple  
 En los entramados de herencia múltiple con clases base virtuales, se puede acceder a un nombre determinado a través de más de una ruta.  Dado que se puede aplicar un control de acceso diferente en estas rutas de acceso diferentes, el compilador elige la ruta de acceso que proporciona el mejor acceso.  Vea la ilustración siguiente.  
  
 ![Acceso mediante rutas de acceso de un gráfico de herencia](../cpp/media/vc38v91.png "vc38V91")  
Acceso a través de las rutas de acceso de un gráfico de herencia  
  
 En la ilustración, se accede a un nombre declarado en la clase `VBase` siempre a través de la clase `RightPath`.  La ruta de acceso derecha es más accesible porque `RightPath` declara `VBase` como clase base pública, mientras que `LeftPath` declara `VBase` como private.  
  
## Vea también  
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)