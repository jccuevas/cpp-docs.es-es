---
title: Error del compilador C3813 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3813
dev_langs:
- C++
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e947b281c90c4d2ace83971f1de972c29bde72ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273112"
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