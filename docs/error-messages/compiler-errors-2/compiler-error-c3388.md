---
title: Error del compilador C3388 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3388
dev_langs: C++
helpviewer_keywords: C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dce412e8998448cdbf746b4598804f2645e10237
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3388"></a>Error del compilador C3388
'type': no se permite como restricción; se supone 'ref class' para continuar con el análisis  
  
 Se especificó una restricción en un tipo genérico, pero la restricción no se especificó correctamente. Vea [restricciones en parámetros de tipo genérico (C++ / CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3388.  
  
```  
// C3388.cpp  
// compile with: /clr /c  
interface class AA {};  
  
generic <class T>  
where T : interface class   // C3388  
ref class C {};  
  
// OK  
generic <class T>  
where T : AA  
ref class D {};  
```