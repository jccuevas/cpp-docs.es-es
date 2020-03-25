---
title: Advertencia de BSCMAKE BK4504
ms.date: 11/04/2016
f1_keywords:
- BK4504
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
ms.openlocfilehash: 57858827439ac8cc11e3718d7a484124ae8a6d74
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197449"
---
# <a name="bscmake-warning-bk4504"></a>Advertencia de BSCMAKE BK4504

el archivo contiene demasiadas referencias. omitiendo otras referencias de este origen

El archivo. cpp contiene más de 64.000 referencias de símbolos. Cuando BSCMAKE ha encontrado 64.000 referencias en un archivo, omite todas las referencias posteriores.

Para corregir el problema, divida el archivo en dos o más archivos, cada uno de los cuales tenga menos de 64.000 referencias de símbolos, o utilice la Directiva de preprocesador `#pragma component(browser)` para limitar los símbolos que se generan para referencias concretas. Para obtener más información, vea [componente](../../preprocessor/component.md).
