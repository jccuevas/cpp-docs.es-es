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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8789889ab0d9ebe93941a438c286ed718ac4721
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
