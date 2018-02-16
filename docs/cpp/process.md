---
title: proceso | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- process_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c50948d613a40a03d0249e1930943ef61c855b9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="process"></a>proceso
Especifica que el proceso de la aplicación administrada debe tener una única copia de una variable global determinada, una variable miembro estática o una variable local estática compartida en todos los dominios de aplicación del proceso. Esto principalmente estaba destinado a usarse cuando se compila con **/CLR: pure**, que ahora está en desuso y se quitará en una versión futura del compilador. Cuando se compila con **/CLR**, variables globales y estáticas son por proceso de forma predeterminada (no es necesario usar `__declspec(process)`.  
  
 Solo una variable global, una variable miembro estática o una variable local estática de tipo nativo se pueden marcar con `__declspec(process)`.  
  
  
 `process` solo es válido cuando se compila con [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
 Si desea que cada dominio de aplicación tiene su propia copia de una variable global, utilice [appdomain](../cpp/appdomain.md).  
  
 Vea [dominios de aplicación y Visual C++](../dotnet/application-domains-and-visual-cpp.md) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [__declspec](../cpp/declspec.md)   
 [Palabras clave](../cpp/keywords-cpp.md)