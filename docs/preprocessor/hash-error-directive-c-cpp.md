---
title: '#Error (directiva) (C/C ++) | Microsoft Docs'
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
ms.openlocfilehash: d2da939fe52e41e122ecd4926e34fb9c4be735ae
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42544493"
---
# <a name="error-directive-cc"></a>#error (Directiva) (C/C++)
El **#error** directiva emite un mensaje de error especificado por el usuario en tiempo de compilación y, a continuación, finaliza la compilación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#errortoken-string  
```  
  
## <a name="remarks"></a>Comentarios  
 
El mensaje de error que esta directiva emite incluye el *token-string* parámetro. El *token-string* parámetro no está sujeto a la expansión de macro. Esta directiva es más útil durante el preprocesamiento para notificar al desarrollador una incoherencia del programa o la infracción de una restricción. En el ejemplo siguiente se muestra el procesamiento de errores durante el preprocesamiento:  
  
```  
#if !defined(__cplusplus)  
#error C++ compiler required.  
#endif  
```  
  
## <a name="see-also"></a>Vea también  
 
[Directivas de preprocesador](../preprocessor/preprocessor-directives.md)