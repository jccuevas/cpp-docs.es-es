---
title: Las herramientas del vinculador LNK4254 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4254
dev_langs:
- C++
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb57882ab4269c06a53ed73fed2a9d6caf2f2c85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316899"
---
# <a name="linker-tools-warning-lnk4254"></a>Advertencia de las herramientas del vinculador LNK4254
sección 'sección1' (desplazamiento) combinada en 'sección2' (desplazamiento) con atributos diferentes  
  
 El contenido de una sección se combina con otra, pero los atributos de las dos secciones son diferentes. El programa puede provocar resultados inesperados. Por ejemplo, datos que desea leer solo pueden ahora tener una sección de escritura.  
  
 Para resolver LNK4254, modifique o quite la solicitud de combinación.  
  
 Cuando el destino es x86 máquinas y destinos de Windows CE (ARM, MIPS, SH4 y Thumb) con Visual C++, el. Sección de CRT es de solo lectura. Si el código depende del comportamiento anterior (. Secciones de CRT son de lectura/escritura), se podrían producir comportamientos inesperados.  
  
 Para obtener más información, vea  
  
-   [/MERGE (Combinar secciones)](../../build/reference/merge-combine-sections.md)  
  
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