---
title: _SCL_SECURE_NO_WARNINGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
dev_langs:
- C++
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 285e54a2eab4d116df81c3e10c597c6dbb6dd9cb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS
Llamar a cualquiera de los métodos potencialmente no seguros en la biblioteca estándar de C++ producirá una [Advertencia del compilador (nivel 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Para deshabilitar esta advertencia, defina la macro **_SCL_SECURE_NO_WARNINGS** en el código:  
  
```  
#define _SCL_SECURE_NO_WARNINGS  
```  
  
## <a name="remarks"></a>Comentarios  
 Otras formas de deshabilitar la advertencia C4996 incluyen:  
  
-   Usar la opción del compilador [/D (Definiciones de preprocesador)](../build/reference/d-preprocessor-definitions.md):  
  
 ```  
    cl /D_SCL_SECURE_NO_WARNINGS [other compiler options] myfile.cpp  
```  
  
-   Usar la opción del compilador [/w](../build/reference/compiler-option-warning-level.md):  
  
 ```  
    cl /wd4996 [other compiler options] myfile.cpp  
```  
  
-   Usar la directiva [#pragma warning](../preprocessor/warning.md):  
  
 ```  
 #pragma warning(disable:4996)  
```  
  
 Además, puede cambiar manualmente el nivel de advertencia C4996 con el **/w\<l >\< n>**  opción del compilador. Por ejemplo, para establecer la advertencia C4996 en el nivel 4:  
  
```  
cl /w44996 [other compiler options] myfile.cpp  
```  
  
 Para más información, vea [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (nivel de advertencia)](../build/reference/compiler-option-warning-level.md).  
  
## <a name="see-also"></a>Vea también  
 [Bibliotecas seguras: Biblioteca estándar de C++](../standard-library/safe-libraries-cpp-standard-library.md)

