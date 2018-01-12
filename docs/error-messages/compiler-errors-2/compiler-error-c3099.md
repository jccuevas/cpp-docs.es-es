---
title: Error del compilador C3099 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3099
dev_langs: C++
helpviewer_keywords: C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a644a27c834efcd3c3857241927a6e618f600d0c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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