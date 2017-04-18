---
title: Error del compilador C3552 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3552
dev_langs:
- C++
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: ae268ae3c0d7857aa2c2cbafe9e158656f657f1a
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3552"></a>Error del compilador C3552
'typename': un tipo de valor devuelto especificado en tiempo de ejecución no puede contener 'auto'  
  
 Si usa la palabra clave `auto` como marcador de posición del tipo de valor devuelto de una función, debe facilitar un tipo de valor devuelto especificado en tiempo de ejecución. Sin embargo, no puede usar otra palabra clave `auto` para especificar el tipo de valor devuelto especificado en tiempo de ejecución. Por ejemplo, el siguiente fragmento de código genera el error C3552.  
  
 `auto myFunction->auto; // C3552`
