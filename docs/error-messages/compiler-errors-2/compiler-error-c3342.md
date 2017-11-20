---
title: Error del compilador C3342 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3342
dev_langs: C++
helpviewer_keywords: C3342
ms.assetid: 5c6d784f-bebe-4f7e-8615-44ca6f78bfba
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4dc1432c6cf89f339094535f5b4ccbbd9af90aa9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3342"></a>Error del compilador C3342
'atributo': atributo ambiguo  
  
 El compilador encontró más de una definición de un atributo.  
  
 Un atributo se definió más de una vez.  
  
 Para obtener más información, consulte [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3342:  
  
```  
// C3342.cpp  
// compile with: /clr /c  
using namespace System;  
using namespace System::Reflection;  
  
[AttributeUsage(AttributeTargets::All)]  
public ref class XAttribute : public  Attribute {};  
  
[AttributeUsage(AttributeTargets::All)]  
public ref class X : public Attribute {};  
  
[X]   // C3342 could refer to X or XAttribute  
// try the following line instead  
// [XAttribute]  
public ref class Class4 {};  
```