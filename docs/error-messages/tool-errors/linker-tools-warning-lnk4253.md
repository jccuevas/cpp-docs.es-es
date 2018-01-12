---
title: Las herramientas del vinculador LNK4253 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4253
dev_langs: C++
helpviewer_keywords: LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d1142544852980b8bd1d543783a9ffdf3361879
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4253"></a>Advertencia de las herramientas del vinculador LNK4253
sección 'sección1' no combinada en 'sección2'; ya se combinó en 'sección3'  
  
 El vinculador detectó varias solicitudes de combinación en conflicto. El vinculador omitirá una de las solicitudes.  
  
 A **/MERGE** opción o directiva se encuentra y la `from` sección ya se ha combinado con una sección diferente debido a una anterior **/MERGE** opción o directiva (o debido a una combinación implícita el vinculador).  
  
 Para resolver LNK4253, quite una de las solicitudes de combinación.  
  
 Cuando el destino es x86 máquinas y destinos de Windows CE (ARM, MIPS, SH4 y Thumb) con Visual C++, el. Sección de CRT es de solo lectura. Si el código depende del comportamiento anterior (. Secciones de CRT son de lectura/escritura), se podrían producir comportamientos inesperados.  
  
 Para obtener más información, vea  
  
-   [/MERGE (Combinar secciones)](../../build/reference/merge-combine-sections.md)  
  
-   [comment (C/C++)](../../preprocessor/comment-c-cpp.md)  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se indica al vinculador para combinar la `.rdata` sección dos veces, pero en secciones diferentes. El ejemplo siguiente genera la advertencia LNK4253.  
  
```  
// LNK4253.cpp  
// compile with: /W1 /link /merge:.rdata=text2  
// LNK4253 expected  
#pragma comment(linker, "/merge:.rdata=.text")  
int main() {}  
```