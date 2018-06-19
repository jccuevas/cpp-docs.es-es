---
title: Error grave de NMAKE U1056 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1056
dev_langs:
- C++
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19890e290c98fd9602d755ad35f9d47204bd6c24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316561"
---
# <a name="nmake-fatal-error-u1056"></a>Error grave de NMAKE U1056
no se puede encontrar el procesador de comandos  
  
 El procesador de comandos no estaba en la ruta de acceso especificada en el **COMSPEC** o **ruta de acceso** variables de entorno.  
  
 NMAKE utiliza COMMAND.COM o CMD. EXE como un procesador de comandos al ejecutar comandos. Busca primero el procesador de comandos en la ruta de acceso establecido **COMSPEC**. Si **COMSPEC** no existe, los directorios especificados en las búsquedas NMAKE **ruta de acceso**.