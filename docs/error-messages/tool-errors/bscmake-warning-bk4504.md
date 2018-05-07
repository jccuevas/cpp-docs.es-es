---
title: Advertencia de BSCMAKE BK4504 | Documentos de Microsoft
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
ms.openlocfilehash: 5a17aa8b4e2a98d3bda5d21ea84962791b8051dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="bscmake-warning-bk4504"></a>Advertencia de BSCMAKE BK4504
archivo contiene demasiadas referencias; se omitirá las demás referencias de este origen  
  
 El archivo .cpp que contiene más de 64.000 referencias de símbolos. Cuando BSCMAKE ha encontrado 64.000 referencias en un archivo, pasa por alto todas las referencias adicionales.  
  
 Para corregir el problema, divida el archivo en dos o más archivos, cada uno de los cuales tiene menos de 64.000 referencias de símbolos o usar el `#pragma component(browser)` directiva de preprocesador para símbolos de límite que se generan para las referencias determinadas. Para obtener más información, consulte [componente](../../preprocessor/component.md).