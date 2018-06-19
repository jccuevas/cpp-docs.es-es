---
title: invalidación (extensiones de componentes de C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6818256aafc64702e5423a5560c251e6d46750fa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878884"
---
# <a name="override--c-component-extensions"></a>override (Extensiones de componentes de C++)
La palabra clave contextual `override` indica que un miembro de un tipo invalida un tipo base o un miembro de interfaz base.  
  
## <a name="remarks"></a>Comentarios  
 El `override` palabra clave es válida cuando se compila para destinos nativos (opción del compilador predeterminada), los destinos de Windows Runtime (**/ZW** opción del compilador), o los destinos de common language runtime (**/CLR** compilador opción).  
  
 Para obtener más información acerca de los especificadores de invalidación, vea [especificador de reemplazo](../cpp/override-specifier.md) y [especificadores de invalidación y compilaciones nativas](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
 Para obtener más información sobre las palabras clave contextuales, vea [palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
## <a name="examples"></a>Ejemplos  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se muestra que `override` también se puede usar en compilaciones nativas.  
  
```cpp#  
// override_keyword_1.cpp  
// compile with: /c  
struct I1 {  
   virtual void f();  
};  
  
struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se muestra que `override` se puede usar en compilaciones de Windows en tiempo de ejecución.  
  
```cpp#  
// override_keyword_2.cpp  
// compile with: /ZW /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Requisitos**  
  
 Opción del compilador: **/ZW**  
  
 **Ejemplo**  
  
 En el ejemplo de código siguiente se muestra que `override` se puede usar en compilaciones de Common Language Runtime.  
  
```cpp#  
// override_keyword_3.cpp  
// compile with: /clr /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **Requisitos**  
  
 Opción del compilador: **/clr**  
  
## <a name="see-also"></a>Vea también  
 [Especificador de reemplazo](../cpp/override-specifier.md)   
 [Especificadores de invalidación](../windows/override-specifiers-cpp-component-extensions.md)