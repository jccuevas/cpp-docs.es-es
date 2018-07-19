---
title: Especificadores | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declaration specifiers
- declarations, specifiers
- specifiers, in declarations
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d437b70148fdaba4c8eb4d7aa855e7d75f6f2487
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953752"
---
# <a name="specifiers"></a>Especificadores
Este tema se describe la *decl-specifiers* componente (especificadores de declaración) de un [declaración](declarations-and-definitions-cpp.md).  
  
 Los siguientes marcadores de posición y palabras clave de lenguaje son especificadores de declaración:  
  
 *especificador de clase de almacenamiento*  
  
 *especificador de tipo*  
  
 *especificador de función*  
  
 [friend](../cpp/friend-cpp.md)  
  
 [typedef] ( [typedef](http://msdn.microsod) `(` *extended-decl-modifier-seq* `)`  
  
## <a name="remarks"></a>Comentarios  
 El *decl-specifiers* parte de una declaración es la secuencia más larga de *decl-specifiers* que se puede tomar para indicar un nombre de tipo, sin incluir el puntero o hacer referencia a los modificadores. El resto de la declaración es la *declarador*, que incluye el nombre introducido.  
  
 En la tabla siguiente incluye cuatro declaraciones y, a continuación, enumera cada declaración *decl-specifers* y *declarador* componente por separado.  
  
|Declaración|*decl-specifiers*|`declarator`|  
|-----------------|------------------------|------------------|  
|`char *lpszAppName;`|**char**|`*lpszAppName`|  
|`typedef char * LPSTR;`|**char**|`*LPSTR`|  
|`const int func1();`|**Const int**|`func1`|  
|`volatile void *pvvObj;`|**anular volátil**|`*pvvObj`|  
  
 Dado que **firmado**, **sin signo**, **largo**, y **corto** implican **int**, un  **TypeDef** nombre siguiente, una de estas palabras clave se considera que es un miembro de *declarator-list,* no de *decl-specifiers*.  
  
> [!NOTE]
>  Dado que un nombre se puede declarar de nuevo, su interpretación está sujeta a la declaración más reciente del ámbito actual. La nueva declaración puede afectar al modo en que el compilador interpreta los nombres, especialmente los nombres de `typedef`.  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones y definiciones](declarations-and-definitions-cpp.md)