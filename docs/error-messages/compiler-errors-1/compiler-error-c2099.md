---
title: Error del compilador C2099 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2099
dev_langs:
- C++
helpviewer_keywords:
- C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 74fdc75470600c29029c52e38ab2073e484dbde6
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2099"></a>Error del compilador C2099
el inicializador no es una constante  
  
 Este error solo lo emite el compilador de C y únicamente se genera para variables no automáticas.  El compilador inicializa variables no automáticas al inicio del programa y los valores con los que se inicializan deben ser constantes.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C2099.  
  
```  
// C2099.c  
int j;  
int *p;  
j = *p;   // C2099 *p is not a constant  
```  
  
## <a name="example"></a>Ejemplo  
 Error C2099 también puede producirse porque el compilador no puede efectuar el plegamiento constante sobre una expresión en **/fp: strict** porque la configuración de entorno de precisión punto flotante (vea [_controlfp_s](../../c-runtime-library/reference/controlfp-s.md) para obtener más información) puede diferir de la compilación y en tiempo de ejecución.  
  
 Cuando falla el plegamiento constante, el compilador invoca una inicialización dinámica, que no se permite en C.  
  
 Para resolver este error, compile el módulo como archivo .cpp o simplifique la expresión.  
  
 Para obtener más información, consulte [/fp (Especificar comportamiento de punto flotante)](../../build/reference/fp-specify-floating-point-behavior.md).  
  
 El ejemplo siguiente genera la advertencia C2099.  
  
```  
// C2099_2.c  
// compile with: /fp:strict /c  
float X = 2.0 - 1.0;   // C2099  
float X2 = 1.0;   // OK  
```
