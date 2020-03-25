---
title: nothrow (C++)
ms.date: 01/03/2018
f1_keywords:
- nothrow_cpp
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
ms.openlocfilehash: 8164f47190267627bdaf7c7ee2f03f22f65c8f50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161066"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Específicos de Microsoft**

**__Declspec** atributo extendido que se puede utilizar en la declaración de funciones.

## <a name="syntax"></a>Sintaxis

> __declspec de *tipo de valor devuelto* (nothrow) [*Convención de llamada*] *nombre de función* ([*lista de argumentos*])

## <a name="remarks"></a>Observaciones

Se recomienda que todo el código nuevo use el operador [noexception](noexcept-cpp.md) en lugar de `__declspec(nothrow)`.

Este atributo indica al compilador que la función declarada y las funciones a las que llama nunca iniciarán una excepción. Sin embargo, no aplica la Directiva. En otras palabras, nunca hace que se invoque [STD:: Terminate](../standard-library/exception-functions.md#terminate) , a diferencia de `noexcept`, o en el modo **STD: C++ 17** (Visual Studio 2017 versión 15,5 y versiones posteriores), `throw()`.

Con el modelo de control asincrónico de excepciones, que ahora es el predeterminado, el compilador puede eliminar los mecanismos de seguimiento de la duración de algunos objetos que no se pueden desenredar en esa función, y reducir significativamente el tamaño del código. Dada la siguiente directiva de preprocesador, las tres declaraciones de función siguientes son equivalentes en el modo **/STD: c++ 14** :

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

En el modo **/STD: c++ 17** , `throw()` no es equivalente a los demás que usan `__declspec(nothrow)` porque hace que `std::terminate` se invoque si se produce una excepción desde la función.

La declaración `void __stdcall f3() throw();` usa la sintaxis definida por el C++ estándar. En C++ 17, la palabra clave `throw()` quedó en desuso.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[__declspec](../cpp/declspec.md)<br/>
[noexcept](noexcept-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
