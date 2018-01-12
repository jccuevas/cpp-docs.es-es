---
title: Las herramientas del vinculador LNK1313 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1313
dev_langs: C++
helpviewer_keywords: LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a9030921178fc23c225a775359724cf5c932d95e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1313"></a>Error de las herramientas del vinculador LNK1313
módulo ijw/native detectado; no se puede vincular con módulos puros  
  
 La versión actual de Visual C++ no admite la vinculación de archivos .obj administrados o nativos nativo o mixto con archivos .obj compilados con **/CLR: pure**.  
  
## <a name="example"></a>Ejemplo  
  
```  
// LNK1313.cpp  
// compile with: /c /clr:pure  
// a pure module  
int main() {}  
```  
  
## <a name="example"></a>Ejemplo  
  
```  
// LNK1313_b.cpp  
// compile with: /c /clr  
// an IJW module  
void test(){}  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente generará el error LNK1313.  
  
```  
// LNK1313_c.cpp  
// compile with: /link LNK1313.obj LNK1313_b.obj  
// LNK1313 warning expected  
```