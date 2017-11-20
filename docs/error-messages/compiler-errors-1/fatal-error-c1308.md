---
title: Error irrecuperable C1308 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1308
dev_langs: C++
helpviewer_keywords: C1308
ms.assetid: 46177997-069e-433a-8e20-93c846d78ffd
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f9958ccb3daa537f8789d7485822fd623da8c703
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1308"></a>Error irrecuperable C1308
no se admite la vinculación de ensamblados  
  
 Se permite un archivo .netmodule como entrada del vinculador, pero no es de un ensamblado. Este error puede generarse cuando se realiza un intento para vincular un ensamblado compilado con `/clr:safe`.  
  
 Para más información, consulte [Archivos .netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md).  
  
 El ejemplo siguiente genera C1308:  
  
```  
// C1308.cpp  
// compile with: /clr:safe /LD  
public ref class MyClass {  
public:  
   int i;  
};  
```  
  
 Y entonces  
  
```  
// C1308b.cpp  
// compile with: /clr /link C1308b.obj C1308.dll  
// C1308 expected  
#using "C1308.dll"  
int main() {  
   MyClass ^ my = gcnew MyClass();  
}  
```