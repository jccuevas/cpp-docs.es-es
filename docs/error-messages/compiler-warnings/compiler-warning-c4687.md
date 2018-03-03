---
title: Advertencia del compilador C4687 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4687
dev_langs:
- C++
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 41992e91b40fc17ef73ccb75828796b31ee3249e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4687"></a>Advertencia del compilador C4687
'clase': una clase abstracta sealed no puede implementar una interfaz 'interfaz'  
  
 Normalmente, un tipo sealed abstracto sólo es útil para contener las funciones miembro estáticas.  
  
 Para obtener más información, consulte [abstracta](../../windows/abstract-cpp-component-extensions.md)y [sellado](../../windows/sealed-cpp-component-extensions.md).  
  
 Advertencia C4687 se emite como un error de forma predeterminada. Puede suprimir la advertencia C4687 con la [advertencia](../../preprocessor/warning.md) pragma. Si está seguro de que desea implementar una interfaz en un tipo sealed abstracto, puede suprimir la advertencia C4687.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4687.  
  
```  
// C4687.cpp  
// compile with: /clr /c  
interface class A {};  
  
ref struct B sealed abstract : A {};   // C4687  
ref struct C sealed : A {};   // OK  
ref struct D abstract : A {};   // OK  
```