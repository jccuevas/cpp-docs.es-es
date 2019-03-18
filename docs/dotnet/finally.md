---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: cb2bbdb36a102c7ef8974a9ac210473f2306f5d6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746778"
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
