---
title: Advertencia de BSCMAKE BK4504
ms.date: 11/04/2016
f1_keywords:
- BK4504
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
ms.openlocfilehash: 7ffcb7c2e6ae512006ccd29c87b05c53fdfcaef5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279310"
---
# <a name="bscmake-warning-bk4504"></a>Advertencia de BSCMAKE BK4504

archivo contiene demasiadas referencias; omitiendo las demás referencias de este origen

El archivo .cpp contiene más de 64.000 referencias de símbolos. Cuando BSCMAKE ha encontrado 64.000 referencias en un archivo, omite todas las referencias adicionales.

Para corregir el problema, ya sea dividir el archivo en dos o más archivos, cada uno de los cuales tiene menos de 64 000 referencias de símbolos, o utilice el `#pragma component(browser)` directiva de preprocesador para símbolos de límite que se generan para las referencias determinadas. Para obtener más información, consulte [componente](../../preprocessor/component.md).