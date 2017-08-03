---
title: Constantes del campo st_mode de la estructura _stat | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- S_IFCHR
- S_IFDIR
- _S_IWRITE
- S_IFMT
- _S_IFDIR
- _S_IREAD
- S_IEXEC
- _S_IEXEC
- _S_IFMT
- S_IWRITE
- S_IFREG
- S_IREAD
- _S_IFCHR
- _S_IFREG
dev_langs:
- C++
helpviewer_keywords:
- S_IFDIR constant
- stat structure
- S_IWRITE constant
- S_IEXEC constant
- _S_IFREG constant
- S_IREAD constant
- stat structure, constants
- _S_IFMT constant
- st_mode field constants
- S_IFMT constant
- _S_IEXEC constant
- _S_IWRITE constant
- _S_IFDIR constant
- S_IFREG constant
- S_IFCHR constant
- _S_IREAD constant
- _S_IFCHR constant
ms.assetid: fd462004-7563-4766-8443-30b0a86174b6
caps.latest.revision: 6
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: ebac26fce8a1717cd6d964e8cec6a5ce7e3c2d8f
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="stat-structure-stmode-field-constants"></a>Constantes del campo st_mode de la estructura _stat
## <a name="syntax"></a>Sintaxis  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Estas constantes se utilizan para indicar el tipo de archivo en el campo **st_mode** de la estructura [_stat structure](../c-runtime-library/standard-types.md).  
  
 A continuación se describen las constantes de máscara de bits:  
  
|Constante|Significado|  
|--------------|-------------|  
|`_S_IFMT`|Máscara de tipo de archivo|  
|`_S_IFDIR`|Directorio|  
|`_S_IFCHR`|Carácter especial (indica un dispositivo si está configurado)|  
|`_S_IFREG`|Estándar|  
|`_S_IREAD`|Permiso de lectura, propietario|  
|`_S_IWRITE`|Permiso de escritura, propietario|  
|`_S_IEXEC`|Permiso de ejecución y búsqueda, propietario|  
  
## <a name="see-also"></a>Vea también  
 [_stat, _wstat (Funciones)](../c-runtime-library/reference/stat-functions.md)   
 [_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [Tipos estándar](../c-runtime-library/standard-types.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)
