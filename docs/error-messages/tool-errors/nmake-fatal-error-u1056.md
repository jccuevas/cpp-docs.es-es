---
title: Error grave de NMAKE U1056 | Microsoft Docs
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
ms.openlocfilehash: e0a83c62bedf995708d5e99fee19f05696d05c2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065704"
---
# <a name="nmake-fatal-error-u1056"></a>Error grave de NMAKE U1056

no se puede encontrar el procesador de comandos

El procesador de comandos no estaba en la ruta de acceso especificada en el **COMSPEC** o **ruta** variables de entorno.

NMAKE utiliza COMMAND.COM o CMD. EXE como un procesador de comandos al ejecutar comandos. Busca primero el procesador de comandos en la ruta de acceso establecido **COMSPEC**. Si **COMSPEC** no existe, los directorios especificados en las búsquedas NMAKE **ruta de acceso**.