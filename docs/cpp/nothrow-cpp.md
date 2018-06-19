---
title: nothrow (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/03/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- nothrow_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69a706577cf112c3d8a3b7748f72679f7213936d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420662"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Específicos de Microsoft**

Atributo extendido `__declspec` que se puede usar en la declaración de funciones.

## <a name="syntax"></a>Sintaxis  
  
> *tipo de valor devuelto* __declspec (nothrow) [*convención de llamada*] *nombre de la función* ([*lista de argumentos*])

## <a name="remarks"></a>Comentarios

Se recomienda que todo el código nuevo use el [noexcept](noexcept-cpp.md) operador en lugar de `__declspec(nothrow)`.

Este atributo indica al compilador que la función declarada y las funciones a las que llama nunca iniciarán una excepción. Sin embargo, no aplica la directiva. En otras palabras, nunca hace [std:: Terminate](../standard-library/exception-functions.md#terminate) que se debe invocar, a diferencia de `noexcept`, o bien en **std:c ++ 17** (Visual Studio 2017 15.5 y versiones posteriores), el modo `throw()`.

Con el modelo de control asincrónico de excepciones, que ahora es el predeterminado, el compilador puede eliminar los mecanismos de seguimiento de la duración de algunos objetos que no se pueden desenredar en esa función, y reducir significativamente el tamaño del código. Dada la siguiente directiva de preprocesador, las tres declaraciones de función siguientes son equivalentes en **/std:c ++ 14** modo:

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

En **/std:c ++ 17** modo, `throw()` no es equivalente a los otros usuarios que utilicen `__declspec(nothrow)` porque hace que `std::terminate` que se invocará si se produce una excepción de la función.

El `void __stdcall f3() throw();` declaración usa la sintaxis definida por el estándar de C++. En C ++ 17 el `throw()` palabra clave está en desuso.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)  
[noexcept](noexcept-cpp.md)  
[Palabras clave](../cpp/keywords-cpp.md)  
