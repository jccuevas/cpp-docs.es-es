---
title: Error de las LNK2023 las herramientas del vinculador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2023
dev_langs:
- C++
helpviewer_keywords:
- LNK2023
ms.assetid: c99e35a8-739a-4a20-a715-29b8c3744703
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d8deaf8bfb10d3ceb56380560320ebb2cf9a7b8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090326"
---
# <a name="linker-tools-error-lnk2023"></a>Error de las herramientas del vinculador LNK2023

dll o punto de entrada erróneo \<dll o punto de entrada >

El vinculador está cargando una versión incorrecta de msobj90.dll. Asegúrese de que link.exe y msobj90.dll en la ruta de acceso tienen la misma versión.

Una dependencia de msobj90.dll no puede estar presente. La lista de dependencias para msobj90.dll es:

- Msvcr90.dll

- Kernel32.dll

Busque en el equipo para otras copias de msobj90.dll que puedan estar obsoleta.