---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: 5849a24d7b5d3d4f4a6d24d8cab3dd32f9d1de14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490771"
---
# <a name="finally"></a>finally

Además `try` y `catch` control admite de excepciones de CLR, en un `finally` cláusula. La semántica es idéntica a la `__finally` bloque de excepciones estructurado (SEH). Un `__finally` bloque puede seguir un `try` o `catch` bloque.

## <a name="remarks"></a>Comentarios

El propósito de la `finally` bloque es limpiar los recursos que queden después de que se produjo la excepción. Tenga en cuenta que el `finally` bloque se ejecuta siempre, incluso si se produjo ninguna excepción. El `catch` bloque se ejecuta solo si se produce una excepción administrada en el asociado `try` bloque.

`finally` es una palabra clave contextual; consulte [palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md) para obtener más información.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un sencillo `finally` bloque:

```
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

## <a name="see-also"></a>Vea también

[Control de excepciones](../windows/exception-handling-cpp-component-extensions.md)