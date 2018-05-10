---
title: runtime_error (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- stdexcept/std::runtime_error
dev_langs:
- C++
helpviewer_keywords:
- runtime_error class
ms.assetid: 4d0227bf-847b-45a2-a320-2351ebf98368
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d21fcc072608d7e0aa1f2f76c1a1b070d7a442eb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="runtimeerror-class"></a>runtime_error (Clase)

Clase que actúa como la clase base para todas las excepciones iniciadas para informar de errores supuestamente detectables únicamente cuando se ejecute el programa.

## <a name="syntax"></a>Sintaxis

```cpp
class runtime_error : public exception {
public:
    explicit runtime_error(const string& message);

    explicit runtime_error(const char *message);

};
```

## <a name="remarks"></a>Comentarios

El valor devuelto por [exception (Clase)](../standard-library/exception-class.md)es una copia de **message**`.`[data](../standard-library/basic-string-class.md#data).

## <a name="example"></a>Ejemplo

```cpp
// runtime_error.cpp
// compile with: /EHsc /GR
#include <iostream>

using namespace std;

int main( )
{
// runtime_error
   try
   {
      locale loc( "test" );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
\* Output:
Caught bad locale name
Type class std::runtime_error
*\
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<stdexcept>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[exception (Clase)](../standard-library/exception-class.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
