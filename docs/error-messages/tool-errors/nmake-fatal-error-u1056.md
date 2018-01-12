---
title: Error grave de NMAKE U1056 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1056
dev_langs: C++
helpviewer_keywords: U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 41db646e2559051c11de5265900dde8ad0a03214
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1056"></a>Error grave de NMAKE U1056
no se puede encontrar el procesador de comandos  
  
 El procesador de comandos no estaba en la ruta de acceso especificada en el **COMSPEC** o **ruta de acceso** variables de entorno.  
  
 NMAKE utiliza COMMAND.COM o CMD. EXE como un procesador de comandos al ejecutar comandos. Busca primero el procesador de comandos en la ruta de acceso establecido **COMSPEC**. Si **COMSPEC** no existe, los directorios especificados en las búsquedas NMAKE **ruta de acceso**.