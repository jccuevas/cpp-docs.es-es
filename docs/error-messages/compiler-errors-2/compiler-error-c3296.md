---
title: Error del compilador C3296 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3296
dev_langs:
- C++
helpviewer_keywords:
- C3296
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 85b4f80a9f257fa5e5d9ed8701a6ee7cfdf68cfd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3296"></a>Error del compilador C3296
'propiedad': ya existe una propiedad con este nombre.  
  
 El compilador encontró más de una propiedad con el mismo nombre. Cada propiedad de un tipo debe tener un nombre único.  
  
 Para obtener más información, consulta [property](../../windows/property-cpp-component-extensions.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3296.  
  
```  
// C3296.cpp  
// compile with: /clr /c  
using namespace System;  
  
ref class R {  
public:  
   property int MyProp[int] { int get(int); }  
  
   property String^ MyProp[int] { void set(int, String^); }   // C3296  
};  
```