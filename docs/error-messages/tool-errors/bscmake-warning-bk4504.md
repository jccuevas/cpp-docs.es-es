---
title: Advertencia de BSCMAKE BK4504 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- BK4504
dev_langs:
- C++
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 58a59b3141a8d7051aa7ece1bcb71dd960fabb18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-warning-bk4504"></a>Advertencia de BSCMAKE BK4504
archivo contiene demasiadas referencias; se omitirá las demás referencias de este origen  
  
 El archivo .cpp que contiene más de 64.000 referencias de símbolos. Cuando BSCMAKE ha encontrado 64.000 referencias en un archivo, pasa por alto todas las referencias adicionales.  
  
 Para corregir el problema, divida el archivo en dos o más archivos, cada uno de los cuales tiene menos de 64.000 referencias de símbolos o usar el `#pragma component(browser)` directiva de preprocesador para símbolos de límite que se generan para las referencias determinadas. Para obtener más información, consulte [componente](../../preprocessor/component.md).