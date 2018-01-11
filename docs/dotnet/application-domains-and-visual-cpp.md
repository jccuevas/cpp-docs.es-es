---
title: "Dominios de aplicación y Visual C++ | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interop [C++], application domains
- application domains [C++], C++
- /clr compiler option [C++], application domains
- interoperability [C++], application domains
- mixed assemblies [C++], application domains
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a66731b9645458441f1c3e1f211c74be698e7231
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="application-domains-and-visual-c"></a>Dominios de aplicación y Visual C++
Si tiene un `__clrcall` función virtual, que será la vtable por dominio de aplicación (appdomain). Si crea un objeto en un appdomain, solo puede llamar a la función virtual desde dentro de ese appdomain. Todas las funciones definidas en **/CLR: pure** compilandos usar el `__clrcall` convención de llamada. Por lo tanto, todas las tablas virtuales definieron en **/CLR: pure** compilandos son por appdomain. En modo mixto (**/CLR**) tendrá por tablas virtuales del proceso si el tipo no tiene ningún `__clrcall` funciones virtuales. Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015.  
  
 Para obtener más información, consulte  
  
-   [appdomain](../cpp/appdomain.md)  
  
-   [__clrcall](../cpp/clrcall.md)  
  
-   [Cómo: migrar a/CLR: pure (C++ / CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [process](../cpp/process.md)  
  
## <a name="see-also"></a>Vea también  
 [Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)