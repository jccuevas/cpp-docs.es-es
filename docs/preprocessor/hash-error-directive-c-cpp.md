---
title: '#Error de directiva (C/C ++) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#error'
dev_langs:
- C++
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e449da64b5221ccddee34dd850a987b28a2f39df
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="error-directive-cc"></a>#error (Directiva) (C/C++)
La directiva `#error` emite un mensaje de error especificado por el usuario en tiempo de compilación y después finaliza la compilación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#errortoken-string  
```  
  
## <a name="remarks"></a>Comentarios  
 El mensaje de error que emite esta directiva incluye el *token-string* parámetro. El parámetro `token-string` no está sujeto a la expansión de macro. Esta directiva es más útil durante el preprocesamiento para notificar al desarrollador una incoherencia del programa o la infracción de una restricción. En el ejemplo siguiente se muestra el procesamiento de errores durante el preprocesamiento:  
  
```  
#if !defined(__cplusplus)  
#error C++ compiler required.  
#endif  
```  
  
## <a name="see-also"></a>Vea también  
 [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)