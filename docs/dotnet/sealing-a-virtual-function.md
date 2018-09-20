---
title: Sellar una función Virtual | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
- derived classes, virtual functions
- virtual functions, sealing
- __sealed keyword
ms.assetid: 0e9fae03-6425-4512-9a24-8ccb6dc8a0d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 69ac614d55ade10b94621da2a3eb1c43d25ebaf5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385188"
---
# <a name="sealing-a-virtual-function"></a>Sellar una función virtual

La sintaxis para sellar una función virtual ha cambiado de extensiones administradas para C++ a Visual C++.

El `__sealed` palabra clave se usa en extensiones administradas para modificar un tipo de referencia, no se permiten derivación posterior de él (consulte [declaración de un tipo de clase administrada](../dotnet/declaration-of-a-managed-class-type.md)), o para modificar una función virtual, no se permiten reemplazo del método en una clase derivada posterior. Por ejemplo:

```
__gc class base { public: virtual void f(); };
__gc class derived : public base {
public:
   __sealed void f();
};
```

En este ejemplo, `derived::f()` invalida la `base::f()` instancia según la coincidencia exacta del prototipo de función. El `__sealed` palabra clave indica que una clase subsiguientes se hereda de la clase derivada no puede proporcionar un reemplazo de `derived::f()`.

En la nueva sintaxis, `sealed` se coloca después de la firma en lugar de que pueda aparecer en cualquier lugar antes del prototipo de función real, tal como se permitían anteriormente. Además, el uso de `sealed` requiere el uso explícito de la `virtual` también la palabra clave. Es decir, la traducción adecuada de `derived`, anteriormente, es como sigue:

```
ref class derived: public base {
public:
   virtual void f() override sealed;
};
```

La ausencia de la `virtual` palabra clave en esta instancia se produce un error. En la nueva sintaxis, la palabra clave contextual `abstract` puede usarse en lugar de la `=0` para indicar una función virtual pura. Esto no estaba admitido en extensiones administradas. Por ejemplo:

```
__gc class base { public: virtual void f()=0; };
```

puede volver a escribirse como

```
ref class base { public: virtual void f() abstract; };
```

## <a name="see-also"></a>Vea también

[Declaraciones de miembros en una clase o interfaz (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[sealed](../windows/sealed-cpp-component-extensions.md)