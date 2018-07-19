---
title: Error del compilador C3807 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3807
dev_langs:
- C++
helpviewer_keywords:
- C3807
ms.assetid: 7e2b0aab-8c61-4e71-b9c1-fcaeb6a1b5ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4171b13d7605d296ac8ac6d1f06125d0fadd226
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272323"
---
# <a name="compiler-error-c3807"></a>Error del compilador C3807
'type': una clase con el atributo ComImport no puede derivar de 'tipo2', se permite solo la implementación de interfaz  
  
 Un tipo que deriva de <xref:System.Runtime.InteropServices.ComImportAttribute> sólo se puede implementar una interfaz.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3807.  
  
```  
// C3807.cpp  
// compile with: /clr /c  
ref struct S {};  
interface struct I {};  
  
[System::Runtime::InteropServices::ComImportAttribute()]  
ref struct S1 : S {};   // C3807  
ref struct S2 : I {};  
```