---
title: "Traducción: Diagnóstico | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
caps.latest.revision: 6
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 525f8c235a4c2500b09ac37a050d4b57fadc8fb9
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="translation-diagnostics"></a>Traducción: Diagnóstico
**ANSI 2.1.1.3** Cómo se identifica un diagnóstico  
  
 Microsoft C muestra mensajes de error con el formato:  
  
```  
  
filename( line-number ) : diagnostic Cnumbermessage  
```  
  
 donde *filename* es el nombre del archivo de código fuente en el que se encontró el error; *line-number* es el número de línea en el que el compilador detectó el error; `diagnostic` es un "error" o "advertencia"; `number` es un número único de cuatro dígitos (precedido de una **C**, como se indica en la sintaxis) que identifica el error o advertencia; `message` es un mensaje explicativo.  
  
## <a name="see-also"></a>Vea también  
 [Comportamiento definido por la implementación](../c-language/implementation-defined-behavior.md)
