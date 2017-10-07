---
title: restringir | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- restrict_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 2d1cdbff84966e7926b30ef70c40581cc3801a93
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

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
