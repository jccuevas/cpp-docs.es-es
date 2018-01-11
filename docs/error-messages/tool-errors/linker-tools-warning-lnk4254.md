---
title: Las herramientas del vinculador LNK4254 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4254
dev_langs: C++
helpviewer_keywords: LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e17bcd03f92114c1b7cd21e63220cf6372c17bf2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4254"></a>Advertencia de las herramientas del vinculador LNK4254
sección 'sección1' (desplazamiento) combinada en 'sección2' (desplazamiento) con atributos diferentes  
  
 El contenido de una sección se combina con otra, pero los atributos de las dos secciones son diferentes. El programa puede provocar resultados inesperados. Por ejemplo, datos que desea leer solo pueden ahora tener una sección de escritura.  
  
 Para resolver LNK4254, modifique o quite la solicitud de combinación.  
  
 Cuando el destino es x86 máquinas y destinos de Windows CE (ARM, MIPS, SH4 y Thumb) con Visual C++, el. Sección de CRT es de solo lectura. Si el código depende del comportamiento anterior (. Secciones de CRT son de lectura/escritura), se podrían producir comportamientos inesperados.  
  
 Para obtener más información, vea  
  
-   [/Merge (combinar secciones)](../../build/reference/merge-combine-sections.md)  
  
-   [comment (C/C++)](../../preprocessor/comment-c-cpp.md)  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia LNK4254.  
  
```  
// LNK4254.cpp  
// compile with: /W1 /link /WX  
// LNK4254 expected  
#pragma comment(linker, "/merge:.data=.text")  
int main() {}  
```