---
title: override (especificador)
ms.date: 11/04/2016
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
ms.openlocfilehash: 82837ae34ab786e607df54038493b14350574a15
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188485"
---
# <a name="override-specifier"></a>override (especificador)

Puede usar la palabra clave **override** para designar las funciones miembro que invalidan una función virtual en una clase base.

## <a name="syntax"></a>Sintaxis

```
function-declaration override;
```

## <a name="remarks"></a>Observaciones

la **invalidación** es contextual y tiene un significado especial solo cuando se utiliza después de una declaración de función miembro; de lo contrario, no es una palabra clave reservada.

## <a name="example"></a>Ejemplo

Use **invalidaciones** para ayudar a evitar el comportamiento inadvertido de herencia en el código. En el ejemplo siguiente se muestra dónde, sin usar **override**, es posible que el comportamiento de la función miembro de la clase derivada no se haya diseñado. El compilador no genera ningún error para este código.

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA(); // ok, works as intended

    virtual void funcB(); // DerivedClass::funcB() is non-const, so it does not
                          // override BaseClass::funcB() const and it is a new member function

    virtual void funcC(double = 0.0); // DerivedClass::funcC(double) has a different
                                      // parameter type than BaseClass::funcC(int), so
                                      // DerivedClass::funcC(double) is a new member function
};
```

Cuando se utiliza **override**, el compilador genera errores en lugar de crear de forma silenciosa nuevas funciones miembro.

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA() override; // ok

    virtual void funcB() override; // compiler error: DerivedClass::funcB() does not
                                   // override BaseClass::funcB() const

    virtual void funcC( double = 0.0 ) override; // compiler error:
                                                 // DerivedClass::funcC(double) does not
                                                 // override BaseClass::funcC(int)

    void funcD() override; // compiler error: DerivedClass::funcD() does not
                           // override the non-virtual BaseClass::funcD()
};
```

Para especificar que las funciones no se pueden invalidar y que las clases no se pueden heredar, use la palabra clave [final](../cpp/final-specifier.md) .

## <a name="see-also"></a>Consulte también

[Especificador final](../cpp/final-specifier.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
