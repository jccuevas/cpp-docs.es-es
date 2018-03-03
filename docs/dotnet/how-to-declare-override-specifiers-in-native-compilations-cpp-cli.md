---
title: "Cómo: declarar especificadores de invalidación (C++ / CLI) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- override specifiers in native compilation, overriding
ms.assetid: d0551836-9ac7-41eb-a6e9-a4b3ef60767d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0f50e500cf25a18e86e107e22d58e6446d03379d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-declare-override-specifiers-in-native-compilations-ccli"></a>Cómo: Declarar especificadores de invalidación en las compilaciones nativas (C++/CLI)
[sellado](../windows/sealed-cpp-component-extensions.md), [abstracta](../windows/abstract-cpp-component-extensions.md), y [invalidar](../windows/override-cpp-component-extensions.md) están disponibles en las compilaciones que no utilizan **/ZW** o [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
> [!NOTE]
>  El ISO C ++ 11 estándar lenguaje tiene la [invalidar](../cpp/override-specifier.md) identificador y el [final](../cpp/final-specifier.md) identificador y ambos se admiten en el uso de Visual Studio `final` en lugar de `sealed` en el código que está diseñado para se compila como solo nativo.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente se muestra que `sealed` es válida en compilaciones nativas.  
  
### <a name="code"></a>Código  
  
```cpp  
// sealed_native_keyword.cpp  
#include <stdio.h>  
__interface I1 {  
   virtual void f();  
   virtual void g();  
};  
  
class X : public I1 {  
public:  
   virtual void g() sealed {}  
};  
  
class Y : public X {  
public:  
  
   // the following override generates a compiler error  
   virtual void g() {}   // C3248 X::g is sealed!  
};  
```  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente se muestra que `override` es válida en compilaciones nativas.  
  
### <a name="code"></a>Código  
  
```cpp  
// override_native_keyword.cpp  
#include <stdio.h>  
__interface I1 {  
   virtual void f();  
};  
  
class X : public I1 {  
public:  
   virtual void f() override {}   // OK  
   virtual void g() override {}   // C3668 I1::g does not exist  
};  
```  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 Este ejemplo muestra que `abstract` es válida en compilaciones nativas.  
  
### <a name="code"></a>Código  
  
```cpp  
// abstract_native_keyword.cpp  
class X abstract {};  
  
int main() {  
   X * MyX = new X;   // C3622 cannot instantiate abstract class  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Especificadores de invalidación](../windows/override-specifiers-cpp-component-extensions.md)