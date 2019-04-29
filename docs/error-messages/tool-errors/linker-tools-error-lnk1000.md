---
title: Error de las herramientas del vinculador LNK1000
ms.date: 06/18/2018
f1_keywords:
- LNK1000
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
ms.openlocfilehash: b0e6eb3ba44216e9300506eb84adb61a6529903d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255477"
---
# <a name="linker-tools-error-lnk1000"></a>Error de las herramientas del vinculador LNK1000

> error desconocido; Consulte la documentación para las opciones de soporte técnico

Anote las circunstancias del error y, a continuación, intente aislar el problema y crear un caso de prueba reproducible. Para obtener información sobre cómo investigar y notificar estos errores, vea [cómo notificar un problema con el conjunto de herramientas de Visual C++ o documentación](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Puede obtener este error si mezcla los archivos de encabezado estándar (por ejemplo, Windows.h) y sus propios archivos. Incluir un encabezado precompilado, si cualquiera, primero y luego los encabezados estándar, seguido por sus propios archivos de encabezado.