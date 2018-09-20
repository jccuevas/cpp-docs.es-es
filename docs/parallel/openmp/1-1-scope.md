---
title: 1.1 definir el ámbito de | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a8570a3c-1dd6-4c3d-b368-a10fcb3534a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81babf799860030f6d398f64b55ed65039de8649
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393539"
---
# <a name="11-scope"></a>1.1 Ámbito

Esta especificación describe paralelización solo dirigido por el usuario, en la que el usuario especifica explícitamente las acciones que deben realizarse por el compilador y el sistema de tiempo de ejecución para ejecutar el programa en paralelo. Las implementaciones de OpenMP C y C++ no tienen que buscar dependencias, los conflictos, interbloqueos, condiciones de carrera u otros problemas que producen la ejecución del programa incorrecto. El usuario es responsable de garantizar que la aplicación con las construcciones OpenMP C y C++ API se ejecuta correctamente. Paralelización automáticas generadas por el compilador y las directivas del compilador para ayudar a dicha ejecución en paralelo no están cubiertas en este documento.