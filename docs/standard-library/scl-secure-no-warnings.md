---
title: _SCL_SECURE_NO_WARNINGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
dev_langs:
- C++
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
caps.latest.revision: 5
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 92cc02c47d4a423cce70a1289a1ce54587a92c2f
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

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


