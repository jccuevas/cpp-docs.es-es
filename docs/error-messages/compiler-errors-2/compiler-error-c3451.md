---
title: Error del compilador C3451 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3451
dev_langs: C++
helpviewer_keywords: C3451
ms.assetid: a4897a69-e3e7-40bb-bb1c-598644904012
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cb68c546a9064801c68844039b7de077d5ee7c17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3451"></a>Error del compilador C3451
'atributo': no se puede aplicar el atributo no administrado a 'tipo'  
  
 Un atributo de C++ no se puede aplicar a un tipo CLR. Vea [referencia de atributos de C++](../../windows/cpp-attributes-reference.md) para obtener más información.  
  
 Para obtener más información, consulte [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
 Este error puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: el [uuid](../../windows/uuid-cpp-attributes.md) atributo ya no se permite en un atributo definido por el usuario mediante programación con CLR. Utilice <xref:System.Runtime.InteropServices.GuidAttribute> en su lugar.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3451.  
  
```  
// C3451.cpp  
// compile with: /clr /c  
using namespace System;  
[ attribute(AttributeTargets::All) ]  
public ref struct MyAttr {};  
  
[ MyAttr, helpstring("test") ]   // C3451  
// try the following line instead  
// [ MyAttr ]  
public ref struct ABC {};  
```