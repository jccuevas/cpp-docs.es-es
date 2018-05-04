---
title: proceso | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- process_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8aa1ba2676ebbd04d1fc1a59d210d69efeab6658
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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