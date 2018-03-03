---
title: Instrucciones compuestas (bloques) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '}'
- '{'
dev_langs:
- C++
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 36dc3c25d5f8bbd37ebfaa3458c07f6948492817
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compound-statements-blocks"></a>Instrucciones compuestas (Bloques)
Una instrucción compuesta consta de cero o más instrucciones entre llaves (**{}**). Una instrucción compuesta se puede utilizar en cualquier lugar donde se espere una instrucción. Las instrucciones compuestas normalmente se denominan "bloques".  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
{ [ statement-list ] }  
```  
  
## <a name="remarks"></a>Comentarios  
 En el ejemplo siguiente se utiliza una instrucción compuesta como la *instrucción* forma parte de la **si** instrucción (consulte [if instrucción](../cpp/if-else-statement-cpp.md) para obtener más información acerca de la sintaxis):  
  
```  
if( Amount > 100 )  
{  
    cout << "Amount was too large to handle\n";  
    Alert();  
}  
else  
{
    Balance -= Amount;  
}
```  
  
> [!NOTE]
>  Dado que una declaración es una instrucción, una declaración puede ser una de las instrucciones en el *lista de instrucciones*. Por consiguiente, los nombres declarados dentro de una instrucción compuesta, pero no declarados explícitamente como static, tienen ámbito local y (para objetos) duración. Vea [ámbito](../cpp/scope-visual-cpp.md) para obtener más información sobre el tratamiento de nombres con ámbito local.  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre las instrucciones de C++](../cpp/overview-of-cpp-statements.md)