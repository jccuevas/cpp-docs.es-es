---
title: Las herramientas del vinculador LNK1000 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 06/18/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1000
dev_langs:
- C++
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a01db36200995813ec4b6862e9ddd04c6f069ba
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238687"
---
# <a name="linker-tools-error-lnk1000"></a>Error de las herramientas del vinculador LNK1000

> error desconocido; Consulte la documentación para opciones de soporte técnico

Anote las circunstancias del error y, a continuación, intente aislar el problema y crear un caso de prueba reproducible. Para obtener información sobre cómo investigar y notificar estos errores, vea [cómo notificar un problema con el conjunto de herramientas de Visual C++ o documentación](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Puede obtener este error si mezcla archivos de encabezado estándar (por ejemplo, Windows.h) y sus propios archivos. Incluir un encabezado precompilado, si alguna, primero y luego los encabezados estándares, seguido de sus propios archivos de encabezado.