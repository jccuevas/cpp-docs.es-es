---
title: C2632 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2632
dev_langs: C++
helpviewer_keywords: C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 03a6d75ab9af6cd45ef982ff9d2e12640266c1b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2632"></a>C2632 de Error del compilador
'tipo1' seguido de 'tipo2' no es válido  
  
 Este error puede generarse si falta código entre dos especificadores de tipo.  
  
 El ejemplo siguiente genera C2632:  
  
```  
// C2632.cpp  
int float i;   // C2632  
```  
  
 Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio .NET 2003. `bool`Ahora es un tipo adecuado. En versiones anteriores, `bool` era una definición de tipo y puede crear identificadores con ese nombre.  
  
 El ejemplo siguiente genera C2632:  
  
```  
// C2632_2.cpp  
// compile with: /LD  
void f(int bool);   // C2632  
```  
  
 Para resolver este error para que el código sea válido en las versiones tanto el Visual Studio .NET 2003 y Visual Studio .NET de Visual C++, cambie el nombre del identificador.