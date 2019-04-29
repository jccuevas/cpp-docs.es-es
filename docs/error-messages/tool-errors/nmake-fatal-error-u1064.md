---
title: Error grave de NMAKE U1064
ms.date: 11/04/2016
f1_keywords:
- U1064
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
ms.openlocfilehash: 71213391032989e5faf8889761b29194928125a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367413"
---
# <a name="nmake-fatal-error-u1064"></a>Error grave de NMAKE U1064

Archivo MAKE no se encuentra y se especificó ningún destino

La línea de comandos NMAKE no especificó un archivo MAKE o un destino y el directorio actual no contiene un archivo denominado archivo MAKE.

NMAKE requiere un archivo MAKE o un destino de línea de comandos (o ambos). Para que esté disponible un archivo MAKE NMAKE, especifique la opción /F o coloque un archivo denominado MAKE en el directorio actual. NMAKE puede crear un destino de línea de comandos mediante una regla de inferencia si no se proporciona un archivo MAKE.