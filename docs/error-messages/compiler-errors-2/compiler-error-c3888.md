---
title: Error del compilador C3888 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
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
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 26e55c8a675ada3fd2e88976bc9d9a51cfa8b751
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3888"></a>Error del compilador C3888
'name': C++/CLI no admite la expresión const asociada con este miembro de datos literal  
  
 El miembro de datos *name* que se declara con la palabra clave [literal](../../windows/literal-cpp-component-extensions.md) se inicializa con un valor que no es compatible con el compilador. El compilador solo admite los tipos de constante integral, de enumeración o de cadena. La causa probable del error **C3888** es que el miembro de datos se inicializa con una matriz de bytes.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Compruebe que el miembro de datos declarado literal es un tipo admitido.  
  
## <a name="see-also"></a>Vea también  
 [literal](../../windows/literal-cpp-component-extensions.md)
