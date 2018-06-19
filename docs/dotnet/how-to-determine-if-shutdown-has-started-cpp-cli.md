---
title: 'Cómo: determinar si ha iniciado el apagado (C++ / CLI) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .NET Framework, shutdown
- shutdown
- termination
- applications [C++], shutdown
ms.assetid: a8d39731-dea8-4f0a-96b7-2a5de09b21d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bbcc2b1efa54808b25238bde4de3dcc21d2ba687
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137707"
---
# <a name="how-to-determine-if-shutdown-has-started-ccli"></a>Cómo: Determinar si se ha iniciado el cierre del sistema (C++/CLI)
En el ejemplo de código siguiente se muestra cómo determinar si la aplicación o .NET Framework actualmente está finalizando. Esto es útil para tener acceso a elementos estáticos de .NET Framework porque, durante el cierre, estas construcciones son finalizadas por el sistema y no se puede usar de forma confiable. Comprobando el <xref:System.Environment.HasShutdownStarted%2A> propiedad en primer lugar, puede evitar posibles errores si no tiene acceso a estos elementos.  
  
## <a name="example"></a>Ejemplo  
  
```  
// check_shutdown.cpp  
// compile with: /clr  
using namespace System;  
int main()   
{  
   if (Environment::HasShutdownStarted)  
      Console::WriteLine("Shutting down.");  
   else  
      Console::WriteLine("Not shutting down.");  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Operaciones de Windows (C++ / CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)