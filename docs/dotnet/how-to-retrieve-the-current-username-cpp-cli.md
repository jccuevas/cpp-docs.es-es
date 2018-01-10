---
title: "Cómo: recuperar el nombre de usuario actual (C++ / CLI) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- current user names
- user names, retrieving
- UserName string
ms.assetid: 91679571-d029-41f5-b657-1460c81c608a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f1532647327c039994a1d09ee8b7eacc2c341f88
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-retrieve-the-current-username-ccli"></a>Cómo: Recuperar el nombre de usuario actual (C++/CLI)
En el ejemplo de código siguiente se muestra la recuperación del nombre del usuario actual (el nombre del usuario que ha iniciado sesión en Windows). El nombre se almacena en la <xref:System.Environment.UserName%2A> cadena, que se define en el <xref:System.Environment> espacio de nombres.  
  
## <a name="example"></a>Ejemplo  
  
```  
// username.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   Console::WriteLine("\nCurrent user: {0}", Environment::UserName);  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Operaciones de Windows (C++ / CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)