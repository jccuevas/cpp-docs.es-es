---
title: Error grave de NMAKE U1064
ms.date: 11/04/2016
f1_keywords:
- U1064
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
ms.openlocfilehash: bfc42c458c1932287f17f367d09c4b23c2c201a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182830"
---
# <a name="nmake-fatal-error-u1064"></a>Error grave de NMAKE U1064

No se encontró el archivo make y no se especificó ningún destino

La línea de comandos NMAKE no especificó un archivo make o un destino y el directorio actual no contenía un archivo denominado MAKEFILE.

NMAKE requiere un archivo make o un destino de línea de comandos (o ambos). Para hacer que un archivo make esté disponible para NMAKE, especifique la opción/F o coloque un archivo denominado MAKEFILE en el directorio actual. NMAKE puede crear un destino de línea de comandos mediante una regla de inferencia si no se proporciona un archivo make.
