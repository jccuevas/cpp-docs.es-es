---
title: nothrow (C++)
ms.date: 01/03/2018
f1_keywords:
- nothrow_cpp
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
ms.openlocfilehash: 88041b374cc48ac31c8990aa7f867ba25b33e1d7
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345880"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Específicos de Microsoft**

Un **__declspec** atributo extendido que se puede usar en la declaración de funciones.

## <a name="syntax"></a>Sintaxis

> *return-type* __declspec(nothrow) [*call-convention*] *function-name* ([*argument-list*])

## <a name="remarks"></a>Comentarios

Se recomienda que todo el código nuevo use los [noexcept](noexcept-cpp.md) operador lugar `__declspec(nothrow)`.

Este atributo indica al compilador que la función declarada y las funciones a las que llama nunca iniciarán una excepción. Sin embargo, no aplica la directiva. En otras palabras, nunca hace [std:: Terminate](../standard-library/exception-functions.md#terminate) que se invocará, a diferencia de `noexcept`, o en **std: c ++ 17** (Visual Studio 2017 versión 15.5 y versiones posterior), de modo `throw()`.

Con el modelo de control asincrónico de excepciones, que ahora es el predeterminado, el compilador puede eliminar los mecanismos de seguimiento de la duración de algunos objetos que no se pueden desenredar en esa función, y reducir significativamente el tamaño del código. Dado que la directiva de preprocesador siguiente, las tres declaraciones de función siguientes son equivalentes en **/std: c ++ 14** modo:

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

En **/std: c ++ 17** modo, `throw()` no es equivalente a los demás que utilizan `__declspec(nothrow)` porque hace que `std::terminate` que se invocará si se produce una excepción de la función.

El `void __stdcall f3() throw();` declaración usa la sintaxis definida por el estándar de C++. En C ++ 17 el `throw()` palabra clave ha quedado en desuso.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)<br/>
[noexcept](noexcept-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)