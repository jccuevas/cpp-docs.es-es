---
title: range_error (Clase)
ms.date: 08/14/2018
f1_keywords:
- stdexcept/std::range_error
helpviewer_keywords:
- range_error class
ms.assetid: 8afb3e88-fc49-4213-b096-ed63d7aea37c
ms.openlocfilehash: 3e741604a3bb23fa8166023d115f79e7a288e2f7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458249"
---
# <a name="rangeerror-class"></a>range_error (Clase)

Clase que actúa como la clase base para todas las excepciones iniciadas para notificar un error de rango.

## <a name="syntax"></a>Sintaxis

```cpp
class range_error : public runtime_error {
public:
    explicit range_error(const string& message);
    explicit range_error(const char *message);
};
```

## <a name="remarks"></a>Comentarios

El valor devuelto por [lo que](../standard-library/exception-class.md) es una `message.data`copia de. Para obtener más información, consulte [basic_string::d ATA](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Ejemplo

```cpp
// range_error.cpp
// compile with: /EHsc /GR
#include <iostream>
using namespace std;
int main()
{
   try
   {
      throw range_error( "The range is in error!" );
   }
   catch (range_error &e)
   {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught: The range is in error!
Type: class std::range_error
*/
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<stdexcept>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[runtime_error (Clase)](../standard-library/runtime-error-class.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
