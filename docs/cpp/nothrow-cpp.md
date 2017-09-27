---
title: nothrow (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- nothrow_cpp
- nothrow
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: c74490229e2ef54e7947f5e8fedda6057ecccb70
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="nothrow-c"></a>nothrow (C++)
**Específicos de Microsoft**  
  
 Atributo extendido `__declspec` que se puede usar en la declaración de funciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
return-type __declspec(nothrow) [call-convention] function-name ([argument-list])  
```  
  
## <a name="remarks"></a>Comentarios  
 Este atributo indica al compilador que la función declarada y las funciones a las que llama nunca iniciarán una excepción. Con el modelo de control asincrónico de excepciones, que ahora es el predeterminado, el compilador puede eliminar los mecanismos de seguimiento de la duración de algunos objetos que no se pueden desenredar en esa función, y reducir significativamente el tamaño del código. Dada la directiva de preprocesador siguiente, las tres declaraciones de función que se muestran a continuación son equivalentes:  
  
```  
#define WINAPI __declspec(nothrow) __stdcall   
  
void WINAPI f1();  
void __declspec(nothrow) __stdcall f2();  
void __stdcall f3() throw();  
```  
  
 Con `void __declspec(nothrow) __stdcall f2();`, tiene la ventaja de que puede usar una definición de API, como la que ilustra la instrucción `#define`, para especificar fácilmente `nothrow` en un conjunto de funciones. La tercera declaración`, void __stdcall f3() throw();`, es la sintaxis definida en el estándar de C++.  
  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)
