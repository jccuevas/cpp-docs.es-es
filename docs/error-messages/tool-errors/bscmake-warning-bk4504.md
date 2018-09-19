---
title: Advertencia de BSCMAKE BK4504 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK4504
dev_langs:
- C++
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8a2da8903dade37faf3b14175b65f3169efd908
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049778"
---
# <a name="bscmake-warning-bk4504"></a>Advertencia de BSCMAKE BK4504

archivo contiene demasiadas referencias; omitiendo las demás referencias de este origen

El archivo .cpp contiene más de 64.000 referencias de símbolos. Cuando BSCMAKE ha encontrado 64.000 referencias en un archivo, omite todas las referencias adicionales.

Para corregir el problema, ya sea dividir el archivo en dos o más archivos, cada uno de los cuales tiene menos de 64 000 referencias de símbolos, o utilice el `#pragma component(browser)` directiva de preprocesador para símbolos de límite que se generan para las referencias determinadas. Para obtener más información, consulte [componente](../../preprocessor/component.md).