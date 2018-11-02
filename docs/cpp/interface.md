---
title: __interface
ms.date: 11/04/2016
f1_keywords:
- __interface_cpp
helpviewer_keywords:
- __interface keyword [C++]
ms.assetid: ca5d400b-d6d8-4ba2-89af-73f67e5ec056
ms.openlocfilehash: 33a3d45f65ab5adf798a2b0f6b11191e6f6a0213
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573554"
---
# <a name="interface"></a>__interface

**Específicos de Microsoft**

Una interfaz de Visual C++ se puede definir de la manera siguiente:

- Puede heredar de cero o más interfaces base.

- No puede heredar de una clase base.

- Solo puede contener métodos virtuales puros, públicos.

- No puede contener constructores, destructores ni operadores.

- No puede contener métodos estáticos.

- No puede contener miembros de datos; se permiten las propiedades.

## <a name="syntax"></a>Sintaxis

```
modifier __interface interface-name {interface-definition};
```

## <a name="remarks"></a>Comentarios

C++ [clase](../cpp/class-cpp.md) o [struct](../cpp/struct-cpp.md) podría implementarse con estas reglas, pero **__interface** aplica.

Por ejemplo, este es un ejemplo de definición de interfaz:

```cpp
__interface IMyInterface {
   HRESULT CommitX();
   HRESULT get_X(BSTR* pbstrName);
};
```

Para obtener información sobre interfaces administradas, vea [clase de interfaz](../windows/interface-class-cpp-component-extensions.md).

Observe que no tiene que indicar explícitamente que las funciones `CommitX` y `get_X` son virtuales puras. Una declaración equivalente para la primera función sería:

```cpp
virtual HRESULT CommitX() = 0;
```

**__interface** implica la [novtable](../cpp/novtable.md) **__declspec** modificador.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar propiedades declaradas en una interfaz.

```cpp
// deriv_interface.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <string.h>
#include <comdef.h>
#include <stdio.h>

[module(name="test")];

[ object, uuid("00000000-0000-0000-0000-000000000001"), library_block ]
__interface IFace {
   [ id(0) ] int int_data;
   [ id(5) ] BSTR bstr_data;
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002") ]
class MyClass : public IFace {
private:
    int m_i;
    BSTR m_bstr;

public:
    MyClass()
    {
        m_i = 0;
        m_bstr = 0;
    }

    ~MyClass()
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
    }

    int get_int_data()
    {
        return m_i;
    }

    void put_int_data(int _i)
    {
        m_i = _i;
    }

    BSTR get_bstr_data()
    {
        BSTR bstr = ::SysAllocString(m_bstr);
        return bstr;
    }

    void put_bstr_data(BSTR bstr)
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
        m_bstr = ::SysAllocString(bstr);
    }
};

int main()
{
    _bstr_t bstr("Testing");
    CoInitialize(NULL);
    CComObject<MyClass>* p;
    CComObject<MyClass>::CreateInstance(&p);
    p->int_data = 100;
    printf_s("p->int_data = %d\n", p->int_data);
    p->bstr_data = bstr;
    printf_s("bstr_data = %S\n", p->bstr_data);
}
```

```Output
p->int_data = 100
bstr_data = Testing
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Atributos de interfaz](../windows/attributes/interface-attributes.md)