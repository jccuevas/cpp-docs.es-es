---
title: Listas de inicializadores | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: initializer lists
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1af020bec295f0f949b7ebb6abe88102f3942b1f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="initializer-lists"></a>Listas de inicializadores
Ahora se denominan listas de inicializadores en constructores antes del constructor de clase base.  
  
## <a name="remarks"></a>Comentarios  
 Antes de Visual C++ 2005, se llama al constructor de clase base antes de la lista de inicializadores al compilar con extensiones administradas para C++. Ahora, cuando se compila con **/CLR**, se llama primero a la lista de inicializadores.  
  
## <a name="see-also"></a>Vea también  
 [Cambios generales en el lenguaje (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)