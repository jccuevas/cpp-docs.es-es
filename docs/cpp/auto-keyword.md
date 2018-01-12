---
title: palabra clave Auto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: auto_cpp
dev_langs: C++
helpviewer_keywords:
- automatic storage class [C++], auto keyword
- auto keyword [C++]
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3508217e7dc333543fa2dbff9cf0643d6faff060
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="auto-keyword"></a>auto (Palabra clave)
La palabra clave `auto` es un especificador de declaración. Sin embargo, C++ estándar define un significado original y otro revisado para esta palabra clave. Antes de Visual C++ 2010, la `auto` palabra clave declara una variable en el *automática* clase de almacenamiento; es decir, una variable que tiene una duración local. A partir de Visual C++ 2010, la `auto` palabra clave declara una variable cuyo tipo se deduce de la expresión de inicialización en su declaración. El [/Zc: auto &#91;-&#93;](../build/reference/zc-auto-deduce-variable-type.md) opción del compilador controla el significado de la `auto` (palabra clave).  
  
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