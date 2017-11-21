---
title: Error del compilador C3670 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3670
dev_langs: C++
helpviewer_keywords: C3670
ms.assetid: d0fa9c6e-8f90-48c7-9066-31b4fa5942eb
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 773ee85df3e19245b665521be8d65055ffe3bf17
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3670"></a>Error del compilador C3670
'override': no se puede invalidar el método de clase base inaccesible 'método'  
  
 Una invalidación sólo puede tener lugar en una función cuyo nivel de acceso hace que esté disponible en un tipo derivado. Para obtener más información, consulte [reemplazos explícitos](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera C3670:  
  
```  
// C3670.cpp  
// compile with: /clr /c  
public ref class C {  
// Uncomment the following line to resolve.  
// public:  
   virtual void g() { }  
};  
  
public ref class D : public C {  
public:  
   virtual void f() new sealed = C::g {};   // C3670  
};  
```