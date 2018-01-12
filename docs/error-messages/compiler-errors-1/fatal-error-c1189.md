---
title: Error irrecuperable C1189 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1189
dev_langs: C++
helpviewer_keywords: C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2330d49f817012fc2e0381a0991f709ada74ea32
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1189"></a>Error irrecuperable C1189
\#Error: mensaje de error proporcionado por el usuario  
  
 Genera el error C1189 el `#error` directiva. El desarrollador que codifica la directiva especifica el texto del mensaje de error. Para obtener más información, consulte [#error (directiva) (C/C ++)](../../preprocessor/hash-error-directive-c-cpp.md).  
  
 El ejemplo siguiente genera el error C1189. En el ejemplo, el desarrollador emite un mensaje de error personalizado porque el `_WIN32` no está definido el identificador:  
  
```  
// C1189.cpp  
#undef _WIN32  
#if !defined(_WIN32)  
#error _WIN32 must be defined   // C1189  
#endif  
```  
  
 También puede ver este error si se compila un proyecto ATL mediante el **/ robust** opción del compilador MIDL. Use la **/ robust** conmutador que se va a compilar sólo [!INCLUDE[win2kfamily](../../c-runtime-library/includes/win2kfamily_md.md)] y versiones posteriores de Windows. Para corregir este error, utilice uno de los procedimientos siguientes:  
  
-   Cambie esta línea en el archivo dlldatax.c:  
  
```  
#define _WIN32_WINNT 0x0400   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
 a:  
  
```  
#define _WIN32_WINNT 0x0500   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
-   Use la **avanzadas** página de propiedades de la **MIDL** carpeta de la página de propiedades para quitar el **/ robust** cambiar y, a continuación, especifique la **/no_robust** conmutador. Para obtener más información, consulte [páginas de propiedades MIDL: avanzadas](../../ide/midl-property-pages-advanced.md).  
  
## <a name="see-also"></a>Vea también  
 [#define (directiva) (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)