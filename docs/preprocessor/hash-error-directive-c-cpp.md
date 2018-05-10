---
title: '#Error de directiva (C/C ++) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba4f0e06798bc6419f8db0471f19588039eb679a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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