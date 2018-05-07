---
title: Listas de inicializadores | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializer lists
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6634b749480e5108548de0c8b53f8b09cc5a42c2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="initializer-lists"></a>Listas de inicializadores
Ahora se denominan listas de inicializadores en constructores antes del constructor de clase base.  
  
## <a name="remarks"></a>Comentarios  
 Antes de Visual C++ 2005, se llama al constructor de clase base antes de la lista de inicializadores al compilar con extensiones administradas para C++. Ahora, cuando se compila con **/CLR**, se llama primero a la lista de inicializadores.  
  
## <a name="see-also"></a>Vea también  
 [Cambios generales en el lenguaje (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)