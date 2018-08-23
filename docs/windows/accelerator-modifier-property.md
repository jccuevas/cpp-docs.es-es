---
title: Propiedad de acelerador modificador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7e6750bfc0195eaaa350b829d1d899f648e9fe0e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592641"
---
# <a name="accelerator-modifier-property"></a>Modifier (Propiedad de acelerador)

Las entradas siguientes son válidas para la propiedad modificador de la tabla de aceleradores.

|Valor|Descripción|
|-----------|-----------------|
|**Ninguno**|Usuario presiona sólo el **clave** valor. Uso es más eficaz con los valores ASCII/ANSI 001 a 026, que se interpreta como ^ A ^ Z (CTRL-A mediante CTRL-Z).|
|**Alt**|El usuario debe presionar el **Alt** clave antes de la **clave** valor.|
|**Ctrl**|El usuario debe presionar el **Ctrl** clave antes de la **clave** valor. No es válido con el tipo de ASCII.|
|**Mayús**|El usuario debe presionar el **MAYÚS** clave antes de la **clave** valor.|
|**Ctrl + Alt**|El usuario debe presionar el **Ctrl** clave y el **Alt** clave antes de la **clave** valor. No es válido con el tipo de ASCII.|
|**CTRL + MAYÚS**|El usuario debe presionar el **Ctrl** clave y el **MAYÚS** clave antes de la **clave** valor. No es válido con el tipo de ASCII.|
|**ALT + MAYÚS**|El usuario debe presionar el **Alt** clave y el **MAYÚS** clave antes de la **clave** valor. No es válido con el tipo de ASCII.|
|**Ctrl + Alt + Mayús**|El usuario debe presionar **Ctrl**, **Alt**, y **MAYÚS** antes de la **clave** valor. No es válido con el tipo de ASCII.|

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Establecimiento de las propiedades de los aceleradores](../windows/setting-accelerator-properties.md)  
[Editor de aceleradores](../windows/accelerator-editor.md)