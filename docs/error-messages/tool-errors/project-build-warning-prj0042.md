---
title: Advertencia PRJ0042 al compilar del proyecto | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0042
dev_langs:
- C++
helpviewer_keywords:
- PRJ0042
ms.assetid: 682c9999-6f85-409f-b102-00c93243f74f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 260da8ac336c640ea875610b2c62e6c42c7d335e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211355"
---
# <a name="project-build-warning-prj0042"></a>Advertencia PRJ0042 al compilar el proyecto

> La propiedad' Outputs' del paso de compilación personalizada para el archivo de'*archivo*' no se ha establecido. El paso de compilación personalizada se omitirá.

No se ha ejecutado un paso de compilación personalizada porque se especificó ningún resultado.

Para resolver este error, realice una de las siguientes:

- Excluir el paso de compilación personalizada de la compilación.

- Agrega una salida.

- Elimine el contenido del comando del paso de compilación personalizada.