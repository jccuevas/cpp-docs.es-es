---
title: Error grave de NMAKE U1056
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: b15b14c04dd91ae648ea4311612c122f04f90477
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635934"
---
# <a name="nmake-fatal-error-u1056"></a>Error grave de NMAKE U1056

no se puede encontrar el procesador de comandos

El procesador de comandos no estaba en la ruta de acceso especificada en el **COMSPEC** o **ruta** variables de entorno.

NMAKE utiliza COMMAND.COM o CMD. EXE como un procesador de comandos al ejecutar comandos. Busca primero el procesador de comandos en la ruta de acceso establecido **COMSPEC**. Si **COMSPEC** no existe, los directorios especificados en las búsquedas NMAKE **ruta de acceso**.