---
title: restringir | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: restrict_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9176336ac96d88a34d758fd55c09a3a938f371fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="restrict"></a>restrict
**Específicos de Microsoft**  
  
 Se aplica a una declaración de función o a una definición que devuelve un tipo de puntero e indica al compilador que la función devuelve un objeto que no tendrá alias de ningún otro puntero.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
__declspec(restrict) return_type f();  
```  
  
## <a name="remarks"></a>Comentarios  
 El compilador propagará `__declspec(restrict)`. Por ejemplo, la función `malloc` de CRT se decora con `__declspec(restrict)` y, por consiguiente, también se implica que los punteros inicializados en ubicaciones de memoria con `malloc` no tienen alias.  
  
 El compilador no comprueba que el puntero no tiene alias realmente. Es responsabilidad del programador garantizar que el programa no utilice un alias de un puntero marcado con el modificador `restrict __declspec`.  
  
 Para una semántica similar en las variables, consulte [__restrict](../cpp/extension-restrict.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [noalias](../cpp/noalias.md) para obtener un ejemplo de uso `restrict`.  
  
 Para obtener información acerca de la palabra clave de restringir que forma parte de C++ AMP, consulte [restrict (C++ AMP)](../cpp/restrict-cpp-amp.md).  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)