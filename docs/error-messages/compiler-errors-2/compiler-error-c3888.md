---
title: Error del compilador C3888 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3888
dev_langs:
- C++
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
caps.latest.revision: 3
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 4b85385c97f5873c1b370cd72f0866439263f787
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3888"></a>Error del compilador C3888
'name': C++/CLI no admite la expresión const asociada con este miembro de datos literal  
  
 El *nombre* miembro de datos que se declara con el [literal](../../windows/literal-cpp-component-extensions.md) palabra clave se inicializa con un valor que no es compatible con el compilador. El compilador solo admite los tipos de constante integral, de enumeración o de cadena. La causa probable del error **C3888** es que el miembro de datos se inicializa con una matriz de bytes.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Compruebe que el miembro de datos declarado literal es un tipo admitido.  
  
## <a name="see-also"></a>Vea también  
 [literal](../../windows/literal-cpp-component-extensions.md)
