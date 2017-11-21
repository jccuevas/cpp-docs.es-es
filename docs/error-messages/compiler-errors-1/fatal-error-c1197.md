---
title: Error irrecuperable C1197 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1197
dev_langs: C++
helpviewer_keywords: C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d0eb3ab152e9299d47210a6d2c1eb58e3f92a925
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1197"></a>Error irrecuperable C1197
no puede hacer referencia 'a mscorlib.dll_1' como el programa ya hacía referencia 'a mscorlib.dll_2'  
  
 El compilador se empareja con una versión de common language runtime.  Sin embargo, se ha intentado hacer referencia a una versión de un archivo de common language runtime desde una versión anterior.  
  
 Para resolver este error, sólo los archivos de referencia de la versión de common language runtime que se incluye con la versión de Visual C++ están compilando con.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C1197:  
  
```  
// C1197.cpp  
// compile with: /clr /c  
// processor: x86  
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197  
// try the following line instead  
// #using "mscorlib.dll"  
```