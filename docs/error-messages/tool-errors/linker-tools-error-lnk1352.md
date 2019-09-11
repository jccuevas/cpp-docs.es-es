---
title: Error de las herramientas del vinculador LNK1352
description: El error LNK1352 de las herramientas del vinculador se produce cuando se intenta realizar una combinación de sección no compatible.
ms.date: 09/10/2019
f1_keywords:
- LNK1352
helpviewer_keywords:
- LNK1352
ms.openlocfilehash: 38f773bfd669529dfb1ada9c7bb59e6f0962c9c7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908397"
---
# <a name="linker-tools-error-lnk1352"></a>Error de las herramientas del vinculador LNK1352

> '*section_name_1*' y '*section_name_2*' no se pueden combinar en secciones diferentes

## <a name="remarks"></a>Comentarios

El vinculador detectó una combinación de sección no permitida, ya que *section_name_1* y *section_name_2* deben combinarse en la misma sección. Por ejemplo, este error se produce si el vinculador detecta un intento de combinar la `.stls` sección y la `.tls` sección en secciones diferentes.

### <a name="to-correct-this-error"></a>Para corregir este error

Compruebe la opción [/Merge](../../build/reference/merge-combine-sections.md) en la línea de comandos del vinculador para este problema.

## <a name="see-also"></a>Vea también

[Errores y advertencias de las herramientas del vinculador](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
