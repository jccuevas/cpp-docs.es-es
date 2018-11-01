---
title: bad_typeid (Excepción)
ms.date: 11/04/2016
f1_keywords:
- bad_typeid
- bad_typeid_cpp
helpviewer_keywords:
- bad_typeid exception
- exceptions [C++], bad_typeid
ms.assetid: 5963ed58-4ede-4597-957d-f7bbd06299c2
ms.openlocfilehash: 5d53d2e25b56aa78edaebcd4be0e468993ebb8f8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514041"
---
# <a name="badtypeid-exception"></a>bad_typeid (Excepción)

El **bad_typeid** excepción la [operador typeid](../cpp/typeid-operator.md) cuando el operando para **typeid** es un puntero NULL.

## <a name="syntax"></a>Sintaxis

```
catch (bad_typeid)
   statement
```

## <a name="remarks"></a>Comentarios

La interfaz para **bad_typeid** es:

```cpp
class bad_typeid : public exception
{
public:
   bad_typeid(const char * _Message = "bad typeid");
   bad_typeid(const bad_typeid &);
   virtual ~bad_typeid();
};
```

El ejemplo siguiente se muestra el **typeid** operador producir una **bad_typeid** excepción.

```cpp
// expre_bad_typeid.cpp
// compile with: /EHsc /GR
#include <typeinfo.h>
#include <iostream>

class A{
public:
   // object for class needs vtable
   // for RTTI
   virtual ~A();
};

using namespace std;
int main() {
A* a = NULL;

try {
   cout << typeid(*a).name() << endl;  // Error condition
   }
catch (bad_typeid){
   cout << "Object is NULL" << endl;
   }
}
```

## <a name="output"></a>Salida

```Output
Object is NULL
```

## <a name="see-also"></a>Vea también

[Información de tipos en tiempo de ejecución](../cpp/run-time-type-information.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)