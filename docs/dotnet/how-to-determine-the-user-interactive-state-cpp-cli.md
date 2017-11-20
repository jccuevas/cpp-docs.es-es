---
title: "Cómo: determinar el estado de interacción del usuario (C++ / CLI) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Visual C++, user interactive state
- user interactive state
ms.assetid: 9f52323e-38b8-4a41-9b1d-052012ad839b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f65933a1cbd81c0794263dfe3fa2628f52599257
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-determine-the-user-interactive-state-ccli"></a>Cómo: Determinar el estado de interacción con el usuario (C++/CLI)
En el ejemplo de código siguiente se muestra cómo determinar si se ejecuta código en un contexto de usuario interactivo. Si <xref:System.Environment.UserInteractive%2A> es false, el código se ejecuta como un proceso de servicio o desde dentro de una aplicación Web, en cuyo caso debe no intenta interactuar con el usuario.  
  
## <a name="example"></a>Ejemplo  
  
```  
// user_interactive.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   if ( Environment::UserInteractive )  
      Console::WriteLine("User interactive");  
   else  
      Console::WriteLine("Noninteractive");  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Operaciones de Windows (C++ / CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)