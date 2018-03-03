---
title: _fmode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- fmode
- _fmode
dev_langs:
- C++
helpviewer_keywords:
- file translation [C++], default mode
- fmode function
- _fmode function
ms.assetid: ac6df9eb-e5cc-4c54-aff3-373c21983118
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d4fdaeb0e67832f4f9e0c657e48fe74a88b86292
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fmode"></a>_fmode
La variable `_fmode` establece el modo de traducción de archivo predeterminado para la traducción de texto o binaria. Esta variable global ha quedado en desuso en las versiones funcionales más seguras [_get_fmode](../c-runtime-library/reference/get-fmode.md) y [_set_fmode](../c-runtime-library/reference/set-fmode.md), que deben usarse en lugar de la variable global. Se declara en Stdlib.h como sigue.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
extern int _fmode;  
```  
  
## <a name="remarks"></a>Comentarios  
 El valor predeterminado de `_fmode` es `_O_TEXT` para la traducción de modo de texto. `_O_BINARY` es la configuración para el modo binario.  
  
 Puede cambiar el valor de `_fmode` de tres formas:  
  
-   Establezca un vínculo con Binmode.obj. Esto cambia la configuración inicial de `_fmode` a `_O_BINARY`, lo que hace que todos los archivos excepto `stdin`, `stdout` y `stderr` se abran en modo binario.  
  
-   Realice una llamada a `_get_fmode` o `_set_fmode` para obtener o establecer la variable global `_fmode`, respectivamente.  
  
-   Cambie el valor de `_fmode` directamente al configurarlo en el programa.  
  
## <a name="see-also"></a>Vea también  
 [Variables globales](../c-runtime-library/global-variables.md)   
 [_get_fmode](../c-runtime-library/reference/get-fmode.md)   
 [_set_fmode](../c-runtime-library/reference/set-fmode.md)