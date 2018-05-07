---
title: 'Cómo: recuperar el nombre del equipo Local (C++ / CLI) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- computer name, retrieving
- machine name, retrieving
- computer name
ms.assetid: 6c7acb9a-3f9b-43b2-a756-bd4fb859e697
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f02c9d12809ef908415c58c6b04da2597a3a1bfc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-the-local-machine-name-ccli"></a>Cómo: Recuperar el nombre del equipo local (C++/CLI)
En el ejemplo de código siguiente se muestra la recuperación del nombre del equipo local (el nombre del equipo tal y como aparece en una red). Puede hacerlo mediante la obtención del <xref:System.Environment.MachineName%2A> cadena, que se define en el <xref:System.Environment> espacio de nombres.  
  
## <a name="example"></a>Ejemplo  
  
```  
// machine_name.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   Console::WriteLine("\nMachineName: {0}", Environment::MachineName);  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Operaciones de Windows (C++ / CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)