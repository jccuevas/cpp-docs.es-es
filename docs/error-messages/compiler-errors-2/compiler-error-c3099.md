---
title: Error del compilador C3099 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3099
dev_langs:
- C++
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27059beb1cb587b9060da8c5cc5702ea966422f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33249760"
---
# <a name="compiler-error-c3099"></a>Error del compilador C3099
'keyword': use [System::AttributeUsageAttribute] para atributos administrados; use [Windows::Foundation::Metadata::AttributeUsageAttribute] para atributos WinRT  
  
 Use <xref:System.AttributeUsageAttribute> para declarar **/CLR** atributos. Use `Windows::Foundation::Metadata::AttributeUsageAttribute` para declarar atributos de Windows Runtime.  
  
 Para obtener más información sobre atributos/CLR, vea [atributos definidos por el usuario](../../windows/user-defined-attributes-cpp-component-extensions.md). Para atributos admitidos en Windows Runtime, consulte [espacio de nombres Windows.Foundation.Metadata](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.aspx)  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C3099 y muestra cómo corregirlo:  
  
```  
// C3099.cpp  
// compile with: /clr /c  
using namespace System;  
[usage(10)]   // C3099  
// try the following line instead  
// [AttributeUsageAttribute(AttributeTargets::All)]  
ref class A : Attribute {};  
```