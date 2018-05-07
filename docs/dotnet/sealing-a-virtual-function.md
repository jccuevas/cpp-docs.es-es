---
title: Sellar una función Virtual | Documentos de Microsoft
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
ms.openlocfilehash: c85f4775025d3661fdfbf8967b310fb733f452b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="sealing-a-virtual-function"></a>Sellar una función virtual
La sintaxis para sellar una función virtual ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 El `__sealed` palabra clave se usa en extensiones administradas para modificar un tipo de referencia, no se permiten derivación posterior de él (vea [declaración de un tipo de clase administrada](../dotnet/declaration-of-a-managed-class-type.md)), o para modificar una función virtual, no se permiten reemplazo del método en una clase derivada posterior. Por ejemplo:  
  
```  
__gc class base { public: virtual void f(); };  
__gc class derived : public base {  
public:  
   __sealed void f();  
};  
```  
  
 En este ejemplo, `derived::f()` invalida la `base::f()` instancia a partir de la coincidencia exacta del prototipo de función. El `__sealed` palabra clave indica que una clase subsiguientes se hereda de la clase derivada no puede proporcionar una invalidación de `derived::f()`.  
  
 En la nueva sintaxis, `sealed` se coloca después de la firma en lugar de que se puedan aparecer en cualquier lugar antes del prototipo de función real, tal y como se permitían anteriormente. Además, el uso de `sealed` requiere un uso explícito de la `virtual` también la palabra clave. Es decir, la traducción adecuada de `derived`anteriormente, es como sigue:  
  
```  
ref class derived: public base {  
public:  
   virtual void f() override sealed;  
};  
```  
  
 La ausencia de la `virtual` palabra clave en esta instancia produce un error. En la nueva sintaxis, la palabra clave contextual `abstract` puede usarse en lugar de la `=0` para indicar una función virtual pura. Esto no estaba admitido en extensiones administradas. Por ejemplo:  
  
```  
__gc class base { public: virtual void f()=0; };  
```  
  
 se puede reescribir como  
  
```  
ref class base { public: virtual void f() abstract; };  
```  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones de miembros en una clase o interfaz (C++ / CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [sealed](../windows/sealed-cpp-component-extensions.md)