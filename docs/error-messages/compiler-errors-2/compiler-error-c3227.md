---
title: Error del compilador C3227 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3227
dev_langs:
- C++
helpviewer_keywords:
- C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 2f65791d709b5790144cd919bf06b61fd94da973
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3227"></a>Error del compilador C3227
'parámetro': no se puede usar 'palabra clave' para asignar un tipo genérico  
  
 Para crear una instancia de un tipo, se requiere un constructor adecuado. Sin embargo, el compilador no es capaz de garantizar que esté disponible un constructor adecuado.  
  
 Puede utilizar plantillas en lugar de los tipos genéricos para resolver este error, o puede usar varios métodos para crear una instancia del tipo.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3227.  
  
```  
// C3227.cpp  
// compile with: /clr /c  
generic<class T> interface class ICreate {  
   static T Create();  
};  
  
generic <class T>  
where T : ICreate<T>  
ref class C {  
   void f() {  
      T t = new T;   // C3227  
  
      // OK  
      T t2 = ICreate<T>::Create();  
      T t3 = safe_cast<T>( System::Activator::CreateInstance(T::typeid) );  
   }  
};  
```
