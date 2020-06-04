---
title: Error de las herramientas del vinculador LNK1000
ms.date: 06/18/2018
f1_keywords:
- LNK1000
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
ms.openlocfilehash: 48b976f6e996d0e076849dc9b20b4cedd47dfbcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195427"
---
# <a name="linker-tools-error-lnk1000"></a>Error de las herramientas del vinculador LNK1000

> error desconocido; Consulte la documentación para obtener información sobre las opciones de soporte técnico

Anote las circunstancias del error e intente aislar el problema y crear un caso de prueba reproducible. Para obtener información sobre cómo investigar y notificar estos errores, vea [Cómo notificar un problema con el C++ conjunto de herramientas visual o la documentación](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)de.

Puede obtener este error si mezcla archivos de encabezado estándar (por ejemplo, Windows. h) y sus propios archivos. Incluya un encabezado precompilado, si lo hubiera, en primer lugar, los encabezados estándar, seguidos de sus propios archivos de encabezado.
