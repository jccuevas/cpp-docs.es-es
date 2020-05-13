---
title: Error de las herramientas del vinculador LNK2008
ms.date: 11/04/2016
f1_keywords:
- LNK2008
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
ms.openlocfilehash: c7794d09f7eeb9dceba7098ca7af90ccf2eeccad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194829"
---
# <a name="linker-tools-error-lnk2008"></a>Error de las herramientas del vinculador LNK2008

El destino de la corrección no está alineado ' symbol_name '

El vínculo encontró un destino de corrección en el archivo objeto que no se ha alineado correctamente.

Este error puede deberse a una alineación de subsección personalizada (por ejemplo, #pragma [Pack](../../preprocessor/pack.md)), un modificador [align](../../cpp/align-cpp.md) o un código de lenguaje de ensamblado que modifica la alineación de la sección.

Si el código no usa ninguno de los anteriores, esto puede deberse al compilador.
