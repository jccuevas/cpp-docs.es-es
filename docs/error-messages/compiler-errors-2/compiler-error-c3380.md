---
title: Error del compilador C3380 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3380
dev_langs:
- C++
helpviewer_keywords:
- C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: b06f57795cea7dda7b3ba2797f7c57026a9acf60
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3380"></a>Error del compilador C3380
'class': especificador de acceso de ensamblado no válido; solo se permiten 'public' o 'private'  
  
 Cuando se aplican a una clase o estructura administrada, las palabras clave [public](../../cpp/public-cpp.md) y [private](../../cpp/private-cpp.md) indican si la clase se expondrá a través de los metadatos del ensamblado. Solo `public` o `private` pueden aplicarse a una clase en un programa compilado con [/clr](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 El `ref` y `value` palabras clave, cuando se usa con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), indican que una clase es administrada (vea [clases y Structs](../../windows/classes-and-structs-cpp-component-extensions.md)).  
  
 El ejemplo siguiente genera la advertencia C3380:  
  
```  
// C3380_2.cpp  
// compile with: /clr  
protected ref class A {   // C3380  
// try the following line instead  
// ref class A {  
public:  
   static int i = 9;  
};  
  
int main() {  
   A^ myA = gcnew A;  
   System::Console::WriteLine(myA->i);  
}  
```  

