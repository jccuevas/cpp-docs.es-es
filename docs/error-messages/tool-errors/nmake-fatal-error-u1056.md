---
title: Error grave de NMAKE U1056
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: 10131e518fa608292fff58672ede36390bcd665b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182908"
---
# <a name="nmake-fatal-error-u1056"></a>Error grave de NMAKE U1056

no se puede encontrar el procesador de comandos

El procesador de comandos no estaba en la ruta de acceso especificada en las variables de entorno **comspec** o **path** .

NMAKE usa COMMAND.COM o CMD. EXE como procesador de comandos al ejecutar comandos. Busca el procesador de comandos en primer lugar en la ruta de acceso establecida en **comspec**. Si no existe la **especificación** , NMAKE busca en los directorios especificados en **ruta de acceso**.
