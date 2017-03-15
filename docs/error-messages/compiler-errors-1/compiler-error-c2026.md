---
title: Error de compilador un error C2026 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2026
dev_langs:
- C++
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
caps.latest.revision: 8
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: c429f81c64b7710b7edc2b8540d98e8c790e4062
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2026"></a>Error de compilador un error C2026
cadena demasiado grande; caracteres finales truncados  
  
 La cadena sobrepasaba el límite de 16380 caracteres de un solo byte.  
  
 Antes de la concatenación de cadenas adyacentes, una cadena no puede tener más de 16380 caracteres de un solo byte.  
  
 Una cadena Unicode de alrededor de la mitad de esta longitud generaría también este error.  
  
 Si tiene una cadena que se define como sigue, generará un error C2026:  
  
```  
char sz[] =  
"\  
imagine a really, really \  
long string here\  
";  
```  
  
 Se puede dividir como sigue:  
  
```  
char sz[] =  
"\  
imagine a really, really "  
"long string here\  
";  
```  
  
 Puede almacenar los literales de cadenas excepcionalmente largas (32K o más) en un recurso personalizado o un archivo externo. Consulte [crear un nuevo personalizado o recurso de datos](../../windows/creating-a-new-custom-or-data-resource.md) para obtener más información.
