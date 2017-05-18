---
title: C3772 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3772
dev_langs:
- C++
helpviewer_keywords:
- C3772
ms.assetid: 63e938d4-088d-41cc-a562-5881a05b5710
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: 7bf4fc0d7e80d2bd77343ee43c31dc74b93c97de
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3772"></a>Error del compilador C3772
"name": declaración de plantilla friend no válida  
  
No es válida para declarar un elemento friend de una especialización de plantilla de clase. No puede declarar una especialización parcial o explícita de una plantilla de clase y declarar en la misma instrucción un elemento friend de esa especialización. El marcador *name* identifica la declaración no válida.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   No declare un elemento friend de una especialización de plantilla de clase.  
  
-   Si es adecuado para la aplicación, declare un elemento friend de la plantilla de clase o declare un elemento friend de una especialización parcial o explícita determinada.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se produce un error, porque se declara un elemento friend de una especialización parcial de una plantilla de clase.  
  
```cpp  
// c3772.cpp  
// compile with: /c  
  
// A class template.  
    template<class T> class A {};  
  
// A partial specialization of the class template.  
    template<class T> class A<T*> {};  
  
// An explicit specialization.  
    template<> class A<char>;  
  
class X {  
// Invalid declaration of a friend of a partial specialization.  
    template<class T> friend class A<T*>; // C3772  
  
// Instead, if it is appropriate for your application, declare a   
// friend of the class template. Consequently, all specializations   
// of the class template are friends:  
//    template<class T> friend class A;  
// Or declare a friend of a particular partial specialization:  
//    friend class A<int*>;  
// Or declare a friend of a particular explicit specialization:  
//    friend class A<char>;  
};  
```  
  
## <a name="see-also"></a>Vea también  
[Plantillas](../../cpp/templates-cpp.md)   
[Especialización de plantilla](../../cpp/template-specialization-cpp.md)   

