---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: 2574ba5a10bbf5eddc68d6e0265d5dfc99c6d8fc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545100"
---
# <a name="finally"></a>finally

Además de las cláusulas `try` y `catch`, el control de excepciones de CLR admite una cláusula `finally`. La semántica es idéntica a la del bloque `__finally` en el control de excepciones estructurado (SEH). Un bloque `__finally` puede seguir a un bloque de `try` o `catch`.

## <a name="remarks"></a>Observaciones

El propósito del bloque `finally` es limpiar los recursos que quedan después de que se produjera la excepción. Tenga en cuenta que el bloque `finally` siempre se ejecuta, incluso si no se produjo ninguna excepción. El bloque `catch` solo se ejecuta si se produce una excepción administrada dentro del bloque de `try` asociado.

`finally` es una palabra clave contextual; consulte [palabras clave contextuales](../extensions/context-sensitive-keywords-cpp-component-extensions.md) para obtener más información.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un bloque de `finally` simple:

```cpp
// keyword__finally.cpp
// compile with: /clr
using namespace System;

ref class MyException: public System::Exception{};

void ThrowMyException() {
   throw gcnew MyException;
}

int main() {
   try {
      ThrowMyException();
   }
   catch ( MyException^ e ) {
      Console::WriteLine(  "in catch" );
      Console::WriteLine( e->GetType() );
   }
   finally {
      Console::WriteLine(  "in finally" );
   }
}
```

```Output
in catch
MyException
in finally
```

## <a name="see-also"></a>Consulte también

[Control de excepciones](../extensions/exception-handling-cpp-component-extensions.md)
