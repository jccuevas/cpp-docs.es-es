---
title: C2757 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2757
dev_langs:
- C++
helpviewer_keywords:
- C2757
ms.assetid: 421f102f-8a32-4d47-a109-811ddf2c909d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 14a65233ae0ad0a925d0b0d18cbc1b196fa5949a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2757"></a>C2757 de Error del compilador
'símbolo': ya existe un símbolo con este nombre y, por tanto, no se puede usar este nombre como un nombre de espacio de nombres  
  
 Un símbolo usado en la compilación actual como un identificador de espacio de nombres ya se está usando en un ensamblado de referencia.  
  
 El ejemplo siguiente genera C2757:  
  
```  
// C2757a.cpp  
// compile with: /clr /LD  
public ref class Nes {};  
```  
  
 Y luego,  
  
```  
// C2757b.cpp  
// compile with: /clr /c  
#using <C2757a.dll>  
  
namespace Nes {    // C2757  
// try the following line instead  
// namespace Nes2 {  
   public ref class X {};  
}  
```  
