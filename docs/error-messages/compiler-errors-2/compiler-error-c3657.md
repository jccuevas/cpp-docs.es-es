---
title: Error del compilador C3657 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3657
dev_langs:
- C++
helpviewer_keywords:
- C3657
ms.assetid: 89a28a18-4c17-43a1-bda6-deb52c32d203
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c81a26ab0f0c47e620b3451c06f7bc6fdced7731
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3657"></a>Error del compilador C3657
los destructores no se pueden reemplazar de forma explícita o reemplazarse explícitamente  
  
 Los destructores o finalizadores no se puede invalidar explícitamente. Para obtener más información, consulte [reemplazos explícitos](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3657.  
  
```  
// C3657.cpp  
// compile with: /clr  
public ref struct I {  
   virtual ~I() { }  
   virtual void a();  
};  
  
public ref struct D : I {  
   virtual ~D() = I::~I {}   // C3657  
   virtual void a() = I::a {}   // OK  
};  
```