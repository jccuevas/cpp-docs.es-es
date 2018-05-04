---
title: Instrucciones compuestas (bloques) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a8823935ee2f871cdc033aec23f05fc108244e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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