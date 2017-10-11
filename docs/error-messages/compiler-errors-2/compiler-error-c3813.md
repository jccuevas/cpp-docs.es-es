---
title: Error del compilador C3813 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3813
dev_langs:
- C++
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: cabe753691b3d72ede25f0c25404d73fb63ceba8
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3813"></a>Error del compilador C3813
una declaración de propiedad solo puede aparecer en la definición de un tipo WinRT o administrado  
  
A [propiedad](../../dotnet/how-to-use-properties-in-cpp-cli.md) solo puede declararse dentro de Windows Runtime o administrado tipo. Los tipos nativos no admiten la palabra clave `property`.  
  
## <a name="example"></a>Ejemplo  
En el ejemplo siguiente se genera el error C3813 y se muestra cómo corregirlo:  
  
```cpp  
// C3813.cpp  
// compile by using: cl /c /clr C3813.cpp  
class A  
{  
   property int Int; // C3813  
};  
  
ref class B  
{  
   property int Int; // OK - declared within managed type  
};  
```
