---
title: underflow_error (Clase)
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::underflow_error
helpviewer_keywords:
- underflow_error class
ms.assetid: d632f1f9-9c6c-4954-b96b-03041bfab22d
ms.openlocfilehash: 41e3c8606cb8c6c90a84927f01eb953be138534a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454992"
---
# <a name="underflowerror-class"></a>underflow_error (Clase)

Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un subdesbordamiento aritmético.

## <a name="syntax"></a>Sintaxis

```cpp
class underflow_error : public runtime_error {
public:
    explicit underflow_error(const string& message);

    explicit underflow_error(const char *message);

};
```

## <a name="remarks"></a>Comentarios

El valor devuelto por [what](../standard-library/exception-class.md) es una copia de **message**`.`[data](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Ejemplo

```cpp
// underflow_error.cpp
// compile with: /EHsc /GR
#include <iostream>

using namespace std;

int main( )
{
   try
   {
      throw underflow_error( "The number's a bit small, captain!" );
   }
   catch ( exception &e ) {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught: The number's a bit small, captain!
Type: class std::underflow_error
*/
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<stdexcept>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[runtime_error (Clase)](../standard-library/runtime-error-class.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
