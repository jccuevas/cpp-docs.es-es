---
title: noreturn | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: noreturn_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 91c6a7b38653a3bb0a86927ced602fd85ff29277
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="noreturn"></a>noreturn
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Este atributo `__declspec` indica al compilador que una función no devuelve resultados. En consecuencia, el compilador sabe que el código después de una llamada a un **__declspec (noreturn)** función no es accesible.  
  
 Si el compilador encuentra una función con una ruta de acceso de control que no devuelve un valor, genera una advertencia (C4715) o un mensaje de error (C2202). Si no se puede tener acceso a la ruta de acceso de control debido a una función que nunca devuelve resultados, puede usar **__declspec (noreturn)** para evitar esta advertencia o error.  
  
> [!NOTE]
>  Agregar **__declspec (noreturn)** a una función que se espera que devuelvan puede dar lugar a un comportamiento indefinido.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, la **else** cláusula no contiene una instrucción return.  Declarar `fatal` como **__declspec (noreturn)** evita un mensaje de advertencia o error.  
  
```  
// noreturn2.cpp  
__declspec(noreturn) extern void fatal () {}  
  
int main() {  
   if(1)  
     return 1;  
   else if(0)  
     return 0;  
   else  
     fatal();  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)