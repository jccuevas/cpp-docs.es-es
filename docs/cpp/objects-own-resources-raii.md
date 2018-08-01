---
title: Objetos de recursos propios (RAII) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f86b484e-5a27-4c3b-a92a-dfaa5dd6d93a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 265eccc4c1a9f51a03e5a84433a9f7e9cc6d6a92
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402141"
---
# <a name="objects-own-resources-raii"></a>Recursos propios de los objetos (RAII)
Asegúrese de que los recursos propios objetos. Este principio es que también se denomina "resource acquisition is initialization" o "RAII."  
  
## <a name="example"></a>Ejemplo  
 Pasar todos los objetos "nuevo" como un argumento de constructor a otro objeto con nombre que pertenece (casi siempre unique_ptr).  
  
```cpp  
void f() {  
    unique_ptr<widget> p( new widget() );  
    my_class x( new widget() );  
    // ...  
} // automatic destruction and deallocation for both widget objects  
  // automatic exception safety, as if "finally { p->dispose(); x.w.dispose(); }"  
```  
  
 Pasar siempre inmediatamente cualquier recurso nuevo a otro objeto que lo posee.  
  
```cpp  
void g() {  
    other_class y( OpenFile() );  
    // ...  
} // automatic closing and release for file resource  
  // automatic exception safety, as if "finally { y.file.dispose(); }"  
```  
  
## <a name="see-also"></a>Vea también  
 [Bienvenido nuevamente a C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)