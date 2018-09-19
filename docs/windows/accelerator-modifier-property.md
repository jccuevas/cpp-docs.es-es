---
title: Propiedad modificador de acelerador (C++) | Microsoft Docs
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
ms.openlocfilehash: 793e02b4ac083d6fe84ba2cc76ee340bcf2484e9
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316060"
---
# <a name="accelerator-modifier-property-c"></a>Propiedad modificador de acelerador (C++)

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