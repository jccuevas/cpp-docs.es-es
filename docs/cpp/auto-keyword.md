---
title: palabra clave Auto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93b2f5e28dc0306a996b4c8bdb799122fe4646ab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="auto-keyword"></a>auto (Palabra clave)
La palabra clave `auto` es un especificador de declaración. Sin embargo, C++ estándar define un significado original y otro revisado para esta palabra clave. Antes de Visual C++ 2010, la `auto` palabra clave declara una variable en el *automática* clase de almacenamiento; es decir, una variable que tiene una duración local. A partir de Visual C++ 2010, la `auto` palabra clave declara una variable cuyo tipo se deduce de la expresión de inicialización en su declaración. El [/Zc: Auto&#91;-&#93; ](../build/reference/zc-auto-deduce-variable-type.md) opción del compilador controla el significado de la `auto` palabra clave.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
auto declarator ;  
auto declarator initializer;  
```  
  
## <a name="remarks"></a>Comentarios  
 La definición de la palabra clave `auto` cambia en el lenguaje de programación C++, pero no en el lenguaje de programación C.  
  
 En los temas siguientes se describe la palabra clave `auto` y la opción del compilador correspondiente:  
  
-   [Auto](../cpp/auto-cpp.md) describe la nueva definición de la `auto` (palabra clave).  
  
  
-   [/ Zc: Auto (deducir tipo de Variable)](../build/reference/zc-auto-deduce-variable-type.md) describe la opción del compilador que indica al compilador qué definición de la `auto` palabra clave que se va a usar.  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)