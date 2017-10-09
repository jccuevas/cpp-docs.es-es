---
title: __p__fmode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __p__fmode
apilocation:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- __p__fmode
dev_langs:
- C++
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0a563385ecd1e773433e053cffbae24403eab6fc
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="pfmode"></a>__p__fmode
Apunta a la variable global `_fmode`, que especifica el *modo de traducción de archivos* predeterminado para las operaciones de E/S de archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
int* __p__fmode(  
   );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Puntero a la variable global `_fmode`.  
  
## <a name="remarks"></a>Comentarios  
 La función `__p__fmode` es solo para uso interno y no debe llamarse desde código de usuario.  
  
 El modo de traducción de archivos especifica la traducción `binary` o `text` para las operaciones de E/S [_open](../c-runtime-library/reference/open-wopen.md) y [_pipe](../c-runtime-library/reference/pipe.md). Para obtener más información, consulte [_fmode](../c-runtime-library/fmode.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|__p\__fmode|stdlib.h|
