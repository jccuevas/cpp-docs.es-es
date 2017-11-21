---
title: Error del compilador C2990 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2990
dev_langs: C++
helpviewer_keywords: C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9a2433bec7992c73fb7e9b7f358e89b7e75da384
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2990"></a>Error del compilador C2990
'clase': tipo de clase no como ya está declarado como tipo de clase  
  
 El no genérica o clase de plantilla vuelve a definir una clase genérica o de plantilla. Compruebe los archivos de encabezado de conflictos.  
  
 El ejemplo siguiente genera el error C2990:  
  
```  
// C2990.cpp  
// compile with: /c  
template <class T>  
class C{};  
class C{};   // C2990  
```  
  
 El error C2990 también puede producirse al usar genéricos:  
  
```  
// C2990b.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct GC;  
  
ref struct GC {};   // C2990  
```  
  
 El error C2990 también puede producirse debido a un cambio importante en el compilador de Visual C++ para Visual C++ 2005; el compilador requiere ahora que varias declaraciones para el mismo tipo sea idéntica con respecto a la especificación de la plantilla.  
  
 El ejemplo siguiente genera el error C2990:  
  
```  
// C2990c.cpp  
// compile with: /c  
template<class T>  
class A;  
  
template<class T>  
struct A2 {  
   friend class A;   // C2990  
};  
  
// OK  
template<class T>  
struct B {  
   template<class T>  
   friend class A;  
};  
```