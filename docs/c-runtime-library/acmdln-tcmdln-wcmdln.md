---
title: _acmdln, _tcmdln, _wcmdln | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcmdln
- _acmdln
apilocation: msvcrt.dll
apitype: DLLExport
f1_keywords:
- _acmdln
- acmdln
- _wcmdln
- wcmdln
- _tcmdln
- tcmdln
dev_langs: C++
helpviewer_keywords:
- _wcmdln global variable
- wcmdln global variable
- _acmdln global variable
- _tcmdln global variable
- tcmdln global variable
- acmdln global variable
ms.assetid: 4fc0a6a0-3f93-420a-a19f-5276061ba539
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a713978e44762d5e4c771112ef5adf256a9475c6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="acmdln-tcmdln-wcmdln"></a>_acmdln, _tcmdln, _wcmdln
Variable global CRT interna. Línea de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
char * _acmdln;  
wchar_t * _wcmdln;  
  
#ifdef WPRFLAG  
   #define _tcmdln _wcmdln  
#else  
   #define _tcmdln _acmdln  
```  
  
## <a name="remarks"></a>Comentarios  
 Estas variables de CRT internas almacenan la línea de comandos completa. Se muestran en los símbolos exportados de CRT, pero usarlas en su código no está previsto. `_acmdln` almacena los datos como una cadena de caracteres. `_wcmdln` almacena los datos como una cadena de caracteres anchos. `_tcmdln` se puede definir como `_acmdln` o `_wcmdln`, según lo que sea apropiado.  
  
## <a name="see-also"></a>Vea también  
 [Variables globales](../c-runtime-library/global-variables.md)